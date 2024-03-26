+++
title = "Understanding ChatGpt Prompt Engineering- Part IV - Using ChatGPT for Inference tasks"
author = ["Kaushal Bundel"]
date = 2024-03-26T04:00:13+05:30
lastmod = 2024-03-26T04:00:13+05:30
tags = ["LLM","chatGPT"]
categories = ["Beginner"]
draft = false
+++



# Basic Usage of LLM's

### Loading the boiler plate code

```python
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

## LLM as a Inference Device

Inference is essentially extraction of specific property of the text fed. These could be sentiments, specific key-value pairs, tone, labels, names etc.  
The application of this function can be very wide, I hope to illustrate a few examples here.

## Sentiment Analysis

In this case, I have a small car review. The objective is to find the sentiment. The possible options could be "neutral, negative and positive".


```python
#starting with a simple example

car_review = f'''
The attractive and urban adapted Skoda Slavia is a sedan for your city lifestyle. 
The car graceful and streamlined body shape projects a dynamic and fashion forward image, and its easy to use interiors provide pleasant and practical conditions for passengers. 
A Slavia equipped with the latest technology features, like the touch screen infotainment system, smartphone connectivity, and driver assist technologies stands out and offers an appealing alternative. Slot by the bonnet of the Slavia black gives a list of effective engine options, some of which have the gasoline engines for precise & economic performance.
'''
```


```python
prompt = f'''
Please share the sentiments of the car review as specified in the text {car_review} as per the following conditions mentioned below:

1. Display possible alternatives either one the following, "neutral, negative or positive"

2. Please output the results in the form of a Json with keys car_review: review_Number and sentiment: <"neutral, negative or positive">
'''

response = get_completion(prompt)
print(response)
```

    {
      "car_review": "review_1",
      "sentiment": "positive"
    }


The expected result is correct.

We can also extract the emotions associated with the above product review.


```python
prompt = f'''
Please share the sentiment and the list of emotions of the car review as specified in the text {car_review} as per the following conditions mentioned below:

1. Display possible alternatives either one the following, "neutral, negative or positive"

2. Please output the results in the form of a Json with keys car_review: review_Number and sentiment: <"neutral, negative or positive">, emotions: <list of emotions>
'''

response = get_completion(prompt)
print(response)
```

    {
      "car_review": "review_1",
      "sentiment": "positive",
      "emotions": ["attractive", "urban", "graceful", "dynamic", "fashion forward", "pleasant", "practical", "appealing", "effective", "precise", "economic"]
    }


Let's try and see if the model is able to extract the review car brand and review car name from the given text.



```python
prompt = f'''
Please share the car brand name and the car model name of the car review as specified in the text {car_review} as per the following conditions mentioned below:


1. Please output the results in the form of a Json with the following keys, brand: <Name of the car brand> and model: <Name of the car Model>. Please display "uknown" if you are not able to discern the values.
'''

response = get_completion(prompt)
print(response)
```

    {
      "brand": "Skoda",
      "model": "Slavia"
    }


## Narrowing the scope of the Text

In this example we will try to narrow down the scope of the text. We will try to capture the essense of the text in some simple keywords. The practicle application could be to extract tags from the text so that only relevent tags pertaining to the document can be shown.


```python
prompt = f'''
Please share the list of key topics as specified in the text {car_review} as per the following conditions mentioned below:

1. Restrict the key topics to one or max two words only.

2. Output the result in python list
'''

response = get_completion(prompt)
print(response)
```

    ['Skoda Slavia', 'sedan', 'urban', 'lifestyle', 'graceful', 'streamlined', 'dynamic', 'fashion', 'interiors', 'technology', 'infotainment', 'connectivity', 'driver assist', 'engine options', 'gasoline', 'performance']


Lets approach the problem in reverse direction. Given a list of tags can we assertain which of the tags is being covered in the text.


```python
tags = ['Skoda Slavia', 'sedan', 'urban', 'lifestyle', 'graceful', 'New Delhi', 'Olympics','Mercedes','elegance']
```


```python
prompt = f'''
Please check if  the list of tags as specified in the python list {tags} is getting covered in the review text {car_review} as per the following conditions mentioned below:

1. Output the result in a JSON object with the keys the list values {tags}. The values could be either 0 or 1 depending on if the tags are present in the review text.

'''

