 ---
author: Kaushal Bundel
date: 2023-08-15T21:29:45+05:30
draft: false
title: User Story
description: Reference Guide for Writing User Story
categories: ["Product management"]
tags: ["Business Analysis"]
---
# What is a user story?

It is a high level description of a user requirement written from the end user's perspective. In simpler terms the user story is a means the communicate to the developer what needs to be built

# How are user stories derived?

User stories are derived from EPIC and user persona

**EPIC**: It is a big chunk of work that has one common objective.It could be a feature, customer request or a business requirement. An epic usually takes more than a sprint to complete

**User Persona**: A user persona is a fictional representation of the ideal user. A persona is based on user research and it incorporates the needs, goals and observed behavioral patters of the target audience.

# What are the components of a good user story?

A good user story should have two main components.

1. User story equation:

As a {User-Persona}, I want to {Some feature}, so that {Reason of using the feature}.

It should be:
- short
- simple
- describes only one piece of functionality. If needed, break it down to two or more user stories

2. Acceptance Criteria:

This lists the activities that needs to be performed to provide value to the user.  This helps a team to understand the value of the story and to set expectations as to when a team should consider something done, 
It should include:
- end to end user flow
- what feature intends to do
- functional and non-functional user cases
- impact of user story to other features
- negative scenarios of the functionality
- performance concerns and guidelines
- UX concerns

3. Assumptions:

It includes the assumptions taken by the person creating the story. The assumptions may be discussion points as captured during the discovery process or list of points helpful during the development phase

4. User Persona

The User Persona's within the scope of the User story as mentioned.

# How to know if a user story is ready?

A complete user story should be clear, feasible and testable 

*Clear*: It includes what is needed by the user

*Feasible*: It should not be too big and can fit in a sprint

*Testable*: A confirmation can be provided post story completion about the correctness of the user story

## Example of an User story

Epic: Online Pricing and Offers 

User Story: As a car buyer I would like to see the latest price and offers so that I can make a decision to buy a car.

Acceptance Criteria:

- Latest car price is to be shown
- Offer is to be shown in terms of % Saving (10% off)
- % Saving should be shown in bold and vibrant colors
- In case of no offer, the car listing should not be visible
- Car listing widget should be placed at a prominent location (Like model profile page)
- The model name should be made clickable so that a user can be guided to the detail discount page
- Offers to be shown on the basis of city which is already selected by user. In case of "no city" selection, default city (New Delhi) discounts to be shown
- If the user has allowed location access, then the prices/discounts for that location should be visible by default 

Assumptions:

- Latest Car price should be made available by the Dealer relations team
- Only offers worth 1 % of car prices should be shown

User Persona:

- Car Buyer

## Additional Pointers

- User stories should not be written based on beliefs and ideas, but should be based on **data and evidence**
- User stories should be written collaboratively usually when the user story is being groomed
- A user story should not be confused with a task. A task represents "how", a user story represents "why"
