---
layout: page
title: Product
permalink: /grading/product
parent: Grading
nav_order: 2
---

# {{page.title}}

The following rubrics contribute to your product grade.

## Implemented Features

{: .caution }
This section still needs updating.
The final rubric for *implemented features* will be released when the deadline for the [backlog]({{site.baseurl}}/assignments/backlog/) has passed.
For now, this page contains the rubric that was used last year to give an idea of what to expect.

We have released an [example backlog for the Quizzzz application]({{site.baseurl}}/rubrics/quizzzz-backlog.pdf).
This backlog builds the basis for our grading of your quizz application.
Make sure that you adopt your own backlog so your are not missing features or spending time on unnecessary functionality.

The following table contains the categories that will be considered in the product assessment.
These categories spread out over MUST/SHOULD/COULD haves of the backlog and there is also plenty of opportunity to polish the game in the areas that we intentionally left undefined to give you some artistic freedom. 
For the grading, we will not just check boxes, we will provide a judgment of how well we think a particular category has been realized.
We will also recognize groups that we think went the extra mile beyond the requirements to reach an excellent state in these categories.

| Item | Description |
| --- | --- |
| Basic Requirements | Does the application fulfil the basic MUST requirements? |
| Prioritization | Does the implementation respect the SHOULD/COULD prioritization? |
| Question Types | How many of the different question types are supported? How well has this been done? |
| Score System   | How extensive is the score system? (Earning points, leaderboards, etc.) |
| Multiplayer    | How mature and extensive is the multiplayer support? |
| Engagement     | Is the game fast-paced and engaging as described in the Q&A? Is it motivating to play? |
| Emojis         | How convincing is the integration of the emoji feature? |
| Jokers         | Are all requested joker types supported? How well is the feature integrated into the game? |
| Usability      | Is the game nice-looking and intuitive to use? |

*Please note:*

- Do not implement features that have not been asked for, instead, polish existing features. For example, we are not going to value a "share functionality" that allows you to post results on social media, because this was never discussed.
However, we will acknowledge if you *-for example-* spend additional time to find more engaging ways to fine-tune score calculation, implement smarter ways to make the activity selection for a question more fun, or other polishing in any of these nine categories.
- If your game has a clever approach for making any of these categories more exciting, highlight these in your final product video, so we don't miss it!

## Technology

| Item | Description |
| --- | --- |
| Dependency Injection | Application uses dependency injection to connect dependent components. No use of static fields in classes. |
| Spring Boot | Application makes good use of the presented Spring built-in concepts to configure the server and maintain the lifecycle of the various server components. |
| JavaFX | Application uses JavaFX for the client and makes good use of avialable features (use of buttons/images/lists/formatting/...). The connected JavaFX controllers are used with dependency injection. |
| Communcation | Application uses communication via REST requests and Websockets. The code is leveraging the canonical Spring techniques for endpoints and websocket that have been introduced in the lectures. The client uses libraries to simplify access. |
| Data Transfer | Application defines meaningful data structures and uses Jackson to perform the de-/serialization of submitted data. |

## Testing

| Item | Description |
| --- | --- |
| Coverage | The project uses tests in all parts of the application. Testing is an integral part of the coding activities. |
| Unit testing | Classes are tested in isolation. Configurable *dependent-on-components* are passed to avoid integration tests (for example, to avoid running a database or opening REST requests in each a test run). |
| Indirection | The test suite includes tests for indirect input/output and behavior. |
| Endpoint Testing | The REST API is tested through automated unit tests. |

## Individual Adjustment

We will analyze the second peer-feedback assignment of all teams (Buddycheck) with respect to contributions to the *product* rubrics.
Should an individual stick out from their team performance, we will sightly adjust the *product* grade of this student by -0.5 to +0.5.

*Please note:* This only affects the partial grade and is not an adjustment of the overall OOPP grade.

