---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

# [Link button](http://example.com/){: .btn .btn-tud }

layout: page
title: 8. Pulling
parent: Git
grand_parent: Assignments
nav_order: 11
permalink: /git-assignment/pull
---

# Synchronise changes from the remote in your local repository
When new changes are pushed into the remote repository, the changes are not automatically put onto your computer. To obtain the latest version of the files, you should pull the branch from the remote.

{: .caution }
Make sure you have no uncommitted/unstashed changes when pulling.

Assuming you are on the branch you want to update, pulling can be done in the following way;

Terminal
{: .label .label-gray }

> Type the following command;
>
>```
>git pull
>```

GUI 
{: .label .label-green }

> <a href="{{site.baseurl}}/assets/images/gitkraken/pulling.png" data-lightbox="gitkraken-pulling" data-title="Pulling.">
>    <img src="{{site.baseurl}}/assets/images/gitkraken/pulling.png" />
> </a>

> Click on the pull button at the top. 

{: .important }
When someone pushed changes onto your branch and you did too, Git will merge the changes that happened. This merge will result in a merge commit where, just like with merging, [merge conflicts](merge-conflict) can occur.

{: .assignment }
Switch back to the `main` branch and see what the current status is of the `main` branch. After this, use pull to get the new changes. What changed?

[merge-conflict]: {{site.baseurl}}/git-assignment/merge-request
