+++
title = "Notes on Building a meditation app (Day 3)"
author = ["Kaushal Bundel"]
date = 2024-02-11
lastmod = 2024-02-11T00:19:48+05:30
tags = ["business", "meditationapp", "Business", "DevNotes"]
categories = ["MeditationApp"]
draft = false
+++

## Development Activity {#development-activity}


### Task: Adding a mood board to check the user mood as soon as the app is opened {#task-adding-a-mood-board-to-check-on-the-user-mood-as-soon-as-the-user-opens-up-the-app}

-  [ ] The user should be able view the mood board as soon as they open the app

-  [ ] The user should be able to click the appropriate mood indicator and mark the mood for the day. After click appropriate indicator the indicator value should get stored in the database

-  [ ] The past values/mood faces of the mood indicator should be shown on the "Reflections" page.

-  [x] The mood board should constitute a design that should indicate 5 faces (sad, confused, indifferent, smiling and happy)

    {{< figure src="/ox-hugo/_20240210_141211screenshot.png" >}}

    -   Advanced designs to be explored, but the first round of implementation should be simple

**Implementation**

-   Good Icons are not available in the Flutterflow library. Custom icons should be added

Link:  [Flutterflow: How to add custom icons](https://docs.flutterflow.io/widgets-and-components/theme-settings/typography-and-icons)

Link to download free icons: [icomoon.io](https://icomoon.io/app/#/select) (This website has options for icons (free as well as paid) and along with just simple svg download, also generates "Dart class for Flutter")

-  [ ] Once the mood is registered by the user for the day, the mood board should be visible on screen yet should remain un-editable by the user

-  [ ] The mood board should be refreshed the next day and should become editable for the user


#### Implementation Notes {#implementation-notes}

-   A reusable component should be created that should have the following features

    -   Mood Indicator faces
    
    -   Mood Indicator animation that becomes active when the button is pressed. eg. as the lines of the indicator icon change color to blue on clicking in the example above
    
    -   Action to store the information in the appropriate db table


#### Note to self {#note-to-self}

-   There is a modal component option in the component library that gives an option of creating a modal window for capturing notes. This component can be used in the future.

-   There is also a ready component for toggling the app theme
