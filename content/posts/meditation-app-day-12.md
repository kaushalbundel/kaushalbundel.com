+++
title = "Notes on Building a Meditation App (Day 12)"
author = ["Kaushal Bundel"]
date = 2024-03-12T00:00:00+05:30
lastmod = 2024-03-12T00:21:20+05:30
tags = ["business", "meditationapp", "Business", "DevNotes"]
categories = ["MeditationApp"]
draft = false
+++

### <span class="org-todo todo TODO">TODO</span> An exciting new feature has been launched by Flutterflow which can be quite useful for user onboarding. This feature is called "walkthrough". Through this feature, I can do entire app walkthrough while the user first logs in the app. 

-   [Flutterflow demo on app walkthrough](https://www.youtube.com/watch?v=FFpR1SDrZEQ)


### <span class="org-todo todo TODO">TODO</span> Another exiting tutorial by "[The Digital Pro's NoCode Academy](https://www.youtube.com/@the_digitalpro)" on  "[building beautiful charts](https://www.youtube.com/watch?v=Dr5xHfk1nQY&ab_channel=TheDigitalPro%27sNoCodeAcademy)" in Flutterflow. This has a special utility for me as with this I could create the date wise charts for "Meditation completion" and "Mood Board Completion" tracking. {#another-exiting-tutorial-by-the-digital-pro-s-nocode-academy-on-building-beautiful-charts-in-flutterflow-dot-this-has-a-special-utility-for-me-as-with-this-i-could-create-the-date-wise-charts-for-meditation-completion-and-mood-board-completion-tracking-dot}


### <span class="org-todo todo TODO">TODO</span> - Implement Good to have user experience {#implement-good-to-have-user-experience}

-   [Ripple Wave effect](https://marketplace.flutterflow.io/item/3UhgN09SYvqorpSOnYAv) : This can be used on the meditation page : **Implementation complete**


#### Implementation (Important from the POV of creating Custom Widgets) {#implementation--important-from-the-pov-of-creating-custom-widgets}

-   Reference Video: [Flutterflow Tutorial on Custom Widgets](https://www.youtube.com/watch?v=QUBS0KFfwB4&t=5s&ab_channel=FlutterFlow)

-   Documentation: [Flutterflown Documentation of Custom Widgets](https://docs.flutterflow.io/customizing-your-app/custom-functions/custom-widgets)

-   **Notes**
    -   The custom widget will always be a stateful widget

    -   Widget specific parameters can be defined

    -   For this specific example of creating ripple effect:
        -   The parameters are width, height, color and icon

        -   The visibility of the widget is conditional on the active status of the meditation

        -   The colors of the ripple effect are the primary app colors

        -   The icon is a pixel wide small circular icon with 0% transparency so that the focus could just be one the timer and progress bar


#### Final Implementation {#final-implementation}

![Final Implementation of Ripple Effect](/ox-hugo/ripple-effect.gif)

- I think the ripple effect looks cool here. The frame rate for the gif could be a bit higher but it is a nice visual addition in the app.
