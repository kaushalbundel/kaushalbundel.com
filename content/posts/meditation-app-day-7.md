+++
title = "Notes on Building a Meditation App (Day 7)"
author = ["Kaushal Bundel"]
date = 2024-02-27T00:00:00+05:30
lastmod = 2024-02-27T20:44:17+05:30
tags = ["business", "meditationapp", "Business", "DevNotes"]
categories = ["MeditationApp"]
draft = false
+++

## Note on a week-long absence {#note-on-a-week-long-absence}

Well, I just recovered from a severe viral infection. A changing weather and a family function triggered the concern. Things were a bit difficult but I am learning to take these circumstances in my stride. Thanks to the wonder of modern medicine and love of near ones.🙏🏼


## Recap of the last session {#recap-of-the-last-session}

-   Completed the UI for Mood Tracker

-   Streamlined how reflection(notes after meditation session) and related information are stored in the backend

-   Configured backend to show correct information on the reflection page


## Today's Implementation {#today-s-implementation}


### <span class="org-todo done DONE">DONE</span> Backend changes {#backend-changes}


#### <span class="org-todo done DONE">DONE</span> "mood" field needs to be removed from the "sessions" collection {#mood-field-needs-to-be-removed-from-the-sessions-collection}

<!--list-separator-->

-  Implementation Reference

    -   For correct implementation the field values should be changed on both flutterflow and firebase console.


#### <span class="org-todo done DONE">DONE</span> A new collection "mood", needs to be created that will be similar to the reflection's and that will store mood related values {#a-new-collection-mood-needs-to-be-created-that-will-be-similar-to-the-reflection-s-and-that-will-store-mood-related-values}

<!--list-separator-->

-  Important fields/types while defining the structure of mood collection

    -   Mood Tracking Date : Date

    -   Tracked Mood : String

    -   Tagged emotions : list of String

    -   Mood Note: String

<!--list-separator-->

-  Implementation Reference

    -   Basic collection structure added on the firebase console and flutterflow backend. Rules deployed successfully

    -   Saving mood tracking responses on the backend
        -   Saving the information from the relevant widget state is smooth except for the Tagged Emotions
            -   The Tagged Emotions concern is resolved by having a several if-else statements on the  mood state widget(radio button) and saving the corresponding choicechip responses

    -   Issue Identified : I am not able to click on some chips while testing the app
        -   The concern is that due to size constraints related to the container. The choicechips are overflowing the defined container size. This can be fixed easily by just adjusting the chip spacing and row distance in choicechips properties.


### <span class="org-todo done DONE">DONE</span> UI changes for showing Mood information {#ui-changes-for-showing-mood-information}


#### <span class="org-todo done DONE">DONE</span> Combine this information with "Reflections" page by showing the information side by side in a tab view {#combine-this-information-with-reflections-page-by-showing-the-information-side-by-side-in-a-tab-view}

<!--list-separator-->

-  Implementation Reference 

    -   Implementation is quite simple. Flutterflow provides a tab-bar option that can be used to land the users on a single page. A user can then select the appropriate tab to navigate to that tab

    -   Then its about creation of individual pages, which can be accomplished by using a list view. A list view can populate values from the database and show corresponding items in the designed format
        -   To show the values query collection needs to be enabled for that specific list view

        -   Often there might be problems when lots of documents are being loaded simultaneously. This can be rectified by enabling infinite scroll and loading the data as and when required

    -   Implementation Screenshots
        -   My Mood Section displaying logged-in mood

        {{< figure src="/ox-hugo/_20240227_201721screenshot.png" >}}
        
        -   My Reflections section displaying logged-in reflections/notes
        
        {{< figure src="/ox-hugo/_20240227_201855screenshot.png" >}}
    


## New Tasks {#new-tasks}


#### <span class="org-todo todo TODO">TODO</span> Should there be any limitation on the size of the textfield (Mood Page and Reflections Page)? {#should-there-be-any-limitation-on-the-size-of-the-textfield--mood-page-and-reflections-page}


#### <span class="org-todo todo TODO">TODO</span> Design consistancy should be ensured (eg. in some places "back" is a button while on others it is an Appbar icon) {#design-consistancy-should-be-ensured--eg-dot-in-some-places-back-is-a-button-while-on-others-it-is-an-appbar-icon}


#### <span class="org-todo todo TODO">TODO</span> Mood Tracking widget changes on Homepage (Last Tracked Date and Streak) {#mood-tracking-widget-changes-on-homepage--last-tracked-date-and-streak}


#### <span class="org-todo todo TODO">TODO</span> UI improvements on the Mood Tracking page (As of now it is confusing the way choice chips are being displayed-Add a indicative heading maybe) {#ui-improvements-on-the-mood-tracking-page--as-of-now-it-is-confusing-the-way-choice-chips-are-being-displayed-add-a-indicative-heading-maybe}


#### <span class="org-todo todo TODO">TODO</span> Nav-Bar improvements {#nav-bar-improvements}


#### <span class="org-todo todo TODO">TODO</span> Flutterflow warnings {#flutterflow-warnings}
