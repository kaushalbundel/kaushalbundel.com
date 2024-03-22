+++
title = "Understanding ChatGpt Prompt Engineering- Part II - An Iterative Approach"
author = ["Kaushal Bundel"]
date = 2024-03-21T14:00:13+05:30
lastmod = 2024-03-20T14:00:13+05:30
tags = ["LLM","chatGPT"]
categories = ["Beginner"]
draft = false
+++


# Prompt Engineering as an Iterative process

There is not single effective method for getting the desired results from the a LLM. For general tasks the process of getting response to a desired problem is simple, whereas for specific problems one needs to used iterative methods to arrive at desired results.

In addition sometime we just do not know what the final result will look like, in such situations moulding the LLM response is essential.

## Task: Write a set of tweets for a car launch


```python
datasheet = f"""
Hyundai has announced a voluntary recall for the Creta SUV. The variants powered by a 1.5-litre naturally aspirated petrol engine with the CVT automatic are affected by this recall.

Price: The Creta is priced between Rs 11 lakh and Rs 20.15 lakh (introductory ex-showroom pan India).

Variants: It is available in seven broad variants: E, EX, S, S(O), SX, SX Tech, and SX(O).

Colour Options: The Creta is available in six monotone and one dual-tone colour options: Robust Emerald Pearl, Fiery Red, Ranger Khaki, Abyss Black, Atlas White, Titan Grey and Atlas White with black roof.

Seating Capacity: It can accommodate five passengers.

Engine and Transmission: The Hyundai Creta comes with three powertrain choices:

1.5-litre naturally aspirated petrol (115 PS/ 144 Nm): 6-speed MT, CVT

1.5-litre turbo-petrol (160 PS/ 253 Nm): 7-speed DCT

1.5-litre diesel (116 PS/ 250 Nm): 6-speed MT, 6-speed AT

Claimed Fuel Efficiency:

1.5-litre petrol MT- 17.4 kmpl

1.5-litre petrol CVT- 17.7 kmpl

1.5-litre turbo-petrol DCT- 18.4 kmpl

1.5-litre diesel MT- 21.8 kmpl

1.5-litre diesel AT- 19.1 kmpl

Features: The Creta facelift comes with features like 10.25-inch displays (one for the infotainment system and the other for instrumentation) and connected car technology. It is also equipped with dual-zone AC, an 8-speaker Bose sound system, a panoramic sunroof, wireless phone charging, an 8-way power-adjustable driver’s seat, and ventilated front seats.

Safety: Safety features include six airbags, a 360-degree camera, electronic stability control, a tyre pressure monitoring system, and a few advanced driver assistance systems (ADAS).

Rivals: The Hyundai Creta competes with Kia Seltos, Maruti Grand Vitara, Toyota Hyryder, Skoda Kushaq, Volkswagen Taigun, Citroen C3 Aircross, and Honda Elevate.

Hyundai Creta N Line: Hyundai has launched the Creta N Line in India, starting from Rs 16.82 lakh (introductory, ex-showroom). We have detailed the differences between the Creta N Line and the Kia Seltos GT Line in real life images.

Hyundai Creta EV: The Hyundai Creta EV has been spotted testing overseas with the same LED DRLs and new aerodynamic alloy wheels.
"""
```

