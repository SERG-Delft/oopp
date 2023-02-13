---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

# [Link button](http://example.com/){: .btn .btn-tud }

layout: page
title: Additional Git features
parent: Git
grand_parent: Assignments
nav_order: 13
permalink: /git-assignment/features
---

# Additional Git features

On this page we will discuss some more advanced features of Git you could read about if you want to learn more about Git.

{: .info }
The intention of this page is not to teach you all these advanced features, but rather to make you aware they exist. As such, not all features have instructions on how to perform them. Feel free to look them up if you want to know more about these options.

## Stashing

Sometimes you made changes that you want to save, but not commit. This can be done with stashing. This will save the changes that you made locally, but does not apply it to the history of the project, it is only on your computer. Additionally, it automatically restores your branch to the last committed version on your machine.

The most useful use case for stashing is the following scenario: 
- You are working on a feature, but you notice a bug in another part of the code.
- You stash your changes and start fixing the bug on a new branch.
- You commit the changes and make a merge request for the bug. 
- You go back to your own branch start working with the assumption of the working code.
- You apply the stash to get your changes back and continue working.

Terminal
{: .label .label-gray }

> For the terminal you can stash your changes by using the command; 
>
>```
>git stash
>```
>
>Afterwards you can use two commands to see and apply the changes to your code again; 
>
>```
>git stash list 
>git stash apply 
>```
>
>You can apply specific stashes by using the reflog syntax, which is the name it states before the stash when viewing the stash list, `stash@{0}` is for example the latest stash.

GUI 
{: .label .label-green }

> When you have uncommited changes, you press the stash button in the top menu. Give the stash a meaningful message to make sure you know what it does and press OK. 
>
> The stashes can now be viewed in the stash tab in the menu on the left side. Applying the changes again can be done by left-clicking on the stash you want to reapply and press “apply stash”.

## Tagging

Tags are marked versions of your program which can be downloaded easily from the repository. It is possible to make tags using Git, but you are also able to make tags in GitLab which is perfectly fine as well. The tags are essentially small releases you make of the project (for example a version number can be a nice use case for a tag).

## Cherry-picking

Sometimes it may occur that you run into a bug that someone fixed in a commit on a different branch. This is where cherry-picking comes in. With cherry-picking you are able to apply the changes of a specific commit to your own branch.

## Rebasing

Rebasing is another way of merging two sets of changes together. Instead of combining them and putting it into a merge commit, rebase reapplies the changes made on top of another branch. For example, if you are in branch A, which branched off of `main`, and `main` gets updated with new changes, you can rebase `A` onto the latest commit of `main`. All changes of the branch are applied starting from a new commit. The resulting code is the same as if you had merged `main` into your branch, but now there is no such merge commit.

Rebasing rewrites the history of the project by creating new commits for each commit in the branch to rebase. It allows for a cleaner project history and can make the history easier to understand. It does come with some risks:
1. The collaboration workflow can become distorted, because you rewrite history.
2. You cannot elaborate on why you had to perform this merge (which you could have indicated in the merge commit otherwise).

Rebasing can be done interactively usually to clean up any messy history. Here you can reorder, combine or plainly delete commits that were created. Interactive rebasing leaves room for errors, as this process is irreversible and distorts the workflow that resembles the actual product.

We do not allow rebasing during the OOP Project to make sure that we have an accurate representation of the work you and your group provided. You are allowed to do it on local branches that are not public/pushed to the remote. You can change your local history, but not the published history. If you want to try rebasing, you can do this in your repository for the Git assignment.

{: .info }
People tend to have different preferences when it comes to merging vs. rebasing. We do not claim that one is better than the other. For your own projects you should pick whichever you like best.

## Automatic rebase

Automatic rebasing is a tool to avoid merge commits in the same branch. When more than one person is working on a branch and another person pushes their commits before you pushed yours, the created changes have to be merged with your changes. The “default” solution uses a merge commit: the new version of the remote branch is merged into your local branch. These merge commits can clutter the Git history and leave the history less clear than before.

An alternative solution is to rebase your commits. This will pull the new commits from the remote and rebase your commits on top of them. This can be done automatically by enabling automatic rebasing. Since your commits are not pushed yet, it will not cause a problem for your peers. However, as you might have changed the same code as your peers, it is possible that conflicts occur. You can resolve these in a way similar to resolving merge conflicts. Always make sure to check the code still works after rebasing.

## Auto stashing

Automatic rebasing is used to rebase your unpushed commits onto new commits on the remote branch, but what if you didn’t commit your changes yet? You can stash your changes, pull the new commits and apply your stashed changes afterwards. This process can be automated by enabling automatic stashing.

## Force pushing

When you are changing the history of a branch that is already online, Git will prevent you push this branch because it conflicts with the existing branch on the repository. When you are sure that the branch you have is the correct one, you are able to force push a branch. This tells Git that you know it conflicts, but you are absolutely sure of what you are doing and the remote branch should be overwritten. During the OOP Project, force pushing is not allowed on the group project repositories. You are free to try this out on your repo for the Git assignment.

{: .caution }
By force pushing you can irreversibly delete code from your repository. Any changes made remotely between the time you last pulled and your forced push will be overwritten. A slightly safer version of forcing a push is using force with lease: this will be rejected in case newer commits were pushed to the remote branch.
