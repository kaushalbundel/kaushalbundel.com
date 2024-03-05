+++
title = "Notes on Building a Meditation App (Day 10)"
author = ["Kaushal Bundel"]
date = 2024-03-05T00:00:00+05:30
lastmod = 2024-03-05T05:41:18+05:30
tags = ["business", "meditationapp", "Business", "DevNotes"]
categories = ["MeditationApp"]
draft = false
+++

## Today's Implementation {#today-s-implementation}


### <span class="org-todo todo WAITING">WAITING</span> Nav-Bar improvements {#nav-bar-improvements}

-   State "WAITING"    from "IN-PROGRESS" <span class="timestamp-wrapper"><span class="timestamp">[2024-03-02 Sat 15:39] </span></span> <br />
    Flutter needs to be installed on the Device
-   State "IN-PROGRESS" from "TODO"       <span class="timestamp-wrapper"><span class="timestamp">[2024-03-02 Sat 15:23]</span></span>

Flutterflow includes three types of Nav-bar implementations: Flutter Default Nav Bar, Google Nav Bar and Floating Nav Bar. I had initially implemented  Flutter Default Nav Bar, the problem with the implementation was that the Nav Bar throws an error if you need a Nav bar on the pages for easy navigation that are not present on the Nav Bar (for eg. I do not have the meditation timer page on the nav bar yet I want the Nav bar to be present on the page for easy user navigation).

I had also changed the Nav Bar to Google Nav Bar. The problem with Google Nav Bar was that I do not like the look and feel of this specific Nav Bar. I also feel that the implementation was a bit unstable with the Nav Bar disappearing from the demo screen. I am unaware for the reason of this particular behaviour.

I was not able to implement the Floating Nav Bar. The app crashed while compiling no matter what I do with this Nav Bar.

I would have to search for a solution for this specific component by looking at the documentation.

Note: The documentation does not solve anything for me. But I have checked on question [Communinty Question: Nav Bar does not Render but it works?](https://community.flutterflow.io/discussions/post/nav-bar-doesn-t-render-but-it-works-uMksZwGbPznp4U6). The user has suggested to download the code and check, the nav bar should be working. The problem with the "Test Mode" is that the test mode depends upon the scaling and other factors of the local device.

-   In order to test this, I will have to setup flutter on my windows device.


### <span class="org-todo todo TODO">TODO</span> Flutterflow warnings {#flutterflow-warnings}

Majority of the warning are from the authentication/login flow.

-   Category 1: Navigation Action execution after a specific action

    The are two methods through which Navigation Action can be done. First, Navigation can be done using a Navigation Action. Second, Navigation can be done by setting the "Navigate Automatically" property on a specific action.

    As it is evident setting these two navigation methods simultaneously is not correct and thus the warning.

    The warning was rectified by simply turning off the "Navigate Automatically" property.

-   Category 2: Nullable App state variables

    The app state variables that have been defined should have a default value associated with them so that they do not have null error. Couple of my app state variables do not not have a default value.

    The two app state variables are timestamp related  and hence I have set the default value of 1/1/2024 12:00 AM and 1/1/2024 12:05 AM.

-   Category 3: Custom Action Related Values

    For the sound loop feature I have utilized some custom code from pub.dev. I was not able to implement the code ([Day 2-Dev Log](https://kaushalbundel.com/posts/meditation-app-day-2/)) and the code is unused at the moment. I intend to work on this at a later point in time, so I will leave the warnings as they are.

-   Category 4: Firestore rule setup

    So far due to continuous app testing, I have kept the firestore rule quite liberal. They will retain the same nature and will be changed during deployment.
