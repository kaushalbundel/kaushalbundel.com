+++
title = "Notes on Building a Meditation App (Day 8)"
author = ["Kaushal Bundel"]
date = 2024-02-28T00:00:00+05:30
lastmod = 2024-02-28T21:16:08+05:30
tags = ["business", "meditationapp", "Business", "DevNotes"]
categories = ["MeditationApp"]
draft = false
+++

## Today's Implementation {#today-s-implementation}


### <span class="org-todo todo IN_PROGRESS">IN-PROGRESS</span>: Design consistancy should be ensured (eg. in some places "back" is a button while on others it is an Appbar icon) {#design-consistancy-should-be-ensured--eg-dot-in-some-places-back-is-a-button-while-on-others-it-is-an-appbar-icon}

-   State "IN-PROGRESS" from "TODO"       <span class="timestamp-wrapper"><span class="timestamp">[2024-02-28 Wed 21:14]</span></span>


#### Implementation Details {#implementation-details}

Pages where back button is a "button"

-   [x] Track your mood page

Pages with design changes

-   [x] Meditation Notes page: Top container(Date) is overflowing
-   [x] Meditation Notes page: The gap between the date and the title field needs to be reduced
-   [x] Meditation Notes page: Box label needs to work properly
-   [ ] Meditation Notes page: "Save" button navigation to notes detail is not working
    -   The updates stopped working after 13th Feb (Check Logs)

    -   Things Tried:
        -   Reference session parameter generated on the meditation page and passed the value of corresponding session onto Meditation Notes page

        -   Reference session document generated on the meditation page and passed the value of corresponding session onto Meditation Notes page

        -   If things, do not work out then just created another collection for Notes

General Information

- [x] Text input boxes should have the label and help text displayed uniformly through out the application

App bar should be enabled on the below pages

- [x] Meditation Page
- [x] Meditation Notes Page
