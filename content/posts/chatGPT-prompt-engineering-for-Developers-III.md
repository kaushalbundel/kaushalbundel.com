+++
title = "Understanding ChatGpt Prompt Engineering- Part III - Using ChatGPT for summarization tasks"
author = ["Kaushal Bundel"]
date = 2024-03-24T14:00:13+05:30
lastmod = 2024-03-24T14:00:13+05:30
tags = ["LLM","chatGPT"]
categories = ["Beginner"]
draft = false
+++


# Basic Usage of LLM


```python
#loading the boiler plate code
import openai
import os
from dotenv import load_dotenv, find_dotenv #library to load the local environment variables jupyter
_=load_dotenv(find_dotenv()) 
api_key= os.getenv("OPENAI_API_KEY")

#creating the basic prompting function

client = openai.OpenAI()

def get_completion(prompt, model = "gpt-3.5-turbo"):
    messages = [{"role": "user", "content":prompt}]
    response =  client.chat.completions.create(
        model = model,
        messages = messages,
        temperature = 0
    )
    return response.choices[0].message.content
```

## Using ChatGPT for summarization tasks

This is the most common usecase and I am sure most of the people are using ChatGPT for this activity. But there are subtle tricks that one can use to enhance the experience of summarization.


```python
# ipad review

sample_text = f"""
Product Name: Apple iPad Air

I Grabed it for 40k in the great Indian festival sale. Although it took much efforts to grab the deal due to limited stock. Now Come to the Machine, it's absolutely fantastic. The M1 chip makes it powerhouse. In fact there are not many apps available to use its power.
Rating
Battery 5/5. - I charge once in a day.
Display 4/5. - It's 60hz. It feels slow due to the bigger screen size. Atleast 90hz display is expected at this price point.
Sound 5/5. Clear vocals, balanced sound, base is enough.
Finger print (touch I'd) - it's slow. You have to hold your finger on it. Even in redmi realme phones of 10k range they are 0roviding faster touch I'd than this one.
Camera 4/5. - 12 mp camera is more than sufficient but FLASH is Missing. Flash must be provided it helps scanning the docs in dark.
Storage 4/5. - There must be a 128gb variant in air series.
Charger could have been more powerful.
Connectivity - C type opens option to connect anywhere. Wireless pencil is awesome you don't need to charge separately. Just use and stick it to the edge of your ipad that's all. It charges wirelessly.
Over all a good buy.
For me this is the best machine because I purchased it in just 40k.

"""
```

### Simple summarization


```python
prompt = f"""
As a product review department, please share the summary of the {sample_text} in 40 words.
"""
response = get_completion(prompt)
print(response)
```

    The reviewer purchased the iPad Air in the Great Indian Festival sale for 40k, despite limited stock. The M1 chip makes it a powerhouse, with excellent battery life and sound quality. However, the display could be improved and the fingerprint sensor is slow. Overall, a good buy for the price.


### Summary of a specific property in the text




```python
prompt = f"""
As a product review department, please share the summary of the {sample_text} in 40 words focussed around the product quality.
"""
response = get_completion(prompt)
print(response)
```

    The iPad Air with M1 chip is a powerhouse with excellent battery life and sound quality. However, the display could be improved, and the fingerprint sensor is slow. Overall, a good buy for the price.


The above prompt gives the information from product's POV.

We can also summarize the product information in different buckets and collate them in a JSON format for future consumption.


```python
buckets = f"""
price, product_quality,camera_quality, delivery_speed, product_purchase_time
"""
keys = f"""
productName as parent key, sub keys ```{buckets}``` 
"""
prompt = f"""
As a product review department, please share the summary of the {sample_text} in 40 words per bucket. Use the rules as specific in the text below:
1. Summarize the {sample_text} in the different buckets as described by {buckets}.
2. Store the information in JSON format with the {keys} as mentioned. Please keep parent keys and child keys are separate
3. If relevant data is not available for review then mention the specific key value as "Data not found"
"""
response = get_completion(prompt)
print(response)
```

    {
        "productName": "Apple iPad Air",
        "price": "40k",
        "product_quality": {
            "Battery": "5/5",
            "Display": "4/5",
            "Sound": "5/5",
            "Finger print (touch ID)": "Slow",
            "Camera": "4/5",
            "Storage": "4/5",
            "Charger": "Could have been more powerful",
            "Connectivity": "C type opens option to connect anywhere. Wireless pencil is awesome"
        },
        "camera_quality": {
            "Camera": "12 MP camera is more than sufficient but FLASH is Missing"
        },
        "delivery_speed": "Data not found",
        "product_purchase_time": "Purchased in the great Indian festival sale"
    }


