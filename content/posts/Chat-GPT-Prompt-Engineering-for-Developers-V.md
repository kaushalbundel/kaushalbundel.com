+++
title = "Understanding ChatGpt Prompt Engineering- Part V - Using ChatGPT for Transforming text"
author = ["Kaushal Bundel"]
date = 2024-03-26
lastmod = 2024-03-26
tags = ["LLM","chatGPT"]
categories = ["Beginner"]
draft = false
+++


# Basic Usage of LLM's


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

## LLM as a Transforming device

Consider the below text in Sanskrit. We can translate this text in the language for our choice with the tonal quality that we aspire.


```python
text = f"""
योगस्थः कुरु कर्माणि सङ्गं त्यक्त्वा धनञ्जय।

सिद्ध्यसिद्ध्योः समो भूत्वा समत्वं योग उच्यते।।
"""
```


```python
prompt = f"""
Please translate the sanskrit text {text} in the hindi and english language. Use the following rules to make the translation:

1. Output the original text and the both translations in the form of python list

2. The tone of the translation should be warn, friendly and personal. 

"""

response = get_completion(prompt)
print(response)
```

    ```python
    original_text = ["योगस्थः कुरु कर्माणि सङ्गं त्यक्त्वा धनञ्जय।", "सिद्ध्यसिद्ध्योः समो भूत्वा समत्वं योग उच्यते।।"]
    
    hindi_translation = ["योगस्थः कर्म करो, संग से दूर होकर धनंजय।", "सिद्धि और असिद्धि में समान बनकर समता को योग कहा जाता है।"]
    
    english_translation = ["Stay focused on your actions while letting go of attachment, Arjuna.", "Being equal in success and failure is called yoga."]
    
    translations = [original_text, hindi_translation, english_translation]
    print(translations)
    ```



```python
original_text = ["योगस्थः कुरु कर्माणि सङ्गं त्यक्त्वा धनञ्जय।", "सिद्ध्यसिद्ध्योः समो भूत्वा समत्वं योग उच्यते।।"]

hindi_translation = ["योगस्थः कर्म करो, संग से दूर होकर धनंजय।", "सिद्धि और असिद्धि में समान बनकर समता को योग कहा जाता है।"]

english_translation = ["Stay focused on your actions while letting go of attachment, Arjuna.", "Being equal in success and failure is called yoga."]

translations = [original_text, hindi_translation, english_translation]
print(translations)
```

    [['योगस्थः कुरु कर्माणि सङ्गं त्यक्त्वा धनञ्जय।', 'सिद्ध्यसिद्ध्योः समो भूत्वा समत्वं योग उच्यते।।'], ['योगस्थः कर्म करो, संग से दूर होकर धनंजय।', 'सिद्धि और असिद्धि में समान बनकर समता को योग कहा जाता है।'], ['Stay focused on your actions while letting go of attachment, Arjuna.', 'Being equal in success and failure is called yoga.']]


Expanding the given translation into a socratic conversation.


```python
prompt_extension = f"""
Please expand the text mentioned below in the python list in the format of socratic conversation between Krishna and Arjuna, the central characters of the epic mahabharata. Follow the below rules for the conversation.

- text: {english_translation}
- The length of the conversation should be 5 lines maximum per character
- The tone of the discussion should be personal and friendly
"""
response_new = get_completion(prompt_extension)
print(response_new)
```

    Krishna: Stay focused on your actions while letting go of attachment, Arjuna.
    Arjuna: But how can I not be attached to the outcome of my actions, Krishna?
    Krishna: Being equal in success and failure is called yoga, Arjuna.
    Arjuna: So, I should strive for excellence without being attached to the results?
    Krishna: Yes, Arjuna. Focus on the present moment and do your best without worrying about the outcome.


Lets try to change this conversation in Hindi


```python
prompt_extension = f"""
Please expand the text mentioned below in the python list in the format of socratic conversation between Krishna and Arjuna, the central characters of the epic mahabharata. Follow the below rules for the conversation.

- text: {hindi_translation}
- The length of the conversation should be 10 lines maximum per character
- The tone of the discussion should be personal and friendly
"""
response_new = get_completion(prompt_extension)
print(response_new)
```

    Krishna: Arjuna, योगस्थः कर्म करो, संग से दूर होकर धनंजय।
    Arjuna: क्या योगस्थ कर्म करने से मुझे कैसे फायदा होगा, कृष्णा?
    Krishna: सिद्धि और असिद्धि में समान बनकर समता को योग कहा जाता है।
    Arjuna: क्या यह मतलब है कि मैं सफलता और असफलता को समान दृष्टि से देखूं?
    Krishna: हाँ, अर्जुन। समता का यही अर्थ है।
    Arjuna: लेकिन क्या यह मेरे कर्मों को प्रभावित नहीं करेगा?
    Krishna: नहीं, अर्जुन। योगस्थ कर्म करने से तू अपने कर्मों का फल नहीं चाहेगा।
    Arjuna: धन्यवाद, कृष्णा। मैं योगस्थ कर्म करने का प्रयास करूंगा।
    Krishna: बहुत अच्छा, अर्जुन। योग का अर्थ समता है, जो तुझे शांति और सफलता की दिशा में ले जाएगा।


The translation and subsequent generation is not that great, let see if we can be more creative in next iterations. For that we will make some modification in the starter function.


```python
# changing the temperature so that the model can give be more random and thereby more creative

def get_completion_creative(prompt, model = "gpt-3.5-turbo"):
    messages = [{"role": "user", "content":prompt}]
    response =  client.chat.completions.create(
        model = model,
        messages = messages,
        temperature = 1
    )
    return response.choices[0].message.content
```


