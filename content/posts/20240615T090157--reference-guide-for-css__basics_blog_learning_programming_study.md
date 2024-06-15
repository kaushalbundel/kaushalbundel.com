+++
title = "Reference Guide for CSS"
author = ["Kaushal Bundel"]
date = 2024-06-15T00:00:00+05:30
publishDate = 2024-06-15T00:00:00+05:30
tags = ["CSS"]
categories = ["CSS"]
draft = false
+++

### CSS (Cascading Style Sheet) {#css--cascading-style-sheet}

CSS is nothing but the collection of selectors, their properties and values that help in styling the website in a way that is desired.


### Rules of CSS {#rules-of-css}

Rules are the order in which the CSS is applied on a web page.

1.  Rule 1: Specificity

    The more specific the rule, the higher is the priority
    ```css

    h, a {
    y color: green; /*Type selectors (Lowest Specifity)*/
    }

    .text-block{
        background-color: yellow; /* class selector, denote by ".", (Medium Specifity)*/
    }

    #text-block{
        color: teal; /*id selector, denoted by "#" (Highest Specifity)*/
    }
    /* {
       color: white; /*Universal selector, No specifity*/
       }

    ```

2.  Rule 2: Inheritance

    The descendants will inherit the rules applied to the ancestors. An exception to this rule is that when an element is directly targeted, than the specifity rule will apply.
    Only certain properties will be applicable to the descendants (eg. Typographical Properties (color, font-size, font-family etc.))

<!--listend-->

1.  Rule 3: Last Applied

    Everything being equal, the last applied rule is the winner.


### [MDN Properties Reference](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference#index) {#mdn-properties-reference}
