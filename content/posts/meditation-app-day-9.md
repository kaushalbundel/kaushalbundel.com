+++
title = "Notes on Building a Meditation App (Day 9)"
author = ["Kaushal Bundel"]
date = 2024-02-29T00:00:00+05:30
lastmod = 2024-02-29T19:43:58+05:30
tags = ["business", "meditationapp", "Business", "DevNotes"]
categories = ["MeditationApp"]
draft = false
+++

## Today's Implementation {#today-s-implementation}


### <span class="org-todo done DONE">DONE</span> Design consistancy should be ensured (eg. in some places "back" is a button while on others it is an Appbar icon) {#design-consistancy-should-be-ensured--eg-dot-in-some-places-back-is-a-button-while-on-others-it-is-an-appbar-icon}

-   State "DONE"       from "IN-PROGRESS" <span class="timestamp-wrapper"><span class="timestamp">[2024-02-29 Thu 16:11]</span></span>
-   State "IN-PROGRESS" from "TODO"       <span class="timestamp-wrapper"><span class="timestamp">[2024-02-28 Wed 21:14]</span></span>

- [x] Meditation Notes page: "Save" button navigation to notes detail is not working
    -   The updates stopped working after 13th Feb (Check Logs)

    -   Things Tried:

        -   Reference session parameter generated on the meditation page and passed the value of corresponding session onto Meditation Notes page

        -   Reference session document generated on the meditation page and passed the value of corresponding session onto Meditation Notes page

        -   If things, do not work out then just created another collection for Notes

        ---

        -   Core Problem: The meditation "session" is not getting created resulting in the failure of collection reference of "session" collection which is culminating in sync failure. The navigation is scheduled after sync, hence with the unsuccessful sync the navigation is also getting blocked.
            -   Solution: There was a problem with rules deployment on Firbase owing to which the sessions collection was not getting synced. With the redeployment of rules, syncing and rest of the implementation is working fine.


### <span class="org-todo done DONE">DONE</span> Mood Tracking widget changes on Homepage (Last Tracked Date and Streak) {#mood-tracking-widget-changes-on-homepage--last-tracked-date-and-streak}

-   State "DONE"       from "IN-PROGRESS" <span class="timestamp-wrapper"><span class="timestamp">[2024-02-29 Thu 16:28]</span></span>
-   State "IN-PROGRESS" from "TODO"       <span class="timestamp-wrapper"><span class="timestamp">[2024-02-29 Thu 16:17]</span></span>


#### Implementation Notes {#implementation-notes}

-   The implementation of "Last Tracked" is very simple. It involves a single "Query collection" creation, that will enable me to pass the last mood-logged date.

-   I will have to remove the "streak" widget from the "Homepage". Here is my rationale:
    1.  To implement the entire streak I will have to query the entire "mood" collection on the "Homepage". This will have a detrimental effect on page loading time. "Homepage" should be swift and friction free and I do not want to slow it down.

    2.  I will anyways show the streak information on a graph view (for both mood tracking and meditation tracking) (Next release). Spending time on implementation now will be redundant effort.


### <span class="org-todo todo BACKLOG">BACKLOG</span> UI improvements on the Mood Tracking page (As of now it is confusing the way choice chips are being displayed-Add a indicative heading maybe) {#ui-improvements-on-the-mood-tracking-page--as-of-now-it-is-confusing-the-way-choice-chips-are-being-displayed-add-a-indicative-heading-maybe}

-   State "IN-PROGRESS" from "TODO"       <span class="timestamp-wrapper"><span class="timestamp">[2024-02-29 Thu 16:29]</span></span>


#### Implementation Notes {#implementation-notes}

-   I am moving this task to backlog, the reason is I feel that UI aspect of the app needs to be improved to a huge extent. This task will be picked up as the other UI tasks are picked up.