response = get_completion(prompt)
print(response)
```

    {
      "Skoda Slavia": 1,
      "sedan": 1,
      "urban": 1,
      "lifestyle": 1,
      "graceful": 1,
      "New Delhi": 0,
      "Olympics": 0,
      "Mercedes": 0,
      "elegance": 0
    }


The list of values is absolutely correct. It even eliminates the "elegance" tag which is very close to the review in question.

## Using the model with the Native Language

In Northern part of India we write in english alphabets with hindi words. Let's see if the model is able to output the results for this use case. For the example, I have chosen a fictitious review of iphone in hindi. 


```python
mixed_language_text = f"""
Ekdum Kharab product hai iphone 15. Apple waale ne kya ganda product banaya hai. Calls nahi aate. Kaafi mehanga bhi hai. Kidney bech di thi lete time ab ek kidney and iphone ka kya karu?
"""
```


```python
prompt = f'''
Please share the sentiments of the mobile review as specified in the text {mixed_language_text} as per the following conditions mentioned below:

1. Display possible alternatives either one the following, "neutral, negative or positive"

2. Please output the results in the form of a Json with keys product_review: product name and sentiment: <"neutral, negative or positive">
'''

response = get_completion(prompt)
print(response)
```

    {
      "product_review": "iphone 15",
      "sentiment": "negative"
    }


This sound about right.


```python
prompt = f'''
Please share the sentiments and the list of emotions of the mobile review as specified in the text {mixed_language_text} as per the following conditions mentioned below:

1. Display possible alternatives either one the following, "neutral, negative or positive"

2. Please output the results in the form of a Json with keys product_review: product name and sentiment: <"neutral, negative or positive">, emotions: <list of emotions>
'''

response = get_completion(prompt)
print(response)
```

    {
      "product_review": "iphone 15",
      "sentiment": "negative",
      "emotions": ["frustration", "disappointment", "anger"]
    }


The extracted emotions are on point. The key to note here is that the model has converted the emotions expressed in Hindi to enlish words that are not far from the actual interpretation. 

I added a bit of sarcasm also in the text but the model was not able to discern that. 

We can extend this activity further by asking the model to tell us if we need the customer representative to make the call to the user to correct the user grivences.


```python
prompt = f'''
Please share the sentiments, the list of emotions and the action of whether to call the customer or not on the basis of the mobile review as specified in the text {mixed_language_text} as per the following conditions mentioned below:

1. Display possible alternatives either one the following, "neutral, negative or positive"


2. Please output the results in the form of a Json with keys product_review: product name and sentiment: <"neutral, negative or positive">, emotions: <list of emotions> and action: <1 or 0>

3. The "action key" can have binary values 1 or 0

4. The condition of populating "action key" is that the customer should be frustated or disappointed in the product.
'''

response = get_completion(prompt)

print(response)
```

    {
      "product_review": "iphone 15",
      "sentiment": "negative",
      "emotions": ["frustration", "disappointment"],
      "action": 1
    }


Testing this same prompt on the Skoda Slavia review.

## Converting Inference into Action
```python
prompt = f'''
Please share the sentiments, the list of emotions and the action of whether to call the customer or not on the basis of the mobile review as specified in the text {car_review} as per the following conditions mentioned below:

1. Display possible alternatives either one the following, "neutral, negative or positive"


2. Please output the results in the form of a Json with keys product_review: product name and sentiment: <"neutral, negative or positive">, emotions: <list of emotions> and action: <1 or 0>

3. The "action key" can have binary values 1 or 0

4. The condition of populating "action key" is that the customer should be frustated or disappointed in the product.
'''

response = get_completion(prompt)

print(response)
```

    {
      "product_review": "Skoda Slavia",
      "sentiment": "positive",
      "emotions": ["excitement", "satisfaction"],
      "action": 0
    }

