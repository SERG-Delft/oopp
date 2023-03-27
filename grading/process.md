---
layout: page
title: Process
parent: Grading
---

# {{page.title}}

The following rubrics contribute to the process grade.

## Backlog

| Item | Description |
| --- | --- |
| Structure | The backlog follows the expected document structure, contains a good level of detail, and is written in a clear fashion. |
| Epics | The different application features have been identified and proritized. Epics are properly introduced to clarify the features and their scopes. |
| User Stories | User stories have consistent format and convey the who/what/why. They focus on the user perspective and cover all requested features. |

The assessment of the user stories is based on the following detailed criteria:

- *Format:* The user stories follow the required format (i.e., As *role*, I want to *requirement*,  so I can *reason*)
- *User focus:* User stories have a clear focus on the user perspective.
- *Scope:* Stories describe one particular interaction/workflow and have little to no overlap.
- *Completeness:* All epics are covered with a good amount of user stories and the required interactions are covered. There are no obvious "gaps", for which it is not clear what the application should do. The epic description and its mockups are fully covered.
- *Coherence:* The backlog does not contain contradicting requirements and the user stories do not overlap.
- *Acceptance Criteria:* User stories are small and acceptance criteria implicit. Only overloaded user stories have concrete acceptance criteria. Effects are measurable/observable, which allows to decide when a story is done/finished.


## Tasks and Planning

#### Task Identification

| Item | Description |
| --- | --- |
| Actionability | User stories are broken down into multiple concrete, technical tasks. These tasks are either modelled as GitLab issues (recommended) or they have been added as nested lists to GitLab issues. Tasks are introduced with a short description (background/context/clarifications/...). |
| Traceability | It is clear how technical tasks relate to user stories. Tags are used to make it easy to understand the source or nature of the various tasks (e.g., backlog, bug, extension, ...) |
| Granularity | Tasks are reasonably sized, so developers can get them done in an average work session. The project history shows that team members get multiple tasks done every week. |
| Expectations | Most tasks have a short description of the actions that need to be performed and the expected outcomes/explicit acceptance criteria. |

#### Planning & Time Management

| Item | Description |
| --- | --- |
| Effort Estimation | Efforts of all tasks have an estimate, which is kept up-to-date in every sprint planning. |
| Assignment Tracking | Tasks get assigned to developers and their effort spent is tracked. |
| Roadmap | Efforts and estimates are taken into consideration in the planning. The overall plan is regularly updated. |

#### Task Distribution

| Item | Description |
| --- | --- |
| Dedication | All developers contribute about the same amount of effort to the project. Time spent is discussed in the weekly meetings. The team takes active counter measures to keep deviations reasonable. |
| Feature Isolation | Developers use feature branches to isolate their work from others while it is under development. The latest changes on main are integrated into the feature branch before opening a merge request (e.g., "merge main into feature" or "rebase feature onto main"). |
| Areas of Expertise | All developers constantly contribute to all system parts. Tasks a not distributed by area, but by feature, which usually results in cross-cutting changes. |


 
## Teamwork

In contrast to the [individual pass/fail criteria that are listed in the grading overview]({{site.baseurl}}/grading/#passfail-criteria), the teamwork module presents a pass/fail element for the whole group.
To pass this aspect of the course, the team needs to continuously execute the [teamwork assignments]({{site.baseurl}}/assignments/teamwork).

The team will receive formative feedback on these assignments from a TA.
It is required to reach at least a *Sufficient* rating in the end.
Should a team receive an *Insufficient* rating in their weekly rubrics, it is required that the team shows willingness and initiative for improvement.

The summative assessment of this part is based on a self-reflection of *each student*:

| Item | Description |
| --- | --- |
| Format | Follows the formatting guidelines (ACM format, length). |
| Structure | Assignment refers to three distinct situations and *strictly* follows the template. |
| Depth | All picked examples are suited for the reflection. The reflections are balanced and have a good depth in all parts. |
| Reflection on Existing Knowledge | All reflections discuss existing knowledge, questions, or assumptions. The reflections contain an articulation of new understandings that results from the experiences. |
| Connection to Academic Concepts | All reflections draw connections between the experience and the concepts/theories that have been discussed in class. It is decribed how the theory was applied in practice. |
| Evidence of Development | All reflections articulate a personal development. They elaborate on the transformation of a personal perspective or on a new insight that will affect future team work. |



## Code Contribution and Code Reviews

| Item | Description |
| --- | --- |
| Focused commits | Commits only affect a small number of files and aggregate a coherent change to the system. Commit messages clearly summarize the change.|
| Isolation | The group has used feature branches or merge requests to isolate individual features during development. |
| Reviewability | Merge requests are easy to review. For example: they contain a low number of formatting changes; they limit the number of commits; the branch was recently created and des not deviate too much from `main`; changes are coherent and relate to each other; ... |
| Code reviews | Reviews are timely, constructive, and lead to iterative improvements. |
| Build Server | Build Server was important part of the development process. Team has committed frequently. Failing builds were fixed directly. Team has selected Checkstyle rules. |



## Individual Adjustment

We will analyze the second peer-feedback assignment of all teams (Buddycheck) with respect to contributions to the *process* rubrics.
Should an individual stick out from their team performance, we will sightly adjust the *process* grade of this student by -0.5 to +0.5.

*Please note:* This only affects the partial grade and is not an adjustment of the overall OOPP grade.