```python
prompt_extension = f"""
Please expand the text mentioned below in the python list in the format of socratic conversation between Krishna and Arjuna, the central characters of the epic mahabharata. Follow the below rules for the conversation.

- text: {hindi_translation}
- The length of the conversation should be 10 lines maximum per character
- The tone of the discussion should be personal and friendly
"""
response_new = get_completion_creative(prompt_extension)
print(response_new)
```

    Krishna: Arjuna, why do you hesitate to perform your duties with a focused mind?
    Arjuna: Krishna, I fear attachment to the results of my actions.
    Krishna: Detach yourself from the outcomes, focus on the present moment.
    Arjuna: But how can I remain unaffected by success or failure?
    Krishna: Achieving balance in success and failure is true yoga, Arjuna.
    Arjuna: So, being equanimous in all situations is the essence of yoga?
    Krishna: Yes, Arjuna, that is the path to inner peace and self-realization.
    Arjuna: Thank you, Krishna, for guiding me on the path of righteousness.
    Krishna: Remember, Arjuna, true fulfillment comes from detached action in the spirit of yoga.


The above text works but the language in not Hindi. Adding this condition to the prompt.


```python
prompt_extension = f"""
Please expand the text mentioned below in the python list in the format of socratic conversation between Krishna and Arjuna, the central characters of the epic mahabharata. Follow the below rules for the conversation.

- text: {hindi_translation}
- The length of the conversation should be 10 lines maximum per character
- The tone of the discussion should be personal and friendly
- The output text should be in hindi
"""
response_new = get_completion_creative(prompt_extension)
print(response_new)
```

    कृष्ण: अर्जुन, योगस्थः कर्म करना क्या अर्थ है?  
    अर्जुन: हाँ कृष्ण, यह अपने कर्मों में संलग्न रहकर संग से दूर रहना है।  
    कृष्ण: सही कहा अर्जुन, संग से दूर रहकर हमें धनंजय के रूप में सिद्धि प्राप्त होती है।  
    अर्जुन: कृष्ण, क्या समता को योग कहा जाता है?  
    कृष्ण: हाँ अर्जुन, समता में सिद्धि और असिद्धि को समान दृष्टिकोण से देखना होता है।  
    अर्जुन: योग का अर्थ समझ में आया, धन्यवाद कृष्ण।  
    कृष्ण: तुम्हारा समझना मेरे लिए आनंद का विषय है, अर्जुन।  
    अर्जुन: कृष्ण, आपके साथ हर समय यह विचार करना मुझे आनंद देता है।  
    कृष्ण: हमारा साथ और भी मजबूत बनाएगा, अर्जुन, जय श्री कृष्ण।


As can be seen that this translation is useless as last 4 conversation points are just Arjuna and Krishna complimenting each other. Let's change the model and see if that improves the results.


```python
# changing the temperature so that the model can give be more random and thereby more creative

def get_completion_gpt4(prompt, model = "gpt-4-turbo-preview"):
    messages = [{"role": "user", "content":prompt}]
    response =  client.chat.completions.create(
        model = model,
        messages = messages,
        temperature = 1
    )
    return response.choices[0].message.content
```


```python
prompt_extension = f"""
Please expand the text mentioned below in the python list in the format of socratic conversation between Krishna and Arjuna, the central characters of the epic mahabharata. Follow the below rules for the conversation.

- text: {hindi_translation}
- The length of the conversation should be 10 lines maximum per character
- The tone of the discussion should be personal and friendly
- The output text should be in hindi
"""
response_new = get_completion_gpt4(prompt_extension)
print(response_new)
```

    अर्जुन: हे कृष्ण, कर्म की महिमा तो मैंने अनेकों बार सुनी है। पर मेरे मन में अभी भी एक संशय है, कि इस कर्म को किस प्रकार किया जाए?
    
    कृष्ण: हे धनंजय, सुनो। कर्म करते वक्त योगस्थ होकर कर्म करो। इसका अर्थ है, अपनी इंद्रियों को नियंत्रित करते हुए, अपने मन को स्थिर रखते हुए कर्म करो।
    
    अर्जुन: पर यह योगस्थ होना कैसे संभव है कृष्ण? कर्म करते समय तो मन अनेक प्रकार की चिंताओं में उलझा रहता है।
    
    कृष्ण: हे पार्थ, संग से दूर होकर कर्म करो। अर्थात, कर्म करते समय फल की चिंता न करो। अपने कर्म को निष्काम भाव से करो, फल की चिंता मुझ पर छोड़ दो।
    
    अर्जुन: तो क्या कर्म के फल की आशा न करना ही योग है?
    
    कृष्ण: जी हाँ, अर्जुन। सिद्धि और असिद्धि में समान बनकर, समता को योग कहा जाता है। कर्म करते समय जब तुम सफलता और असफलता में समान भाव रखते हो, तब तुम योगी होते हो।
    
    अर्जुन: किन्तु हे मधुसूदन, इस समता को प्राप्त करना बहुत कठिन लगता है।
    
    कृष्ण: वही तो योग की साधना है, अर्जुन। आत्मा की शांति और मन की एकाग्रता के माध्यम से, इस समता को प्राप्त किया जा सकता है। यही योग का असली रूप है।
    
    अर्जुन: धन्यवाद, हे कृष्ण। आपके इन शब्दों ने मेरी आंखें खोल दी हैं। मैं अब समझ गया हूँ कि वास्तविक योग क्या है।
    
    कृष्ण: याद रखो अर्जुन, योग कर्मसु कौशलम। यानी, कर्म में कौशल ही योग है। अपने कर्म को पूरे मन से, सभी आसक्तियों से मुक्त होकर करो, तब ही तुम योगी कहलाओगे।


This translation and expansion is just wow!!!
Its the best I have seen a model do. 


