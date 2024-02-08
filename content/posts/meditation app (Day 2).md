+++
title = "Notes on Building a meditation app (Day 2)"
author = ["Kaushal Bundel"]
date = 2024-02-08T00:00:00+05:30
lastmod = 2024-02-08T19:26:40+05:30
tags = ["business", "meditationapp", "Business", "DevNotes"]
categories = ["MeditationApp"]
draft = false
+++

## Development Activity {#development-activity}


### Task Adding Ambient music to the meditation session {#task-adding-ambient-music-to-the-meditation-session}

-   Option 1: Create a local app state, store the value of the widget state in that app state. Use the app state in the meditation section
-   Option 2: Create a page parameter, Pass the widget state in the page parameter and use the page parameter in the meditation session

So far, having tried both of these methods, I am not able to get the looping music to work. In both of the above options, the app was not compiling at all.

Google search resulted in the following answer [Play Background music on Loop (Credit: Janos Kiss)](https://community.flutterflow.io/c/community-custom-widgets/post/play-background-music-on-loop-custom-actions-MeEMMe5JdmsZQFM)

-   Implementation configured in the app.

-   **Problem** : Not able to listen to the sound.
    -   Diagnosis using "Inspect" - Chrome Dev Tools
        -   The error was "Error initializing or playing audio from asset: (4) Failed to load URL"

        -   On further search I found out that the online compiler provided by flutter flow does not enable sound ([Flutterflow community query](https://community.flutterflow.io/database-and-apis/post/using-pud-dev-just-audio-not-able-to-load-asset-audio-file-mp3-tawxf9wYAwRUsZT))

    -   As a series of next steps I would have to download the app locally and would need to do testing on mobile
        -   I would need additional help on this as I can not make this work at the present moment.
