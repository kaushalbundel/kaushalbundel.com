+++
title = "Notes on Building a meditation app (Day 5)"
author = ["Kaushal Bundel"]
date = 2024-02-13T00:00:00+05:30
lastmod = 2024-02-13T17:18:43+05:30
tags = ["business", "meditationapp", "Business", "DevNotes"]
categories = ["MeditationApp"]
draft = false
+++

## Development Activity # 1 {#development-activity-1}

-   The user should be able to click the appropriate mood indicator and mark the mood for the day. After clicking appropriate indicator the indicator value should get stored in the database


### Implementation {#implementation}

1.  Page parameter(mood) created on the meditation page
2.  The mood value, which is stored in the widget state is passed from Homepage to the meditation page
3.  To store the value in firebase:
    1.  Add the field in the firebase database
    2.  Add the value on the firebase database on Flutterflow
    3.  Deploy the firebase database on Flutterflow

---

Problem: The value of the notes is not getting stored in the session collection, infact I am not sure where the value is getting stored 🧐

1.  Found the record where the notes details are being overwritten. The issue here is that I have taken the reference of the sessions collection which is stored in a persisted app state. This approach is wrong one, I will have to take reference of the session created on the session originator page and then transfer that session reference through the page parameter to the notes page. In the notes page, the specific session will be updated by taking the reference of the session parameter.

Status: Resolved

---

Problem: Session date and session start time is being picked retroactively ie. session date is 30/01/2024

1.  The date and time of the session were picked incorrectly as the values were captured using wrong parameter

Status: Resolved

---


## Development Activity # 2 {#development-activity-2}

-   The past values/mood faces of the mood indicator should be shown on the "Reflections" page


### Implementation {#implementation}

1.  I have checked the app and I feel in the present mode the functionality to show mood emojis on the "Reflections" Page does not make much sense. Reflections is related to the notes that are created after the meditation is performed while the mood checkin is typically for a day
2.  Also, it would actually make sense to log some comments from the user in the mood checkin flow to know their physical and mental state while logging their mood and it would also make sense to show these bits separately
3.  I can probably use existing components to enhance this functionality
4.  The two pending points will have to be covered in the new scope
    1.  [ ] Once the mood is registered by the user for the day, the faces should be visible on screen yet should remain uneditable by the user

    2.  [ ] The mood board should be refreshed the next day and should become editable for the user


### Plan {#plan}


#### <span class="org-todo todo TODO">TODO</span> To create a new section for capturing Mood Related information {#to-create-a-new-section-for-capturing-mood-related-information}

<!--list-separator-->

- <span class="org-todo todo TODO">TODO</span>  UI changes for capturing Moods

    <!--list-separator-->

    - <span class="org-todo todo TODO">TODO</span>  Mood Capture Entry on the "Homepage" 
    
            {{< figure src="/ox-hugo/_20240213_170455screenshot.png" >}}

        
    <!--list-separator-->

    - <span class="org-todo todo TODO">TODO</span>  Navigate the user to a new page where mood information can be captured 

        {{< figure src="/ox-hugo/_20240213_170526screenshot.png" >}}
        
<!--list-separator-->

- <span class="org-todo todo TODO">TODO</span>  UI changes for showing Mood information

    <!--list-separator-->

    - <span class="org-todo todo TODO">TODO</span>  Combine this information with "Reflections" page by showing the information side by side in a tab view

<!--list-separator-->

- <span class="org-todo todo TODO">TODO</span>  Backend changes

    <!--list-separator-->

    - <span class="org-todo todo TODO">TODO</span>  "mood" field needs to be removed from the "sessions" collection

    <!--list-separator-->

    - <span class="org-todo todo TODO">TODO</span>  A new  collection "mood", needs to be created that will be similar to the reflection's and that will store mood related values

        ---


## Additional Activities {#additional-activities}

-   Completed UI/UX improvements like adding box shadows, rounding the edges of the containers and forcing size constraints on some of the containers

---


## Flutterflow update {#flutterflow-update}

-   Just saw a "Route Setting" option in the Properties panel on the page level. This setting allows me to define page routes and establish if the specific page requires authentication or not. This can be super helpful in defining the user flow at the end stage of the project
