---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

# [Link button](http://example.com/){: .btn .btn-tud }

layout: page
title: 3. Pushing
parent: Git
grand_parent: Assignments
nav_order: 6
permalink: /git-assignment/push
---

# Synchronise your commits to GitLab
To allow for everyone to use and see your changes, you need to upload the changes to GitLab. Uploading the changes is done by **pushing** the commits containing your changes. After pushing, you cannot undo the changes anymore. When you made a mistake, you need to make new changes, commit them and push that commit again to change it.

Before you push your on commits you should ensure that your local repository is up to date by **pulling** all changes that others may have pushed meanwhile. This will be explained in the next sections.

Terminal
{: .label .label-gray }

> For pushing, use the command:
>
>```
>git push
>```
>
>When you want to push a new branch, which you will do in the next assignment, you need to push in the following way;  
>
>```
>git push -u origin <branch_name>
>```

GUI 
{: .label .label-green }

> <a href="{{site.baseurl}}/assets/images/gitkraken/pushing.png" data-lightbox="gitkraken-pushing" data-title="Pushing.">
>    <img src="{{site.baseurl}}/assets/images/gitkraken/pushing.png" />
> </a>

> For pushing the only step needed is to press the push button in the top menu.

{: .assignment }
Push the changes you have made so far.


