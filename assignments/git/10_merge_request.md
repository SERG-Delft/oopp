---
layout: page
title: 7. Merge Requests
parent: Git
grand_parent: Assignments
nav_order: 10
permalink: /git-assignment/merge-request
---

# Merging your changes in the main branch
When you finish working on a feature, the changes need to be put into the shared repository. To do this, we create merge requests. This allows your peers to check and give feedback on the changes you made and spot potential bugs. 

{: .info }
Make sure you've watched the screencast on [GitLab Issues and Merge Requests]({{site.baseurl}}/lectures/git-gitlab#screencasts-gitlab) first before you continue with this part. Within the ["Collaborative SE"]({{site.baseurl}}/lectures/collaborative-se) lecture we'll discuss these features in-depth.

Creating a merge request is done in the GitLab online environment. Here you can set a variety of options. For example, you can (and should) provide a short description of the changes you want to merge. Besides that, you can request a specific person to review your merge request. You can also require a certain number of approvals before your merge request may be merged. There is also an option to mark a merge request as draft, which will make it impossible to merge it (until it is unmarked as draft).

{: .assignment }
Create a merge request for the `merge_readme` branch to the `main` branch. Once this is done, merge the merge request.

{: .caution }
It is generally considered bad practice to merge your own merge requests. Since this is an individual assignment, it's fine to do so now. However, during the project, make sure one of your peers merges your merge request (after reviewing it thoroughly).
