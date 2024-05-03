+++
title = "Configuring Screen Time on Apps"
author = ["Kaushal Bundel"]
date = 2024-05-03T11:56:00+05:30
publishDate = 2024-05-03T00:00:00+05:30
tags = ["Product Management"]
categories = ["Product", "Behavior Science"]
draft = false
+++

The Note tries to understand mobile screen time control and presents current and proposed strategies. The inspiration of the article came from an excellent blog-post by Kristen Berman and her excellent product breakdown blog ([kristenberman.substack.com](https://kristenberman.substack.com/)). Do subscribe!!


## Introduction {#introduction}

In behavioral science, the problems affecting behavior can be segregated in i-frame and s-frame.

i-frame refers to individual frame of reference. Here the onus is on the individual to take action on the basis of their motivation, habits, biases and mindset.

s-frame refers to situational frame of reference. The onus lies on the context, situation and environment that influences the user to take action.


## i-frame and s-frame from the point of view of app usage {#i-frame-and-s-frame-from-the-point-of-view-of-app-usage}

**i-frame**: This consist of tools that aid in changing users behaviors. The onus is on the user to initiate action. The article offers excellent analogy :

> &lt;i-frame intervention is&gt; like adjusting the game's settings to play better, but without changing the game’s rules. For example, you can set app limits or schedule downtime. Great features, but they typically require you (read: the user/individual) to opt into changing your behavior.

**s-frame**: This consist of the fundamental aspect of app behavior, making systemic changes to the environment itself. This means redesigning digital environment so that it discourage excessive app usage. An imaginary example could be "X" making the feed more boring and thereby users to go off the after "x" time.


## i-frame strategies {#i-frame-strategies}

Companies generally go about making changes in their apps from i-frame side of things. Often these changes are easier to implement as compared to s-frame changes. These changes include monitoring, analytics and reporting app usage and they work by asking a opt in from the user:

-   The "digital wellbeing app" in android is a very good example of this. This works by users opting in to see their usage statistics. The app provides access to Dashboard, Bedtime mode, Focus mode and Notification Management. These tools can be further divided into following categories:
    -   Suggestive Measures: Bedtime mode, Dashboard and Notification fall to this category. They show current status to the user and the expectation is that user after being made aware of the current situation(High phone usage and/or late night phone usage) will take actions on their own accord. They give responsibility to the user and in my personal experience the result is infrequent at best and absolute failure at most.

    -   Forceful Measures: Focus Mode forces the user to disconnect from the app completely. This is enabled by either setting up a schedule or blocking the app from use. The feature gives the option to turn off the focus mode for a brief while (which I think does a dis-service to the whole concept).


## s-frame strategies {#s-frame-strategies}

s-frame interventions are difficult to make as they seek to the change the inherent nature of the product. They do built in implementation that actively work to reduce the usage. I was not able to find many s-frame interventions in Android. But a few interventions that control usage could be:

1.  Relative vs Absolute: We have options to set the number of hours an app should be used. This is a flawed method. This issue being absolutes do not work but relative work very well. Instead of asking the user to set hours, the app should dictate the change in usage statistics. The app should figure out the usage statistics and automatically offset the usage to be 10% less than the previous week's usage.

2.  Design for what you want people to do vs what you don't want them to do.

    > Dog trainers would never tell the dog to “stop running” or “stop jumping.” Instead, they recommend saying “sit” or “come.” By telling dogs (and people) what they should do, we focus on the behavior change needed to succeed.

    Thus, instead of telling the users that the usage time is complete the app should block the user to block from using the app completely.

3.  Reducing the attractiveness of usage instead of disabling usage: In the current situation the usage is typically blocked by using a notification that gives the usage information and asks or sometimes forces the user to discontinue the app usage by blocking the app. In the new pattern the color palette should be changed to "grey scale" after a specific period of time. The user should not be able to revert the color scale by their own agency. The grey scale should only be able to revert after spending time away from the app for "x" period of time.

---
