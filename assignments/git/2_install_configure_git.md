---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

# [Link button](http://example.com/){: .btn .btn-tud }

layout: page
title: Install & Configure Git
parent: Git
grand_parent: Assignments
nav_order: 2
permalink: /assignments/git/install-git
---

# Install & Configure Git

When Git is not installed on your system yet then you can follow the steps from [Git’s website](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) to install it. You can check whether Git is installed by running the following command on your terminal;

```
$ git --version
```

This should print something like

```
git version 2.30.2
```

There are multiple ways to use Git. For instance, you can use your terminal (entering raw commands), you can use a GUI (in case you prefer pushing buttons instead of typing commands) or your editor (e.g., IntelliJ, Eclipse, etc.) may include Git support.

In this manual we will focus on the GUI, for the examples we will use GitKraken (on Windows), but you can use any other GUI and/or OS that you like. We will always mention the equivalent terminal commands in case you prefer to work with the terminal. The most important thing is to get familiar with the terms, and how to perform the basic operations in Git.

{: .caution }
We **strongly** encourage you to [setup SSH authentication](ssh-keys), as repeated authentication error will get your IP banned.


## Configuring Git on your system

Submitting your code on GitLab has been restricted to only accept code that is authored by students. The platform will automatically check whether the email address ends with “@student.tudelft.nl”. 

Therefore, you need to instruct Git what name and email address to associate with your work. You can configure this on a _global_ and a _per project_ level. We advise to set it globally. To do so do the following;

Terminal
{: .label .label-gray }

>Run the following commands;
>
>```
>git config --global user.name “Your full name”
>git config --global user.email “Your student email”
>```
>
>To check whether it worked you can run;
>
>```
>git config --global user.name
>git config --global user.email
>```
>
>This should output whatever you configured using the commands above. Make sure that the configured email address ends with **@student.tudelft.nl**!

GUI 
{: .label .label-green }

> <a href="{{site.baseurl}}/assets/images/gitkraken/configure-git.png" data-lightbox="gitkraken-configure-git" data-title="Configure Git on your system.">
>    <img src="{{site.baseurl}}/assets/images/gitkraken/configure-git.png" />
> </a>

You should now have everything set to get started with git.