credit: [cardekho.com](https://www.cardekho.com/hyundai/creta)


```python
#loading the boiler plate code
import openai
import os
from dotenv import load_dotenv, find_dotenv #library to load the local environment variables jupyter
_=load_dotenv(find_dotenv()) 
api_key= os.getenv("OPENAI_API_KEY")
```


```python
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


```python
number_tweets = 5
prompt = f"""
As a Senior Content write, create {number_tweets} as per the data sheet specified by the text {datasheet}. The necessary conditions that should be satisfied while writing tweets is mentioned below:

1. Tweets should include features that a customer respectes and likes.

2. Data should to used to emphassise the statements made

3. Length of the tweets should not exceed 140 words.

"""

response = get_completion(prompt)
print(response)
```

    1. "Experience luxury and convenience with the Hyundai Creta's 10.25-inch displays, dual-zone AC, and Bose sound system. Stay connected on the go with connected car technology. #HyundaiCreta #LuxuryFeatures"
    
    2. "Safety first with the Hyundai Creta! Enjoy peace of mind with six airbags, a 360-degree camera, and electronic stability control. Drive with confidence. #SafetyFirst #HyundaiCreta"
    
    3. "Efficiency meets performance with the Hyundai Creta's range of powertrain choices. Choose from petrol, turbo-petrol, or diesel options for a smooth and powerful drive. #HyundaiCreta #PowerfulPerformance"
    
    4. "Stand out on the road with the Hyundai Creta's stylish colour options. Choose from six monotone and one dual-tone shades to match your personality. #HyundaiCreta #StylishDesign"
    
    5. "Upgrade your driving experience with the Hyundai Creta N Line. Enjoy sporty design elements and enhanced performance starting from Rs 16.82 lakh. #HyundaiCretaNLine #SportyDesign"


On the surface these tweets looks fine. But we can make improvements to them to make them better.


```python
number_tweets = 5
prompt = f"""
As a Senior Content write, create {number_tweets} as per the data sheet specified by the text {datasheet}. The necessary conditions that should be satisfied while writing tweets is mentioned below:

1. Tweets should include features that a customer respectes and likes.

2. Data should to used to emphassise the statements made

3. Length of the tweets should not exceed 140 words.

4. Please include emojis whereever needed.

5. The tonality of the tweet should symbolize a young men born in 2000's.
"""

response = get_completion(prompt)
print(response)
```

    1. "🚗 The Hyundai Creta is a game-changer with its 10.25-inch displays, connected car tech, and Bose sound system. Who wouldn't want to cruise in style with all these features? #HyundaiCreta #TechSavvy"
    
    2. "⚡️ Safety first! The Hyundai Creta comes equipped with six airbags, a 360-degree camera, and electronic stability control. Drive with peace of mind knowing you're protected. #SafetyFirst #HyundaiCreta"
    
    3. "🌈 Stand out from the crowd with the Hyundai Creta's vibrant colour options like Fiery Red and Robust Emerald Pearl. Express your personality with every drive! #ColourfulCreta #Hyundai"
    
    4. "🔋 Go green with the Hyundai Creta EV! Spotting testing overseas, this electric SUV is set to revolutionize the way we drive. Stay tuned for the future of mobility! #HyundaiCretaEV #GreenDriving"
    
    5. "🔥 Power and performance meet in the Hyundai Creta N Line! With a turbo-petrol engine and sporty design, this SUV is perfect for those who crave excitement on the road. #NLine #HyundaiCreta"


Let's imagine the car is launching on the day of the Holi festival and try to include the mood in the tweet copy. 


```python
number_tweets = 5
prompt = f"""
As a Senior Content write, create {number_tweets} as per the data sheet specified by the text {datasheet}. The necessary conditions that should be satisfied while writing tweets is mentioned below:

1. Tweets should include features that a customer respectes and likes.

2. Data should to used to emphassise the statements made

3. Length of the tweets should not exceed 140 words.

4. Please include emojis towards the end or in between the tweet text.

5. The tonality of the tweet should symbolize a young men born in 2000's.

6. As holi festival is near, please include references of colors and description of holi in these tweets. 

"""

response = get_completion(prompt)
print(response)
```

    1. "The Hyundai Creta is a technologically advanced SUV with a 10.25-inch display, Bose sound system, and panoramic sunroof 🚗💥 Get ready to add some color to your life with the vibrant range of color options available this Holi! #HyundaiCreta #HoliVibes"
    
    2. "Safety first with the Hyundai Creta! Equipped with six airbags, electronic stability control, and a 360-degree camera 🛡️💪 Drive confidently this Holi knowing you're protected in every journey. #SafetyFirst #HyundaiCreta #HoliCelebrations"
    
    3. "Experience luxury with the Hyundai Creta's dual-zone AC, wireless phone charging, and ventilated front seats 🌟🔌 Treat yourself this Holi to a comfortable and stylish ride with the Creta! #LuxuryRide #HyundaiCreta #HoliFestivities"
    
    4. "Efficiency meets performance with the Hyundai Creta's fuel-efficient engine options and advanced driver assistance systems 🌿🚗 Celebrate Holi with a smooth and eco-friendly drive in the Creta! #EfficientDrive #HyundaiCreta #HoliColors"
    
    5. "Stand out from the crowd with the Hyundai Creta N Line's sporty design and dynamic features 🏁🔥 Add a splash of excitement to your Holi celebrations with the bold and stylish Creta N Line! #SportyDrive #HyundaiCretaNLine #HoliFun"


These tweets look markedly better than the first set of tweets that the model returned and this shows that through this iterative process we can improve the way to get desired results.
