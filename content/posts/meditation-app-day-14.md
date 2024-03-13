+++
title = "Notes on Building a Meditation App (Day 14)"
author = ["Kaushal Bundel"]
date = 2024-03-13
lastmod = 2024-03-13
tags = ["business", "meditationapp", "Business", "DevNotes"]
categories = ["MeditationApp"]
draft = false
+++

## Enabling Audio in the App {#enabling-audio-in-the-app}

This is a long standing task. I tried to implement this feature but was unsuccessful. Let's see how we fare now.


### Supporting Material {#supporting-material}

[Community Solution to the sound looping problem](https://community.flutterflow.io/c/community-custom-widgets/post/play-background-music-on-loop-custom-actions-MeEMMe5JdmsZQFM)

[Digital Pro's No Code Academy Tutorial on Custom Action](https://www.youtube.com/watch?v=yl2LOhJl964&ab_channel=TheDigitalPro%27sNoCodeAcademy)


### Important Background Context {#important-background-context}

**BuildContext**

-   In Flutter, the build context represents the location of a widget within the widget tree. It allows widgets to interact with other widgets and access data and services provided by higher-level widgets.


### Steps Completed {#steps-completed}

-   Used the code structure as provided in the Community Solution
    -   Created the custom actions and the app state variables

    -   Configured the app

-   Things not working (error: Error initializing or playing audio from asset: (4) Failed to load URL)
    -   Sound is still not working

    -   The navigation to "Homepage" when the "Stop" button is pressed on meditation page is not working as the "stopAudio" custom code is not working

    -   Instead of audioRef I have given the "assets/audio/music.mp3" link directly on the custom action but still the error is same

-   Next Steps
    -   Perhaps instead of loading the data from asset, I will have to download the data through the network
