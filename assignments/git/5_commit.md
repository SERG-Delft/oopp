---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

# [Link button](http://example.com/){: .btn .btn-tud }

layout: page
title: 2. Committing
parent: Git
grand_parent: Assignments
nav_order: 5
permalink: /git-assignment/commit
---

# Sharing changes on git

Now that the setup is complete it is finally time to work with Git. As stated before, git is a tool for version control and collaboration. Git works by storing the changes that have been made to your files. In the practice repository you will be able to find a document called README.md. We are going to work with this document to practise.

{: .assignment }
First open the `README.md` document in your preferred editor (a plain text editor or IDE). Read the document and add yourself to the contributors of the project. Once you’re done, save the changes and go back to the GUI or the terminal to store the changes you made.

## Staging
Saving changes on git is done in two steps, the first step is to select which changes need to be stored. This is called **staging**. Afterwards we actually store the changes by **committing**.

Terminal
{: .label .label-gray }

> To see which files are staged run the command; 
>
>```
>git status
>```
>
>The red files are not staged, the green files are staged. To see the changes of the files you can run the commands; 
>
>```
>git diff [file]
>git diff --staged [file]  
>```
>
>To stage or unstage changes you can respectively use the commands;
>
>```
>git add <file>
>git restore --staged <file>
>```
>
>for partial commits you can add the -p flag to the add command. 

GUI 
{: .label .label-green }

> <a href="{{site.baseurl}}/assets/images/gitkraken/commit.png" data-lightbox="gitkraken-commit" data-title="Staging and committing in GitKraken.">
>    <img src="{{site.baseurl}}/assets/images/gitkraken/commit.png" />
> </a>
> In GitKraken you can now see that there are uncommitted changes. In corner on the right (near the top) you see all the files that changed and have not been committed yet, you can select the files which you want to stage and then click "Stage file" (or "Stage all changes"). After this they will move to the staged files section. You can also make a partial commit by staging selected lines from the diff window (comparing old and new situation) which you can see after you have selected a file in the right sidebar. 
To unstage, select the files you want to unstage and press "Unstage file". 

{: .assignment }
Stage the changes you made in the `README.md` file.

## Committing
The second step of storing changes is called **committing**. This step can be seen as boxing all the changes that you have made and labelling them with a message which is called the commit message. This message is to make sure that you, your team members and the TAs know what the changes are without having to go through all the files. You have learned about the conventions for commit messages during the git lecture. To refresh you memory you can look at this [guide][good-commit-messages]. 

Terminal
{: .label .label-gray }

> To commit the changes in the terminal you need to enter the command;
>
>```
>git commit -m “your commit message”
>```
>
>You can also add your commit message in an editor by removing the -m and the commit message.
>
>{: .info }
>The default editor on many systems is  vim (which is a very useful tool to learn). If you enter it by accident, use the following key sequence (one by one) to exit: `[escape][:][w][q]` (to store changes and quit vim). To exit without storing your changes you can use `[escape][:][q][!]`. You can find a tutorial on vim [here][vim-tutorial] if you want to get started with it.

GUI 
{: .label .label-green }

> <a href="{{site.baseurl}}/assets/images/gitkraken/commiting.png" data-lightbox="gitkraken-commiting" data-title="Staged file with commit Summary and Description.">
>    <img src="{{site.baseurl}}/assets/images/gitkraken/commiting.png" />
> </a>

> To commit the staged changes you first need to enter your commit message in the "Subject" and "Description" fields in the lower right corner. The subject is the most imoprtant part. This is what is primarily visible to your teammembers. The description can be used to further explain/summarise your changes (the description is hidden by default in most interfaces).  

{: .recommendation }
Commit cohesive sets of changes, and give the changes a clear description. You can find more best practices in [this online article by Tower][tower-git-best-practices].

{: .assignment }
Commit the changes you staged in the previous assignment.

## How to revert a set of changes
Sometimes you committed something incorrectly, for example when you forgot to check if the code actually compiled. All the commits that are not online yet can be reverted without too many problems.

Terminal
{: .label .label-gray }

> To reset the branch to the last commit you can use the following command; 
>
>```
>git reset [--soft | --mixed | --hard] HEAD~1
>```
>
>See the paragraph on the left on the three ways of resetting.
Without specifying the reset option it will default to a mixed reset. The number behind HEAD~ is how many commits you want to go back. To see the log of the commits and check where you want to go to when you made multiple commits use the command;

>```
>git log
>```

GUI 
{: .label .label-green }
> <a href="{{site.baseurl}}/assets/images/gitkraken/soft-reset.png" data-lightbox="gitkraken-soft-reset" data-title="Soft reset.">
>    <img src="{{site.baseurl}}/assets/images/gitkraken/soft-reset.png" />
> </a>

> In the commit graph right-click on the commit you want to revert to (not the commit you want to remove). Right click on the commit and click "Reset [branch name] to this commit". In the sub-menu select ‘soft’ to keep the changes you made, ‘mixed’ for keeping the changes but unstaging the files or ‘hard’ to remove the changes.

{: .assignment }
To try it out, make some changes in the `README.md` document that you do not want to share and commit them. Then revert the changes.

{: .recommendation }
Try out all the different options for resetting you branch to see what the effect is. We recommend soft reset as it keeps your changes. Mind that these changes remain staged!

[good-commit-messages]: https://www.freecodecamp.org/news/writing-good-commit-messages-a-practical-guide/
[vim-tutorial]: https://www.openvim.com/
[tower-git-best-practices]: https://www.git-tower.com/learn/git/ebook/en/command-line/appendix/best-practices