---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

# [Link button](http://example.com/){: .btn .btn-tud }

layout: page
title: 9. Workflow
parent: Git
grand_parent: Assignments
nav_order: 12
permalink: /git-assignment/workflow
---

# Full workflow for adding changes
Now that you have seen all basic functionalities of Git and GitLab, it's time to put them all together. In this final task you will perform the full workflow of finding a problem, reporting it and fixing it.

The final part of your readme should be a short reflection on this assignment. The readme should contain 2 sentences about what you learned in this assignment (What was hard? Did you already hear of certain terms before?).

{: .assignment }
Create an issue in GitLab describing the problem: a reflection is missing. Make sure the issue has a clear title and description.

The next step is to fix the problem. As you saw before, each issue should be resolved in a separate branch.

{: .assignment }
Create a new branch to work on this issue.

{: .recommendation }
You can create a branch directly from the issue on GitLab. To do so, go to the issue page. You will see a blue button "Create merge request". Clicking this will create a merge request with a draft status and a branch for this issue. If you do not want this merge request, in the dropdown menu of this same blue button you can choose the option "Create branch".
By using these options, the branch name will be prefixed with the issue number. GitLab will show that you created a branch to address the issue on the page of the issue. This way it's clear to everyone you're working on this issue. You can also get the same result by manually creating a branch that starts with the issue number, e.g. `1-add-reflection`.

Now it's time to fix the problem.

{: .assignment }
Checkout the newly created branch. Address the issue by adding your reflection. Once you are done, commit and push the changes.

Propose the fix by creating a merge request for it.

{: .assignment }
Create a merge request for the branch. Make sure the title and description are clear.
If you already created the draft merge request automatically with the branch, unmark the merge request as draft.

{: .info }
If you created the branch from GitLab, you will notice the text "Closes #1" is put in the description automatically. This links the merge request to the issue it was made for. Once the merge request is merged, the issue is closed automatically. You can also add this text to a merge request manually: "closes", "fixes" and "resolves" are keywords you can use, followed by the issue number.

Normally your peers would review your changes by leaving comments and/or suggestions on your merge request. Once that is done, one of them will merge your changes into the codebase. You will have to perform the merge yourself this time.

{: .assignment }
Merge the merge request you just created. Checkout the `main` branch and pull the latest changes.

Congratulations, you have reached the end of the Git assignment! You should now know the basics of how to work with Git and GitLab. Before you start on the project, you can read some [tips from the TAs][tips] about working on a group project.

If you are interested in more information about Git, you can read the section on [additional features][features].

[features]: {{site.baseurl}}/git-assignment/features
[tips]: {{site.baseurl}}/git-assignment/tips
