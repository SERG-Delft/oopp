---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

# [Link button](http://example.com/){: .btn .btn-tud }

layout: page
title: 5. Merging
parent: Git
grand_parent: Assignments
nav_order: 8
permalink: /git-assignment/merge
---

# Combining your feature with the “live” version of the system
When you start coding, your peers can work on other features in the meantime. To see if the features work together, you can combine the features by **merging** their branches. To merge their changes into your branch, you need to do the following;

Terminal
{: .label .label-gray }

> Make sure that the to be merged branch is up to date (by using fetch and pull) then execute the following commands:
>
>```
>git checkout <branch_name>
>git merge <to_be_merged_branch>
>```

GUI 
{: .label .label-green }

> Make sure you are in the branch you want to merge another branch into. Then right-click on the commit you want to merge into your branch. Usually it is the latest commit from another branch. Then press `Merge <branch_name> into <current_branch_name>`.

> <a href="{{site.baseurl}}/assets/images/gitkraken/merging.png" data-lightbox="gitkraken-merging" data-title="Merge a branch into your branch.">
>    <img src="{{site.baseurl}}/assets/images/gitkraken/merging.png" />
> </a>


{: .assignment }
Merge the branch `readme_gettingstarted` into the `merge_readme` branch to practise merging. Push the changes after the merge is done.
