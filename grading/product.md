---
layout: page
title: Product
parent: Grading
nav_order: 2
---

# {{page.title}}

The following rubrics contribute to your product grade.

## Implemented Features

[/]: comment out next year
[/]:{: .caution }
[/]:This section still needs updating.
[/]:The final rubric for *implemented features* will be released when the deadline for the [backlog]({%link assignments/backlog.md%}) has passed.
[/]:For now, this page contains the rubric that was used last year to give an idea of what to expect.

We have released an [example backlog for the Talio application][backlog23], which builds the basis for our grading of your application.
Make sure that you are not missing out on a requested feature or spending time on unnecessary functionality.


[backlog23]: {%link /grading/oopp23-talio-backlog.pdf%}
[backlog22]: {%link /grading/oopp22-quizzzz-backlog.pdf%}


The following table contains the categories that will be considered in the product assessment.
These categories cover the different epics that we have discussed in the client Q&A sessions.
All of them leave plenty of opportunity to polish the application in the areas that are left undefined to give you some artistic freedom. 
For the grading, we will not just check boxes, we will provide a judgment of how well we think a particular epic has been realized.
We will also recognize groups that we think went the extra mile beyond the requirements to bring an epic to an excellent state.


| Item | Description |
| --- | --- |
| Basic Requirements | Does the application fulfill the basic requirements? (pass/fail) |
| Prioritization | Does the implementation follow the given epic prioritization? We won't fail teams for not respecting prioritization, but it will have a negative influence on the grade. (pass/fail) |
| Epics | For each of the six requested epics (Multi-board, Card Details, Tags, Customization, Keyboard Shortcuts, Password Protection), we will judge how well the respective feature has been implemented. We will consider the functionality, the ease of use, the look of the UI, and overall how mature the feature appears to us. (6x Insufficient to Excellent) |

*Please note:*

- Do not implement features that have not been asked for, instead, polish existing features. For example, we are not going to value a "share functionality" that allows you to post results on social media, because this was never discussed.
However, we will acknowledge if you *-for example-* spend additional time with fine-tuning a given epic, like finding better workflows for the users, making the UI easier to use, or other polishing in any of the provided categories.
- If your application is using a clever approach in any of these categories, highlight this in your final product video, so we don't miss it!

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
Should an individual stand out from their team performance, we will sightly adjust the *product* grade of this student by -0.5 to +0.5.

*Please note:* This only affects the partial grade and is not an adjustment of the overall OOPP grade.

