+++
title = "Notes on Building a meditation app (Day 4)"
author = ["Kaushal Bundel"]
date = 2024-02-12T00:00:00+05:30
lastmod = 2024-02-12T17:19:53+05:30
tags = ["business", "meditationapp", "Business", "DevNotes"]
categories = ["MeditationApp"]
draft = false
+++

### Task continue from the previous day 

(Task: Adding a mood board to check on the user mood as soon as the user opens up the app) 

- [x]  The mood board should constitute a design that should indicate 5 faces


#### Implementation Notes

-   Feature design notes
    -   Option 1: Create a new component. Create 5 containers with different emoji faces. These different faces also have their corresponding color variants. The color switching will happen with the help of a radio button. When the radio button is clicked, the conditional display of emoji buttons will be triggered, displaying only the selected option. The problem with this implementation is how to control when two or more emojis are clicked one after another. There are no hooks that enable me to link these separate bits.

        {{< figure src="/ox-hugo/_20240212_135930screenshot.png" >}}

-   Option 2: Use the radio button feature. Create different options in the radio button category, add different emoji face just above the radio buttons and link the radio button using widget state.
    So far this option has worked well. I am going to use this option to implement this component.

    {{< figure src="/ox-hugo/_20240212_151830screenshot.png" >}}

    I have also done additional modifications in this component to make it re-configurable so that it can be used in future projects. This is done by adding variables such as moodBoardColor, iconUnselectColor and iconSelectColor.

-   Next steps:
    -   I can perhaps enhance this component by adding an option to add the values and corresponding emoji faces by taking these values from the backend table.

    -   The problem with this component is that since I am using two separate row components, I am not able to control the relative placement of these. Just a small formatting will result in orientation change. Perhaps this could be improved by using a slider widget.

-   **Note to Self**
    -   I need to be very careful while giving the values to any kind of widget. I added an extra space to the "smile" keyword ("smile ") and that screwed up the whole logic. It took me 15 mins to debug and correct the logic.

- [x] The user should be able view the mood board as soon as they open the app.

-   **Final Implementation Demo**

    [Demo Moodboard Widget](/ox-hugo/moodboardwidget.gif)

---

-   UI improvement points
    -   I have found some components in Flutterflow marketplace that can enhance the app from an UI POV
        -   [Confetti Overlay](https://marketplace.flutterflow.io/item/xqdpgTokWYjYaME3V8ZD) : This can be used to create a celebration tool if a user has complete a rewarding task

        -   [Device Screen Awake](https://marketplace.flutterflow.io/item/3QBvadjlapPVWjlubLy7) : This code can be used to keep the device screen awake (especially useful on the meditation page)

        -   [Ripple Wave effect](https://marketplace.flutterflow.io/item/3UhgN09SYvqorpSOnYAv) : This can be used on the meditation page
