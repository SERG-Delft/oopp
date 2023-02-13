---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

# [Link button](http://example.com/){: .btn .btn-tud }

layout: page
title: Tips
parent: Git
grand_parent: Assignments
nav_order: 14
permalink: /git-assignment/tips
---

# Do's and Don't from TAs

In this section you’ll find various tips from the TAs. Typically these are things the TAs bumped into themselves when doing projects within the CSE programme.

## Line endings

Different operating systems use different symbols to denote the end of a line. It can happen that your system uses a different symbol than the system of your group member. To prevent many commits that change all line-endings back and forth, [let Git handle the line-endings for you](https://docs.github.com/en/get-started/getting-started-with-git/configuring-git-to-handle-line-endings).

All that is necessary to do is to set the `core.autocrlf` setting in your Git config. The correct value depends on your operating system, on Windows, it should be set to `true`, while on all other operating systems, the recommended setting is `input`. The setting can be set very conveniently from the command line (`$`) with one single command:

    # Windows
    $ git config --global core.autocrlf true
    # Mac OS/Linux/...
    $ git config --global core.autocrlf input

## One branch == One (isolated!) feature

Within a single branch you should work on a single, isolated feature. This keeps the resulting merge requests small and therefore easier to review. Furthermore, you reduce the risk of merge conflicts. When two team members work on big parts of the system in parallel you have a bigger chance that some chances overlap.

## Run CheckStyle locally before pushing

Typically using Checkstyle causes more commits.
In a normal workflow, you commit your work, you push it, and then GitLab runs checks.
Should then Checkstyle find any issues with your code, you have to fix them, and commit/push again.
This causes your git history to have needless commits.
The better approach is to run the analysis tools locally. Install the Checkstyle plugin in your editor and it will report problems even before you push your changes. This can be both a timesaver and a way to keep your git history clean.
