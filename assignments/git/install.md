---
layout: page
title: Install & Configure Git
parent: Git
grand_parent: Assignments
nav_order: 1
---

# {{ page.title }}

Git is not installed on every machine.
You can check by running the following command on your terminal;

```
$ git --version
```

This should print something like

```
git version 2.30.2
```

When Git is not installed on your system, you can find installation instructions in the official [getting started guide](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).


### Basic Git Configuration

All your Git commits will include you as *Author* or *Committer*.
The GitLab server that we are using in the course enforces that commits are authored by students through automatically checking that the email address ends in `@student.tudelft.nl`.
The same information is used for our activity tracking.

To be able to commit, you need configure Git to use your full name and your student email address.
You can configure this on a _global_ and a _per project_ level.
We advise to set it globally using the following commands on your terminal.

```
git config --global user.name “Your full name”
git config --global user.email “your-student-email-that-MUST-end-in@student.tudelft.nl”
```

A *per project* configuration omits the `--global` flag.
To check whether it worked you can run:

```
git config --global user.name
git config --global user.email
```

This should output whatever you configured using the commands above.

{: .caution}
Make sure that you use your *full name* and your *student email address* that ends with `@student.tudelft.nl` or the server will reject your push.

### Configure your line-endings

In contrast to Linux and macOS, which only use a single *line-feed* character to indicate a line-break, Windows uses two characters: *line-feed* and *carriage-return*.

It can quickly become annoying in projects that have contributors with different operating systems, when line-endings are not used consistently and constantly replaced *on edit*.
The accepted default is to only store *line-feeds* in the repository.

On Windows, Git can be configured to auto-correct the line-endings for you:

    $ git config --global core.autocrlf true # use only on Windows!

On non-Windows computers, you can set the same setting to `input`, to eliminate any *carriage-returns* that might already have been accidentally introduced into the project.

    $ git config --global core.autocrlf input # use only on macOS/Linux


