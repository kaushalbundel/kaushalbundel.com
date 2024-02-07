+++
title = "Notes on Building a meditation app (Day 1)"
author = ["Kaushal Bundel"]
date = 2024-02-06T00:00:00+05:30
lastmod = 2024-02-06T21:06:54+05:30
tags = ["business", "meditationapp", "Business", "DevNotes"]
categories = ["MeditationApp"]
draft = false
+++

## Defining the Constraints {#defining-the-constraints}

1.  Feature Constraint: The time spent on an activity should be minimal, yet the feature/activity should offer relief from day-to-day stressors during that period.
2.  Feature Constraint: The activity should seamlessly integrate into daily routines.
3.  Developmental Constraint: I should be able to reuse already developed features such as the login flow, registration flow, meditation timer, and journal.
4.  Cost Constraint: The development cost should be limited to less than 50,000 INR.
5.  Time Constraint: The app should be live on either the Android Play Store or Apple App Store by the end of March.


## Expansion of features that have already been developed {#expansion-of-features-that-have-already-been-developed}


#### <span class="org-todo todo TODO">TODO</span> Adding ambient music to the meditation session {#adding-ambient-music-to-the-meditation-session}

<!--list-separator-->

- <span class="org-todo done DONE">DONE</span>  Adding ambient music track to the session (Started: <span class="timestamp-wrapper"><span class="timestamp">&lt;2024-02-06 Tue 07:30&gt;</span></span>)(Ended: <span class="timestamp-wrapper"><span class="timestamp">&lt;2024-02-06 Tue 08:30&gt;</span></span>)

<!--list-separator-->

- <span class="org-todo todo TODO">TODO</span>  A choice of 5 or more ambient tracks to choose from

<!--list-separator-->

- <span class="org-todo todo TODO">TODO</span>  Tracks to run through the duration of the session


#### <span class="org-todo todo TODO">TODO</span> Adding a mood board to check on the user mood as soon as the user opens up the app {#adding-a-mood-board-to-check-on-the-user-mood-as-soon-as-the-user-opens-up-the-app}


#### <span class="org-todo todo TODO">TODO</span> Improving UI {#improving-ui}

<!--list-separator-->

- <span class="org-todo todo TODO">TODO</span>  How to make buttons standout?

<!--list-separator-->

- <span class="org-todo todo TODO">TODO</span>  How to use different widgets so that the app looks pretty?


#### <span class="org-todo todo TODO">TODO</span> Improving UX {#improving-ux}

<!--list-separator-->

- <span class="org-todo todo TODO">TODO</span>  How to fit in separate components needed for the meditation session (like setting the time, setting the music, starting the session, collecting feedback after the session)?

<!--list-separator-->

- <span class="org-todo todo TODO">TODO</span>  How to improve the journaling experience?


## New Feature Design {#new-feature-design}


### <span class="org-todo todo TODO">TODO</span> Fitting the basic features (Journal and Meditation with the core premise of the app) {#fitting-the-basic-features--journal-and-meditation-with-the-core-premise-of-the-app}


### <span class="org-todo todo TODO">TODO</span> Develop a Tinder style quote gallery {#develop-a-tinder-style-quote-gallery}


#### <span class="org-todo todo TODO">TODO</span> Adding share links to social media {#adding-share-links-to-social-media}


### <span class="org-todo todo TODO">TODO</span> Redesigning the App to fit in different features {#redesigning-the-app-to-fit-in-different-features}


### <span class="org-todo todo TODO">TODO</span> Payment Gateway Integration?? {#payment-gateway-integration}


## Development Activity {#development-activity}


### Adding ambient music to the meditation session {#adding-ambient-music-to-the-meditation-session}


#### Commercial use music resources {#commercial-use-music-resources}

<!--list-separator-->

-  [Pixabay.com](https://pixabay.com/sound-effects/search/ambient/)

<!--list-separator-->

-  [videvo.net](https://www.videvo.net/royalty-free-sound-effects/ambience/)


#### Sound extensions {#sound-extensions}

There needs to be a balance between good audio output and low file size. The following extensions came up in the research.

1.  MP3: Widely supported and offers a good balance between audio quality and file size.
2.  AAC (Advanced Audio Coding): Similar to MP3, it provides good audio quality with reasonable file sizes.
3.  OGG Vorbis: Known for its efficient compression and decent audio quality.
4.  Opus: Designed for low bit rate audio, it offers good audio quality with small file sizes.

Flutterflow support mp3 by default. But if audio size becomes an issue then other formats should be explored.


#### Free online tool to cut audio to required length {#free-online-tool-to-cut-audio-to-required-length}

[Clideo.com](https://clideo.com/)


#### <span class="org-todo todo TODO">TODO</span> Not able to understand, how to integrate the app state with conditional action on the form. Search more or experiment with the Page Parameter definition to play selected sound. {#not-able-to-understand-how-to-integrate-the-app-state-with-conditional-action-on-the-form-dot-search-more-or-experiment-with-the-page-parameter-definition-to-play-selected-sound-dot}
