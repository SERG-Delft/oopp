---
layout: page
title: Backlog
parent: Assignments
has_children: false
has_toc: false
---

# {{ page.title }}

Create a backlog that formalizes the requirements that were covered in the various *Client Q&A* sessions.
We expect that you follow the principles and practices that were introduced in the *Requirements Engineering* lecture.

### Format

We do not have requirements for the backlog layout, but we require that the backlog includes the following sections:

- *Stakeholders:* Introduce the stakeholders that you have identified as application users.
- *Terminology:* Introduce important terms of the domain
- *User Stories:* Provide a a (prioritized) list of user stories. The stories should be grouped by epic.
- *Mockups (optional):* We recommend to create mockups to illustrate the envisioned application.

In general, we recommend to keep the document simple.
You can use the official backlog of [last years project][backlog22] as a good indicator of the expected format.

[backlog23]: {%link /grading/oopp23-talio-backlog.pdf%}
[backlog22]: {%link /grading/oopp22-quizzzz-backlog.pdf%}


### User Stories

The list of user stories is the heart of your backlog.
It describes all the functionality that has been requested by your client and provides the basis for your weekly planning. 
Please note that it won't be required to implement all features later in the project, you just implement as many stories as you can.


#### Epics

Start by identifying the high-level epics that represent the features of the application.
These epics could form subsections, in which you include list of user stories.
Make sure that you include one epic for the *minimal application* that contains the user stories that are required for passing the course.

Each epic should have a description that introduces the feature and clarifies the scope of what's being implemented.
It can prove useful to complement this description with mockups to illustrate the vision.
To keep the descriptions concise, these mockups should be moved to the optional mockup section at the end of the document and they should only be refered to.

Make sure that epics and their user stories are prioritized, i.e., they can be worked on from top to bottom.
A higher-priority epic/story should not depend on items that are listed below them.


#### User Stories

Use user stories to flesh out the detailed description of the epic.
It is important that all user stories follow the required sentence structure that has been introduced in the lecture (e.g., As *role* I want *functionality* so that *reason/goal/motivation*).

User stories must have a clear focus on the user perspective.
They are supposed to describe all interactions and workflows of the different epics.
It is not necessary to create a user story for each *click* in the application, but avoid larger "gaps" of undefined application behavior.
Also, ensure that all functionality that has been initially described through the epic is actually covered in user stories.
Try to avoid contradicting requirements in your backlog and avoid overlap between user stories.


#### Acceptance Criteria

Aim for small user stories that clearly communicate their goal and implicit acceptance criteria.
When a story is covering multiple things, it might be necessary to define explicit acceptance criteria for them that help with disambiguation.
Make sure that user stories and explicit acceptance criteria are formulated in a measurable/observable way that allows to decide when a story is done/finished.


### Submission

The submission procedure is the same for the draft and the final submission:
Create a single document (e.g., PDF export or a Markdown file) for the backlog.
Commit this file to your repository and place it in `/docs/backlog.pdf`.
After the respective deadline (draft/final), your TA will check for the existence of this file and provide you with formative/summative feedback on it.

Details about the assessment of your submission are provided in the [Grading Section][grading].

[grading]: {{site.baseurl}}/grading/process/#backlog
