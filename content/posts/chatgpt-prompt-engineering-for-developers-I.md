+++
title = "Understanding ChatGpt Prompt Engineering- Part I"
author = ["Kaushal Bundel"]
date = 2024-03-20T14:38:13+05:30
lastmod = 2024-03-20T14:38:13+05:30
tags = ["LLM","chatGPT"]
categories = ["Beginner"]
draft = false
+++

# Understanding Prompt Engineering

We live in a knowledge economy where paramount importance must be placed on information retrieval and absorption. My journey with ChatGPT began when I started experimenting with the model and discovered use cases that were helpful to me. However, working with a general-purpose model presented its own challenges. As I continued practicing, I became acquainted with specific use cases of ChatGPT, such as efficiently performing standard NLP tasks and generating text summaries, which significantly simplified and enhanced my work. For this purpose, I leveraged third-party tools. Nonetheless, there were times when I struggled to achieve the desired result.

To gain a deeper understanding of prompting and its specialized applications, I enrolled in the [deeplearning.ai](https://learn.deeplearning.ai/) short course on [prompt engineering](https://learn.deeplearning.ai/courses/chatgpt-prompt-eng/lesson/1/introduction). My overarching goal is to learn and then apply the materials in a project.

## Preparation

The first bit involved getting the API token for chatgpt and setting up local variables so that these can be accessed from the choice of text editor with entering them everytime they were needed.
The following openAI [quickstart guide](https://platform.openai.com/docs/quickstart?context=python) was helpful in setting up the system.

```python
import openai
import os
from dotenv import load_dotenv, find_dotenv #library to load the local environment variables jupyter
_=load_dotenv(find_dotenv()) 
```


```python
api_key= os.getenv("OPENAI_API_KEY")
```


```python
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


```python
# testing the api

capital = get_completion("what is the capital of India?")
print(capital)
```

    The capital of India is New Delhi.


## Principles of Prompting

1. Principle 1: Write clear and specific instructions
2. Principle 2: Give the model time to think

### Principle 1: Write clear and specific instructions

#### 1.1 Clarity is not equal to short prompts

The prompt provided to the model must be clear stated with expectations, assumptions and nature of results clearly defined.

##### 1.1.1 Use delimiters like """, ```, ---, <> or "<tag></tag>" in the prompts

Example: Text Summerization

```python
text = f"""
Marina was extremely afraid of the dark. When the lights went out, everything and every shadow appeared to her as the most terrible of monsters. Her parents explained to her, everyday and with great patience, that these things were not monsters. Marina understood her parents, but she could not stop feeling an awful fear whenever it was dark.

One day her Aunt Valerie came to visit. Valerie was an incredible woman. She was famous for her courage, and for having gone on many journeys of adventure, some of which had been made into books and movies. Marina wanted to conquer her fear of the dark, so she asked her Aunt how she became so brave, and whether she had ever been frightened.

"A great many times, Marina," answered her Aunt, "I remember when I was small and I was terribly afraid of the dark. I couldn't stay in the dark for even a moment".

Marina became very excited. How was it possible that someone so courageous could have been afraid of the dark?

"I'll tell you a secret, Marina. It was some blind children who taught me how to be brave. They can't see, so if they had never discovered the secret of how not to be afraid of the dark, they would have been forever frightened".
"It's true!" said Marina, intrigued, "Can you tell me that secret?"
"Of course! The secret is to change your eyes. Since blind children can't see, their hands are their eyes. All you have to do to conquer your fear is what they do. Shut the eyes of your face and open the eyes of your hands. Let's make a deal: tonight, when you go to bed and put out the light, if anything makes you afraid, close your eyes, carefully get out of bed, and try to see what it is that's making you scared. But do it using your hands as eyes... and tomorrow tell me how you're getting on with the fear".

Marina accepted, but she was rather worried. She knew she would need to be brave to close her eyes and go and touch whatever it was that was frightening her; but she was willing to try because she was already too old for this. When her parents took her to bed, she herself put out the light. After a little while, she felt afraid of one of the shadows in the bedroom. Following the advice of Aunt Valerie, she closed the eyes of her face and opened the eyes of her hands. And, summoning up all her courage, she went over to touch that mysterious shadow...

The next morning Marina came running into the kitchen, a big smile on her face, and a song on her lips. "The monster is so soft and smooth!..." she cried,
"It's my teddy bear!

"""

prompt = f""" Give the response in the following form:

1. Summary: Summerize the ```{text}```

2. Moral of the story: Give the moral of the ```{text}```
"""
```

Notice that the text to be used and the prompt are defined separately. This is done because we are not populating general information but a highly specific one that is pertaining to the text given.


```python
response = get_completion(prompt)
print(response)
```

    1. Summary: Marina was extremely afraid of the dark and saw shadows as monsters. Her Aunt Valerie, a courageous woman, taught her to conquer her fear by using her hands as eyes to touch what scared her. Marina found out the monster was her teddy bear.
    
    2. Moral of the story: Conquer your fears by facing them head-on and looking at them from a different perspective. Sometimes what we fear the most turns out to be harmless once we confront it.


In the above example, I have made sure that the response in defined in a specific format that is needed. Along with this reponse text based response I can also tweak the response output as per the need.
For eg.


```python
text = f"""
Marina was extremely afraid of the dark. When the lights went out, everything and every shadow appeared to her as the most terrible of monsters. Her parents explained to her, everyday and with great patience, that these things were not monsters. Marina understood her parents, but she could not stop feeling an awful fear whenever it was dark.

One day her Aunt Valerie came to visit. Valerie was an incredible woman. She was famous for her courage, and for having gone on many journeys of adventure, some of which had been made into books and movies. Marina wanted to conquer her fear of the dark, so she asked her Aunt how she became so brave, and whether she had ever been frightened.

"A great many times, Marina," answered her Aunt, "I remember when I was small and I was terribly afraid of the dark. I couldn't stay in the dark for even a moment".

Marina became very excited. How was it possible that someone so courageous could have been afraid of the dark?

"I'll tell you a secret, Marina. It was some blind children who taught me how to be brave. They can't see, so if they had never discovered the secret of how not to be afraid of the dark, they would have been forever frightened".
"It's true!" said Marina, intrigued, "Can you tell me that secret?"
"Of course! The secret is to change your eyes. Since blind children can't see, their hands are their eyes. All you have to do to conquer your fear is what they do. Shut the eyes of your face and open the eyes of your hands. Let's make a deal: tonight, when you go to bed and put out the light, if anything makes you afraid, close your eyes, carefully get out of bed, and try to see what it is that's making you scared. But do it using your hands as eyes... and tomorrow tell me how you're getting on with the fear".

Marina accepted, but she was rather worried. She knew she would need to be brave to close her eyes and go and touch whatever it was that was frightening her; but she was willing to try because she was already too old for this. When her parents took her to bed, she herself put out the light. After a little while, she felt afraid of one of the shadows in the bedroom. Following the advice of Aunt Valerie, she closed the eyes of her face and opened the eyes of her hands. And, summoning up all her courage, she went over to touch that mysterious shadow...

The next morning Marina came running into the kitchen, a big smile on her face, and a song on her lips. "The monster is so soft and smooth!..." she cried,
"It's my teddy bear!

"""

prompt = f""" Give the response in the following form:

1. Summary: Summerize the ```{text}```

2. Moral of the story: Give the moral of the ```{text}```

3. Populate the response in a JSON format
"""
```


```python
response = get_completion(prompt)
print(response)
```

    {
      "Summary": "Marina was extremely afraid of the dark, but with the help of her Aunt Valerie, she learned to conquer her fear by using her hands as eyes to see what was scaring her. She discovered that the 'monster' in the dark was actually her teddy bear, and she was able to overcome her fear.",
      "Moral": "The moral of the story is to face your fears head-on and to look at them from a different perspective. By changing the way you see things, you can conquer your fears and realize that they may not be as scary as they seem."
    }


The json format can be useful incase an API is created that outputs the response to the query made from client side. Multiple options can be mentioned, retrieved and used in applications using this technique.

Another advantage of this method is that using this method, one can be safe from prompt injection.

#### 1.2. Ask for a structured output (Explained above)

Also, the structured output can be any format that is desireable. eg.


```python
text = f"""
explain the central characters in the epic ramayana in the order of their introduction.
"""
prompt =f"""
Share the response if {text} in json format with keys: S.no, Name, Relation to Rama.
"""
```


```python
response = get_completion(prompt)
print(response)
```

    {
      "characters": [
        {
          "S.no": 1,
          "Name": "Dasaratha",
          "Relation to Rama": "Father"
        },
        {
          "S.no": 2,
          "Name": "Rama",
          "Relation to Rama": "Main protagonist"
        },
        {
          "S.no": 3,
          "Name": "Sita",
          "Relation to Rama": "Wife"
        },
        {
          "S.no": 4,
          "Name": "Lakshmana",
          "Relation to Rama": "Brother"
        },
        {
          "S.no": 5,
          "Name": "Hanuman",
          "Relation to Rama": "Devotee and ally"
        },
        {
          "S.no": 6,
          "Name": "Ravana",
          "Relation to Rama": "Main antagonist"
        }
      ]
    }


#### 1.3. Check if conditions are satisfied or check assumptions required to do the tasks.


```python
text = f"""
Check if the color is in rainbow. If the color is not present, output "Color is not present".
"""

prompt = f"""
Check color: Black as per {text}.
"""

response = get_completion(prompt)
print(response)
```

    Color is not present.



```python
text = f"""
Check if the color is in rainbow. If the color is not present, output "Color is not present".
"""

prompt = f"""
Check color: Violet as per {text}.
"""

response = get_completion(prompt)
print(response)
```

    Yes, violet is a color in the rainbow.


#### 1.4. Few shot prompting.

Give successful examples of completing tasks then ask the model to perform the task. eg.


```python
text = f"""
Give the responses in the style consistant to the text below.

Free lunch in the office? That’s lit!
I come into the office every day because I have such bad FOMO.
He called out sick 23 times this year – no cap.
Are you still salty that she got the promotion and you didn’t?
She’s a huge T-Swift stan – let’s try to get her tickets.

"""
prompt = f"""
Convert the sentence ```I am a huge Cricket fan and I miss playing cricket now.``` as per the tonality and style of {text}.
"""
response = get_completion(prompt)
print(response)
```

    I'm a massive Cricket fan and I lowkey miss playing cricket right now.



```python
prompt = f"Convert the sentence ```The air to too polluted. I am going to go to a hillside resort to relax``` as per the tonality and style of {text}"

response = get_completion(prompt)
print(response)
```

    The air is straight up polluted. I'm about to dip to a hillside resort to chillax.


### Principle 2: Give the model time to think

#### 2.1 Specify the steps needed to complete a task. eg:


```python
text = f"""
Give the responses in the style consistant to the text below.

Free lunch in the office? That’s lit!
I come into the office every day because I have such bad FOMO.
He called out sick 23 times this year – no cap.
Are you still salty that she got the promotion and you didn’t?
She’s a huge T-Swift stan – let’s try to get her tickets.

The format of the response should be as below:
- Point 1 : Response to the Prompt
- Point 2 : Total number of words in the response
- Point 3 : JSON response with keys response and countWords
"""
prompt = f"""
Convert the sentence ```I am a huge Cricket fan and I miss playing cricket now.``` as per the tonality and style of {text}.
"""
response = get_completion(prompt)
print(response)
```

    - Response to the Prompt: I am a massive Cricket enthusiast and I'm really missing playing cricket right now.
    - Total number of words in the response: 12
    - JSON response: {"response": "I am a massive Cricket enthusiast and I'm really missing playing cricket right now.", "countWords": 12}


Observe the model is hallucinating in calculating the length of words


```python
prompt = f"""
Count the number of words in the text: "I am a massive Cricket enthusiast and I'm really missing playing cricket right now."
"""

response = get_completion(prompt)
print(response)
```

    14



```python
text = f"""
Your task is to give the responses in the style consistant to the text below.

Free lunch in the office? That’s lit!
I come into the office every day because I have such bad FOMO.
He called out sick 23 times this year – no cap.
Are you still salty that she got the promotion and you didn’t?
She’s a huge T-Swift stan – let’s try to get her tickets.


The format of the response should be as below:
- Point 1 : Response to the Prompt
- Point 2 : Total number of words in the response
- Point 3 : JSON response with keys response and countWords
"""
prompt = f"""
Convert the sentence ```I am a huge Cricket fan and I miss playing cricket now.``` as per the tonality and style of {text}.
"""
response = get_completion(prompt)
print(response)
```

    - Point 1 : I am a massive Cricket enthusiast and I am currently yearning to engage in a game of cricket.
    - Point 2 : 15
    - Point 3 : {"response": "I am a massive Cricket enthusiast and I am currently yearning to engage in a game of cricket.", "countWords": 15}


The character length is 18, but the model is give the length as 15. This hallucination is bit problematic. Need to see tools and tactics to remove this specific type of hallucination.

#### 2.2 Instruct the model to work out its own solutions before running to a conclusion.


```python
sample = f"""
Free lunch in the office? That’s lit!
I come into the office every day because I have such bad FOMO.
He called out sick 23 times this year – no cap.
Are you still salty that she got the promotion and you didn’t?
She’s a huge T-Swift stan – let’s try to get her tickets.
"""
query = f"""
Your task is to give the responses in the style consistant to the {sample}. You should follow the following steps before sharing the response:
Step 1 : Convert the text in the the style and tone of {sample}.

Step 2: Count the words coming in the response. Do not randomly generate word count but really count each individual word.

Step 3: Recalculate the words and see if the words match with the above step. Only populate the count of words when the solutions match.

Step 4. Present the optput in the format below ```

- Point 1 : Response to the Prompt
- Point 2 : Total number of words in the response
- Point 3 : JSON response with keys response and countWords```
"""
prompt = f"""
Convert the sentence ```I am a huge Cricket fan and I miss playing cricket now.``` as per instructions provided in the {query}.
"""
response = get_completion(prompt)
print(response)
```

    ```
    - Point 1 : I'm a massive Cricket enthusiast and I'm currently yearning to play cricket.
    - Point 2 : 12
    - Point 3 : {"response": "I'm a massive Cricket enthusiast and I'm currently yearning to play cricket.", "countWords": 12}
    ```



```python
sample = f"""
Free lunch in the office? That’s lit!
I come into the office every day because I have such bad FOMO.
He called out sick 23 times this year – no cap.
Are you still salty that she got the promotion and you didn’t?
She’s a huge T-Swift stan – let’s try to get her tickets.
"""
query = f"""
Your task is to give the responses in the style consistant to the {sample}. You should follow the following steps before sharing the response:
Step 1 : Convert the text in the the style and tone of {sample}.

Step 2: Count the words coming in the response. Do not randomly generate word count but really count each individual word.

Step 3: Recalculate the words and see if the words match with the above step. Only populate the count of words when the solutions match.

Step 4. Present the optput in the format below ```

- Point 1 : Response to the Prompt
- Point 2 : Total number of words in the response
- Point 3 : JSON response with keys response and countWords```
"""
prompt = f"""
Convert the sentence ```My parents do not understand me. Give me some solution.``` as per instructions provided in the {query}.
"""
response = get_completion(prompt)
print(response)
```

    ```
    - Point 1 : My folks just don't get me. Can you drop some knowledge?
    - Point 2 : 11
    - Point 3 : 
    {
      "response": "My folks just don't get me. Can you drop some knowledge?",
      "countWords": 11
    }
    ```


As can be seen from the solution, the hallucination is now gone, plus the quality of the response has also improved.
