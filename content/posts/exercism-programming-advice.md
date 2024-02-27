+++
title = "Exercism Programming Advice"
author = ["Kaushal Bundel"]
description = "Response to a programming question raised by me on Exercism"
date = 2024-02-29T00:00:00+05:30
publishDate = 2024-02-29T00:00:00+05:30
tags = ["beginner", "programming"]
categories = ["programming"]
draft = false
+++

## Context {#context}

I am a novice programmer who used to hate programming earlier. Slowly I have started enjoying programming as an activity and [exercism.org](https://exercism.org/) has played a huge part in it. Exercism is tool to help learn programming, their are numerous language tracks, super interesting problems, absolutely free and the best part, amazing mentors that can mentor you on either a problem specific or a general way.

This conversation is one of such conversations that I had with my mentor for a specific problem that I was doing 7 months ago. Through this is for beginners but you never know, ideas and memories are same, one can be used when least expected.🤓


## My Question {#my-question}

>
>
> My question is not about this solution specifically, but more of a meta question triggered by this problem. My main challenge in this problem was thinking about all the test case scenarios and then accommodating them in the code. My current situation: After I see a problem, I try to think of a solution and possible set of test cases that my code should solve. But invariably my solution does not cover the whole suit of test cases. I tend to correct the code multiple times, so that it fits.
>
> My question here is: How do we get better in writing solution/code which covers these test cases? How to get better in thinking different possibilities that the code/solution could encounter and formulate them in code?


## Answer on Exercism {#answer-on-exercism}

**(Credit - Schlizohr on Exercism)**

> There is something thats called test driven development. in test driven development you first write tests for all edgecases and behaviors that exist. Then you exec the tests and they could fail. Then you start implementing your solution. That is a nice theoretical approach but does not work all the time. I would suggest the way you are currently doing it. You read the instructions and try to solve it. Once its solved or you think you solved it, then starts the verifying process. maybe you didn't check for null or forgot a certain edge case. Thats totally fine and valid. You often do dont know what input cases you are provided. Further thinking all the time about the test cases distracts alot from the main goal atleast for me. Once you have all tests passing you go over it again and look if there is something you can improve and refactor the code. Writing code is an iterative processes. You will never write the best solution at the first try. there is often something that can be refactored or you did not think about. and thats is totally normal. Writing code is very complex, its okay to not have everything in mind before hand. When I am working on a solution I try to have the general flow in my head. During implementing it I create use functions that do not exist at the moment but i will write them later on. with that I have the flow implemented and add the details later on. That helps me to keep track where I am and what I am still missing. This is something that works well for me. everybody is different and has there own aproach. there is no best.


## Answer Breakdown {#answer-breakdown}

1.  Utilize test driven development: One writes tests first and then start developing the solution on the basis of those tests
    1.  Disadvantage: This may break the flow and can distract one from building a solution.

2.  Treating the code as an iterative process. One can always refactor the code after development has been accomplished
    1.  Missing solutions or key test cases is quite normal

3.  Common mode of working:
    1.  Approach a problem, think and define the problem scope

    2.  Create comments and functions (empty functions) as per the solution created. At this stage you can define what the input and output to that program will look like

    3.  After filling the gaps, run the program and try to debug it. Afterwards try to refactor the program as you see fit
