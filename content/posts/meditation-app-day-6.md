+++
title = "Notes on Building a Meditation App (Day 6)"
author = ["Kaushal Bundel"]
date = 2024-02-16T00:00:00+05:30
lastmod = 2024-02-16T17:06:16+05:30
tags = ["business", "meditationapp", "Business", "DevNotes"]
categories = ["MeditationApp"]
draft = false
+++

### Additional Information

Flutterflow team recently released some exceptional videos to help with the UI problems that I am currently facing. These problems include:

-   I am creating for one set screen and in reality the app will be used in multiple devices of varied sizes. A common guide for getting a size reference is available on android developer guide.

{{< figure src="/ox-hugo/_20240216_014034screenshot.png" >}}

Even though the size that I have chosen makes sense, still due to faulty layout configuration negative spaces/gaps will get affected if the screen size deviates from the standard one.

-   There is a problem in certain pages where I have not utilized the proper method of alignment and simply have relied on the padding.


### Note to self: To check the following video links during UI improvement stage {#note-to-self-to-check-the-following-video-links-during-ui-improvement-stage}

-   [Flutterflow channel video on "How to use alignment and Padding"](https://www.youtube.com/watch?v=n3XtbL4xJBE)

-   [Flutterflow Channel Video Mastering Layouts](https://www.youtube.com/watch?v=_QhCrh00xiI)


### Development Activity {#development-activity}


#### <span class="org-todo done DONE">DONE</span> To create a new section for capturing Mood Related information {#to-create-a-new-section-for-capturing-mood-related-information}

<!--list-separator-->

- <span class="org-todo done DONE">DONE</span>  UI changes for capturing Moods

    <!--list-separator-->

    - <span class="org-todo done DONE">DONE</span>  Mood Capture Entry on the "Homepage" <span class="tag"><span class="ATTACH">ATTACH</span></span>

        -   Keys to the design
            -   The design should be simple to implement

            -   The design should be minimal so that so that the feature of meditation (which is also minimal in design) should seem as running in sync

            -   The entry point should convey sparse but useful information about the mood tracking
                -   Information such as Total Streak days, Last tracked days, Tracking done today or not should be captured on the "Homepage" widget

                -   Sample design that can be used in the project with little tweaks ([Credit- Dribble: Habitomic by Soheil Najafi](https://dribbble.com/shots/15882374/attachments/7708524?mode=media))

        {{< figure src="/ox-hugo/_20240216_132623screenshot.png" >}}

        -   Final "Mood Capture Entry" on the Homepage

        {{< figure src="/ox-hugo/_20240216_141859screenshot.png" >}}

        -   The icon on the circle will change its color to "Green" so as to indicate that the tracking for today has been completed

    <!--list-separator-->

    - <span class="org-todo done DONE">DONE</span>  Navigate the user to a new page where mood information can be captured <span class="tag"><span class="ATTACH">ATTACH</span></span>

        -   The design blueprint created in [(Notes on building meditation app - Day 5](https://kaushalbundel.com/posts/meditation-app-day-5/)) seem good enough starting point for initial design

        -   Flutterflow has a very interesting widget (choicechips) that can be enabled to show the different options as the user selects a specific mood on the mood selection board [(Flutterflow: Choicechip documentation](https://docs.flutterflow.io/widgets-and-components/widgets/form-elements-1/choicechips))

        -   In my previous notes [(Notes on building meditation app - Day 5](https://kaushalbundel.com/posts/meditation-app-day-5/)), instead of adding "emotion related word cloud", it would make more sense to add the probable causes of mood. Below I have added some of the probable causes of the different moods
            -   Word cloud for "Sad" Mood
                -   Stress, loneliness, grief, illness, fatigue, boredom, rejection, disappointment, insecurity, failure, trauma, change, guilt, envy, lack of purpose, poor self-esteem, weather, hormones, medication, relationship issues.

            -   Word cloud for "Confused" Mood
                -   Uncertainty, information overload, conflicting instructions, complexity, lack of clarity, decision-making, overwhelming choices, contradictory evidence, disorganization, fatigue, sleep deprivation, multitasking, medication side effects, cognitive impairment, conflicting emotions, sensory overload, lack of direction, unfamiliarity, language barrier, academic pressure.

            -   Word cloud for "Indifferent" Mood
                -   Apathy, boredom, detachment, lack of interest, burnout, emotional exhaustion, monotony, disillusionment, complacency, resignation, disengagement, indifference, routine, lack of motivation, numbness, dissatisfaction, emotional detachment, unfulfilling experiences, lack of stimulation, feeling disconnected.

            -   Word Cloud for "Happy" Mood
                -   Love, success, achievement, laughter, gratitude, accomplishment, contentment, friendship, kindness, appreciation, fulfillment, joy, harmony, serenity, optimism, celebration, excitement, relaxation, satisfaction, connection.

            -   Word Cloud for "Ecstatic" Mood
                -   Triumph, surprise, euphoria, exhilaration, elation, breakthrough, achievement, victory, passion, thrill, bliss, amazement, awe, rapture, wonder, delight, ecstasy, jubilation, exuberance, enchantment.

        -   Page implementation
            -   The mood selection is linked with the word cloud, with every mood selection enabling a change in the word cloud options

            -   Word cloud options are multi-select

            -   Back Button navigates to the "Homepage"

        {{< figure src="/ox-hugo/_20240216_170001screenshot.png" >}}
