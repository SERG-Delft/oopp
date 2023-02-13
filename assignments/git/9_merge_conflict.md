---
layout: page
title: 6. Merge Conflict
parent: Git
grand_parent: Assignments
nav_order: 9
permalink: /git-assignment/merge-conflict
---

# Merge Conflict
Sometimes merging cannot be done automatically. This is caused by a merge conflict, which basically means that the two branches changed the same part of a file. Git will modify the conflicting file to have both versions. The two versions are separated by greater than (>), equals (=) and less than (<) signs. It is your task to determine what the correct version is and make sure the merge is correct.

{: .important }
Always check if merging worked out before you commit the resolved merge conflict. Make sure your code still works afterwards!

Terminal
{: .label .label-gray }

> When the merge fails the affected files will be listed in the output using the following format;
>
>```
>CONFLICT (content): Merge conflict in <file>
>```
>
>Resolve the conflicts in these files in your editor and commit the changes to finalise the merge.

GUI 
{: .label .label-green }

> <a href="{{site.baseurl}}/assets/images/gitkraken/merge-conflict.png" data-lightbox="gitkraken-merge-conflict" data-title="Merge conflict.">
>    <img src="{{site.baseurl}}/assets/images/gitkraken/merge-conflict.png" />
> </a>

> When merging the branch, you will get a popup (as seen above) stating that a merge conflict is present, which you need to resolve before continuing.

> GitKraken will show an exclamation mark next to the unstaged files. When you click on these files, you will be able to stage all the lines that should be present in the merge commit. To have more freedom, use your own editor to resolve the conflicts. Then stage and commit the changes to finalise the merge.

> <a href="{{site.baseurl}}/assets/images/gitkraken/resolve-merge-conflict.png" data-lightbox="gitkraken-resolve-merge-conflict" data-title="Resolve merge conflict.">
>    <img src="{{site.baseurl}}/assets/images/gitkraken/resolve-merge-conflict.png" />
> </a>
 

{: .assignment }
Merge the branch `readme_install` into the `merge_readme` branch and resolve the conflicts. Try to have the different instructions in a logical order. Make sure to commit and push the changes you made.