As can be seen the entire data is extracted and summarized in a neat easy to use format.

In somecases we need to show the summarized data on product site. This can also be easily accomplished in the following manner.


```python
buckets = f"""
price, product_quality,camera_quality, delivery_speed, product_purchase_time
"""
paragraph_detail = f"""
Key Points, Data Table, Conclusion
"""
keys = f"""
productName as parent key, sub keys ```{buckets}``` 
"""
prompt = f"""
As a product review department, please share the summary of the {sample_text} in 100 words. Use the rules as specific in the text below:
1. Summarize the entire data in HTML format as per the text mentioned in {paragraph_detail} 
2. In the data table paragraph create a HTML table with the table columns as {buckets} and values as defined in {sample_text} 
4. If relevant data is not available for HTML table then mention the specific value as "Data not found"
"""
response = get_completion(prompt)
print(response)
```

    <!DOCTYPE html>
    <html>
    <head>
      <title>Product Review: Apple iPad Air</title>
    </head>
    <body>
    
    <h2>Key Points:</h2>
    <p>Price: 40k</p>
    <p>Battery Rating: 5/5</p>
    <p>Display Rating: 4/5</p>
    <p>Sound Rating: 5/5</p>
    <p>Fingerprint (Touch ID): Slow</p>
    <p>Camera Rating: 4/5</p>
    <p>Storage Rating: 4/5</p>
    <p>Charger: Could be more powerful</p>
    <p>Connectivity: C type, Wireless pencil</p>
    <p>Overall: Good buy</p>
    
    <h2>Data Table:</h2>
    <table>
      <tr>
        <th>Price</th>
        <th>Product Quality</th>
        <th>Camera Quality</th>
        <th>Delivery Speed</th>
        <th>Product Purchase Time</th>
      </tr>
      <tr>
        <td>40k</td>
        <td>Data not found</td>
        <td>4/5</td>
        <td>Data not found</td>
        <td>Data not found</td>
      </tr>
    </table>
    
    <h2>Conclusion:</h2>
    <p>The Apple iPad Air is a fantastic machine with a powerful M1 chip. While the display could be improved to at least 90hz, the battery life is excellent and the sound quality is top-notch. The fingerprint sensor is slow compared to other devices in the market, and the camera lacks a flash which could be useful for dark environments. Overall, it is a good buy especially at the price of 40k.</p>
    
    </body>
    </html>


Checking the HTML response


```python
from IPython.display import display, HTML
display(HTML(response))
```


<!DOCTYPE html>
<html>
<head>
  <title>Product Review: Apple iPad Air</title>
</head>
<body>

<h2>Key Points:</h2>
<p>Price: 40k</p>
<p>Battery Rating: 5/5</p>
<p>Display Rating: 4/5</p>
<p>Sound Rating: 5/5</p>
<p>Fingerprint (Touch ID): Slow</p>
<p>Camera Rating: 4/5</p>
<p>Storage Rating: 4/5</p>
<p>Charger: Could be more powerful</p>
<p>Connectivity: C type, Wireless pencil</p>
<p>Overall: Good buy</p>

<h2>Data Table:</h2>
<table>
  <tr>
    <th>Price</th>
    <th>Product Quality</th>
    <th>Camera Quality</th>
    <th>Delivery Speed</th>
    <th>Product Purchase Time</th>
  </tr>
  <tr>
    <td>40k</td>
    <td>Data not found</td>
    <td>4/5</td>
    <td>Data not found</td>
    <td>Data not found</td>
  </tr>
</table>

