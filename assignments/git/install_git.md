---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

# [Link button](http://example.com/){: .btn .btn-tud }

layout: page
title: Install Git
parent: Git
grand_parent: Assignments
nav_order: 2
permalink: /assignments/git/install
---

# Install & Configure Git

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
git config --global user.email “Your student email that ends in @student.tudelft.nl”
```

A *per project* configuration omits the `--global` flag.
To check whether it worked you can run:

```
git config --global user.name
git config --global user.email
```

This should output whatever you configured using the commands above.
You should now have everything set to get started with git.

{: .caution}
Make sure that you use your *full name* and your *student email address* that ends with `@student.tudelft.nl` or the server will reject your push.

