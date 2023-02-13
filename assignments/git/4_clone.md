---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

# [Link button](http://example.com/){: .btn .btn-tud }

layout: page
title: 1. Cloning
parent: Git
grand_parent: Assignments
nav_order: 4
permalink: /git-assignment/clone
---
# The `clone` operation

There are two ways to get a repository on your computer. By creating a new one locally (also called initialisation of a repository). Or, alternatively, you can download an existing repository from a platform like GitLab, GitHub, or similar (this is called “cloning” a project). In our course we use our self-hosted GitLab instance, located at [gitlab.ewi.tudelft.nl][gl-ewi]. 

As this course will provide you with a template to start working from, we will explain the case where you download an existing project to your machine. 

{: .important }
Always use TU Delft's Single Sign On (NetID login) to authenticate yourself to GitLab and do **not** change the username (your NetID) and/or your primary email address (your student email). Those are used to generate reports about your performance in our course.

{: .caution }
There is also a GitLab instance located at gitlab.tudelft.nl. These instances are not linked in any way. You should only use the instance of our faculty.

In case you have connected the (self-hosted) GitLab instance inside GitKraken then you do not need to look up the clone URL. In the GitKraken interface you'll have the option to choose one of the projects in your GitLab account and clone that. For that you should select "GitLab (Self-Managed)" rather than the "Clone with URL" option (see the part on "Cloning a repository" further down this page).

## Finding the URL of the project
To clone a project we need to have the URL of the repository. To get this we will first go to the project in the web interface of GitLab by clicking on Projects > Your projects in the top left corner in GitLab, now select your personal git assignment repository. The name of this repository contains your NetID in the name. Click on the blue “Clone” button in the top-right corner and copy the “Clone with SSH” URL (starts with `git@…`, not `https://`).

{: .recommendation }
Cloning using the https URL is also possible, but this will trigger a prompt where you have to enter a username and password. This way of authentication is likely to be deprecated in the near future, so we recommend you already get familiar with cloning over SSH.

## Cloning a repository
Now that we have the URL we need to clone the repository on our machine. This can be done in the following way;

Terminal
{: .label .label-gray }

> Navigate to the folder where you'd like to store the projects' files and run the following command;
>
>```
>git clone <URL>
>```
>
>You can paste a URL into the terminal using ⌘V (OSX), Ctrl+Insert (Windows) or Crtl+Shift+V (Linux).


GUI 
{: .label .label-green }

> Click on the "Clone a Repo" button in the main screen, select "Clone with URL" and paste the SSH URL. Select the location where you want the repository to be stored on your local machine and confirm by clicking on the button "Clone the Repo!". If SSH is not properly set up the Clone button will be greyed out or an error will appear. Go back to the [SSH step]({{ site.baseurl }}/git-assignment/install-gitkraken) to setup SSH correctly or ask help from your peers or a TA. 
>
> <a href="{{site.baseurl}}/assets/images/gitkraken/clone-repo.png" data-lightbox="gitkraken-clone-repo" data-title="Cloning a repository in GitKraken.">
>    <img src="{{site.baseurl}}/assets/images/gitkraken/clone-repo.png" />
> </a>


{: .assignment }
Clone your individual git repository to your local machine. 

## Common errors

Here you can find some of the most common errors that your peers have encountered in the past year(s).

### **You are prompted for `git@gitlab.ewi.tudelft.nl's password`**
Something in your SSH key setup is not working as expected. Please check whether your SSH agent is running (you may need to restart it manually upon reboot of your device), and that your SSH key is loaded into the agent. 

{: .important }
Do **not** enter any password. You don't have the correct password, and performing too many attempts here will get your IP banned from our GitLab server. 



[gl-ewi]: https://gitlab.ewi.tudelft.nl