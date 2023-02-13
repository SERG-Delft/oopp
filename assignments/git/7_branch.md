---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

# [Link button](http://example.com/){: .btn .btn-tud }

layout: page
title: 4. Branches
parent: Git
grand_parent: Assignments
nav_order: 7
permalink: /git-assignment/branch
---

# Working together
So far we have only worked in the “main" branch (previously this was commonly referred to as the "master" branch). This branch is meant for a stable version of your project and not meant for ongoing development. So far it worked out because you are the only person working in this repository, but imagine when all your team members also make changes on the same code. You would not be able to see easily what is finished and what is still in progress, plus there might be a broken product on "main". So from now on: **never push to main**. Instead, you should create branches to work in isolation on the new features and functionalities. The branch should have a name which is descriptive about its purpose.

## Creating a branch

First, a branch must be created.

Terminal
{: .label .label-gray }

> Use the following command to make a new branch:
>
>```
>git checkout -b <branch_name>
>```
>
>When you want to push a new branch, which you will do in the next assignment, you need to push in the following way;  
>
>```
>git push -u origin <branch_name>  
>```

GUI 
{: .label .label-green }

> Click on the branch button in the top menu.
> <a href="{{site.baseurl}}/assets/images/gitkraken/branch.png" data-lightbox="gitkraken-branch" data-title="Create a new branch.">
>    <img src="{{site.baseurl}}/assets/images/gitkraken/branch.png" />
> </a>

> Enter the name you decided on for the branch and press `Enter`. 
> <a href="{{site.baseurl}}/assets/images/gitkraken/name-branch.png" data-lightbox="gitkraken-name-branch" data-title="Name your branch.">
>    <img src="{{site.baseurl}}/assets/images/gitkraken/name-branch.png" />
> </a>


{: .info }
Branches are created from the currently checked out commit. Typically you create a new branch from the most recent working version of your product. Sometimes you may want to try a different approach to a problem, then you can go back a few commits and branch from there.

{: .assignment }
For this assignment you are going to create a new branch for adding the required tools for this assignment to the README file. For example, you need Git and SSH to complete this assignment. Decide on a descriptive name and create the branch. Add the requirements and make sure to push the branch to the remote repository. (You may run into an error `The current branch new_branch has no upstream branch.`, the error should already include instructions on how to resolve this).

## Switching to another branch

When you made changes on a branch, you sometimes need to change branches to look at something from someone else (for example when reviewing code). To change branches, you need to do the following;

Terminal
{: .label .label-gray }

> Make sure that all the updates are visible on your machine by fetching; 
>
>```
>git fetch --all 
>```
>
>Now you can view and switch branches by using the following commands; 
>
> ```
>git branch -a 
>git checkout <branch_name>
>```

GUI 
{: .label .label-green }

> First you need to make sure that all the updates are visible for your machine. To do this we need to fetch the changes. Click on the fetch button in the top menu to fetch all the updates/branches.
> <a href="{{site.baseurl}}/assets/images/gitkraken/fetch-all.png" data-lightbox="gitkraken-fetch-all" data-title="Fetch the changes.">
>    <img src="{{site.baseurl}}/assets/images/gitkraken/fetch-all.png" />
> </a>

> Then go to the remotes in the left menu and open origin. Here you see all the branches that exist in the remote repository (“origin”). To switch to a branch simply double click on any branch you want to go to. If a branch is already on your machine, you can also double click on it in the branches tab of the left menu.
> <a href="{{site.baseurl}}/assets/images/gitkraken/switch-branch.png" data-lightbox="gitkraken-switch-branch" data-title="Switch to another branch.">
>    <img src="{{site.baseurl}}/assets/images/gitkraken/switch-branch.png" />
> </a>



{: .caution }
Switching branches is possible when you have no uncommitted changes. Make sure that all changes are either stashed (see “Additional terminology”) or committed before changing branches.

{: .assignment }
Switch to the remote branch called `merge_readme`.