<h2>Conclusion:</h2>
<p>The Apple iPad Air is a fantastic machine with a powerful M1 chip. While the display could be improved to at least 90hz, the battery life is excellent and the sound quality is top-notch. The fingerprint sensor is slow compared to other devices in the market, and the camera lacks a flash which could be useful for dark environments. Overall, it is a good buy especially at the price of 40k.</p>

</body>
</html>


While the above example works from the HTML generation point of view, but here the model has hallucinated. The "Product Purchase Time" that was clearly mentioned as "Purchased in the great Indian festival sale" in the previous example is now treated as "Data not Found". Lets see if we can remove this halluncination.


```python
buckets = f"""
price, product_quality,camera_quality, delivery_speed, product_purchase_time
"""
paragraph_headings = f"""
Key Points, Data Table, Conclusion
"""
keys = f"""
productName as parent key, sub keys ```{buckets}``` 
"""
prompt = f"""
As a product review department, please share the summary of the {sample_text} in 100 words. Use the rules as specific in the text below:
1. Summarize the entire data in HTML format as per the headings mentioned in {paragraph_headings} 
2. Key Points heading should contain a summary text of the {sample_text}
3. In the data table paragraph create a HTML table with the table columns as {buckets} and values as defined in {sample_text} 
3.1. If relevant data is not available for HTML table then mention the specific value as "Data not found"
4. It is important that we get the values in the HTML table absolutely correct. So double check each response before sharing.
"""
response = get_completion(prompt)
print(response)
```

    
    Key Points:
    Product Name: Apple iPad Air
    Summary: Purchased for 40k in a sale, fantastic machine with M1 chip, good battery and sound quality, slow fingerprint sensor, missing flash in camera, limited storage options, could have a more powerful charger, good connectivity options with wireless pencil.
    
    Data Table:
    | Price | Product Quality | Camera Quality | Delivery Speed | Product Purchase Time |
    |-------|-----------------|----------------|----------------|----------------------|
    | 40k   | 4/5             | 4/5            | Data not found | Data not found        |
    
    Conclusion:
    The Apple iPad Air is a great purchase at 40k with its powerful M1 chip, good battery life, and sound quality. However, there are some areas for improvement such as the slow fingerprint sensor and lack of flash in the camera. Overall, it offers good value for money with its connectivity options and wireless pencil feature.



```python
display(HTML(response))
```


Key Points:
The Apple iPad Air was purchased for 40k during the Great Indian Festival sale. The M1 chip makes it a powerhouse, although there are limited apps to fully utilize its power. The battery life is excellent, requiring only one charge per day. The display is rated 4/5 due to the 60hz refresh rate, and the sound quality is praised for clear vocals and balanced sound. The fingerprint sensor is noted to be slow, and the camera quality is rated 4/5 with a missing flash. Storage options and charger power could be improved, but connectivity options are praised, including the wireless pencil feature.

Data Table:
| Price | Product Quality | Camera Quality | Delivery Speed | Product Purchase Time |
|-------|-----------------|----------------|----------------|-----------------------|
| 40k   | Data not found  | 4/5            | Data not found | Data not found        |

Conclusion:
Overall, the Apple iPad Air is considered a good buy for the price of 40k. The device offers powerful performance with the M1 chip, excellent battery life, and clear sound quality. However, improvements could be made in the display refresh rate, fingerprint sensor speed, camera flash availability, storage options, and charger power. The connectivity options, including the wireless pencil feature, are highlighted as convenient and innovative.


After making necessary changes, the model is still hallucinating. let me change the model and see if a high performance model gives different results.


```python
#loading GPT 4 model

def get_completion_gpt4(prompt, model = "gpt-4-turbo-preview"):
    messages = [{"role": "user", "content":prompt}]
    response =  client.chat.completions.create(
        model = model,
        messages = messages,
        temperature = 0
    )
    return response.choices[0].message.content
```


