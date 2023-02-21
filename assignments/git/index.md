---
layout: page
title: Git
parent: Assignments
has_children: true
permalink: /assignments/git/
---

# {{ page.title }}

{: .caution}
Work on this page has not finished yet.
Expect completion in the first weeks of the course.

{: .important}
The Git assignment will change for this year.
Do not worry, when you only see an empty repository on Gitlab, the assignment instructions will be updated timely.

This set of exercises aims to help you getting started with Git. Git is the Version Control System we 
use in this course. Git is very popular, it is used by many companies industry, so knowing how to work 
with it will be an important skill to master.

Git will allow you to work on the source code of your software system collaboratively. It can be used 
for big teams, small teams, and even by individuals. 

As we use Git to gain insights into the groups’ and your individual progress it is important that you 
make sure to configure Git as explained in the first section of this manual. When you already know how 
to work with Git then you are free to skip the parts that are already known to you. Make sure to 
complete the final assignment at the end of this manual before the second lab session.

In case you have questions you can firstly ask your peers for help, furthermore you can ask on the 
Mattermost git channel or ask your TA. 

Git takes some time to get used to, it may look complex at first, but once you get familiar with the 
terminology it should be much easier to work with. Don’t hesitate to ask for help when you get stuck, 
it’s better to ask in the first weeks than halfway into the project.

Good luck!


## How to hand in your assignment?
To complete this assignment you have to complete all tasks marked in the gray "assignment" boxes on the following pages. You do not need to upload anything to Brightspace; just make sure your changes have been uploaded (pushed) to our GitLab server and then your TA will be able to check that you've completed the assignment.

## Furthermore
- Login at [GitLab](https://gitlab.ewi.tudelft.nl) through Single Sign On.
- Your account will be added to two projects in the first week of the course.
- Do not change account details such as your email address and/or username please.
  - These are used for automated checks by course staff.
  - Setting a profile picture is fine, as is filling in other profile fields.
- Ensure you are using the correct URL: e.g. https://gitlab.ewi.tudelft.nl and not something like 
  https://gitlab.tudelft.nl (which exists as well, but is not linked to EEMCS' GitLab)
- <span class="text-red-300">Never enter a password for user `git@gitlab.ewi.tudelft.nl`, there's 
  no correct password and you'll get yourself banned when you try a couple of times!</span>
- The server has a pretty tight firewall, therefore:
  - Upon failed connections, do **not** immediately retry without verifying your setup.
  - In the event that you tried too many times you'll be banned from the server automatically.
    The first two times you'll be banned automatically for _1 hour_. When you reach the banlist
    for the third (or more) time then you'll be banned permanently.
  - When you ended up in the server's banlist, you can request to be unbanned by the [EIP][eip] team.
    Send an email to `eip-ewi@tudelft.nl`, mentioning that you want to be unbanned from
    GitLab, and include your _public_ IP address (find it using [whatsmyip.org][ip] for example).

[eip]: https://eip.ewi.tudelft.nl
[ip]: https://www.whatsmyip.org


<img src="{{ page.license_image | relative_url }}" style="width: 125px;" />