```python
buckets = f"""
price, product_quality,camera_quality, delivery_speed, product_purchase_time
"""
paragraph_headings = f"""
Key Points, Data Table, Conclusion
"""
keys = f"""
productName as parent key, sub keys ```{buckets}``` 
"""
prompt = f"""
As a product review department, please share the summary of the {sample_text} in 100 words. Use the rules as specific in the text below:
1. Summarize the entire data in HTML format as per the headings mentioned in {paragraph_headings} 
2. Key Points heading should contain a summary text of the {sample_text}
3. In the data table paragraph create a HTML table with the table columns as {buckets} and values as defined in {sample_text} 
3.1. If relevant data is not available for HTML table then mention the specific value as "Data not found"
4. It is important that we get the values in the HTML table absolutely correct. So double check each response before sharing.
"""
response = get_completion_gpt4(prompt)
print(response)
```

    ```html
    <!DOCTYPE html>
    <html>
    <head>
    <title>Apple iPad Air Review Summary</title>
    </head>
    <body>
    
    <h2>Key Points</h2>
    <p>The Apple iPad Air, purchased during the Great Indian Festival sale for 40k, is described as a fantastic machine powered by the M1 chip, though it's noted there aren't many apps that fully utilize its power. The device boasts a solid battery life, requiring only daily charging, but its 60hz display is seen as a drawback, with a preference for at least a 90hz display at this price point. Sound quality is praised, while the fingerprint sensor is criticized for its slowness. The camera is adequate but lacks a flash, and storage options could be improved. Connectivity features and the wireless pencil are highlighted as positives, making it overall a good purchase, especially at the sale price.</p>
    
    <h2>Data Table</h2>
    <table border="1">
    <tr>
    <th>price</th>
    <th>product_quality</th>
    <th>camera_quality</th>
    <th>delivery_speed</th>
    <th>product_purchase_time</th>
    </tr>
    <tr>
    <td>40k</td>
    <td>High</td>
    <td>Good</td>
    <td>Data not found</td>
    <td>Great Indian Festival sale</td>
    </tr>
    </table>
    
    <h2>Conclusion</h2>
    <p>Overall, the Apple iPad Air is considered a valuable purchase, especially for the price of 40k during a sale. It excels in performance thanks to the M1 chip, offers great sound and battery life, though it falls short in display refresh rate and fingerprint sensor speed. The lack of a flash for the camera and limited storage options are minor drawbacks. The inclusion of a C-type connector and a wireless pencil enhances its usability, making it a recommended choice for those looking for a powerful tablet.</p>
    
    </body>
    </html>
    ```



```python
display(HTML(response))
```


```html
<!DOCTYPE html>
<html>
<head>
<title>Apple iPad Air Review Summary</title>
</head>
<body>

<h2>Key Points</h2>
<p>The Apple iPad Air, purchased during the Great Indian Festival sale for 40k, is described as a fantastic machine powered by the M1 chip, though it's noted there aren't many apps that fully utilize its power. The device boasts a solid battery life, requiring only daily charging, but its 60hz display is seen as a drawback, with a preference for at least a 90hz display at this price point. Sound quality is praised, while the fingerprint sensor is criticized for its slowness. The camera is adequate but lacks a flash, and storage options could be improved. Connectivity features and the wireless pencil are highlighted as positives, making it overall a good purchase, especially at the sale price.</p>

<h2>Data Table</h2>
<table border="1">
<tr>
<th>price</th>
<th>product_quality</th>
<th>camera_quality</th>
<th>delivery_speed</th>
<th>product_purchase_time</th>
</tr>
<tr>
<td>40k</td>
<td>High</td>
<td>Good</td>
<td>Data not found</td>
<td>Great Indian Festival sale</td>
</tr>
</table>

<h2>Conclusion</h2>
<p>Overall, the Apple iPad Air is considered a valuable purchase, especially for the price of 40k during a sale. It excels in performance thanks to the M1 chip, offers great sound and battery life, though it falls short in display refresh rate and fingerprint sensor speed. The lack of a flash for the camera and limited storage options are minor drawbacks. The inclusion of a C-type connector and a wireless pencil enhances its usability, making it a recommended choice for those looking for a powerful tablet.</p>

</body>
</html>
```


As expected, the newer, updated and more expensive model perfoms amazing on this task.


```python

```
