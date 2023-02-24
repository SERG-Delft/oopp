---
layout: page
title: Instructions
parent: Git
grand_parent: Assignments
nav_order: 3
permalink: /assignments/git/instructions
---

# {{ page.title }}

{: .caution}
Work on this page has not finished yet.
Expect completion in the first weeks of the course.

This assignment follows the introductory [Tools][tools] lecture, please make sure that you have watched the lecture before starting this assignment, so you are familiar with the terminology.

The goal of this assignment is two-fold:

1. You will learn how a basic Spring Boot application is setup.
This will allow you to recognize all the modifications that have already been introduced in the OOPP template project of your team.
2. You will learn about the basic Git commands and exercise day-to-day Git usage.



[tools]: {{site.baseurl}}/material/

### Syntax

To make it easier to mix terminal input and output in one code snippet, the following instructions will use the `$` char to indicate the command line.
Take the following snippet as an example.

    $ echo "Hello World!"
    Hello World!

You can read this as *execute the command `echo "Hello World!"` on the commandline*, which should result in the output *Hello World!*

Sometimes, it is easier to explain commands inline, we use a comment symbol (`#`) for that.
Take the following snippet as an example.

    $ ls /etc/ # will show you the content of /etc/

Read this as *execute `ls /etc/`*, everything after the `#` is an illustrative comment.

Git uses SHA1 hashes like `9963ad2601f37e353aec0d1b01f23374ea2e2c8e` to refer to unique commit ids.
As long as a hash stays unambigous, it is possible to abbreviate these hashes.
For example, the previous hash can be referred to through the abbreviated hash `9963ad` or through any other substring that starts from the beginning.
These shortened abbreviations are used in many Git tools and throughout this assignment, to make the descriptions more concise.

### Getting Started

In this assignment, you will work with your private OOPP Git repository (i.e., `CSE1105`  » `<currentyear>`» `Students` » `oopp-<yournetid>`).
When you open your repository on GitLab, you will see that it is still empty.
You already know how to `clone` an existing repository from the lecture, so we will follow the other direction and start by initializing a local repository.

#### Initialization

Change your current directory to where you want to store the repository, create a directory, and initialize the Git repository in it (`~` represents your *home directory* under most operating systems).

    $ cd ~
    $ mkdir oopp-<netid>
    $ cd oopp-<netid>
    $ git init

If you have not set your name or email address globally yet or prefer to configure the information on a per-project basis, you can do that now.

    $ git config user.name "Your Full Name"
	$ git config user.email "your-student-email-that-MUST-end-in@student.tudelft.nl"

At this point, you have a fully working local repository that you can use for versioning files in the `oopp-<netid>` directory.

The first content of your new repository will be a `README.md` file.
Create the file and add some arbitray contents to it with a text editor of your choice or just do it from the commandline:

    $ echo "Hello World!" > README.md

This has changed the contents of your working directory.
You can check the status of your working directory with `git status`:

    $ git status
    On branch main
    No commits yet
    Untracked files:
        (use "git add <file>..." to include in what will be committed)
            README.md

This means that Git sees the change, but does not consider it, as the file is not tracked.
Start tracking the file by adding it to the index, either by invoking `git add README.md` (to add this one file) or by adding *all* changes and untracked files by invoking `git add -A`.
You can investigate the effect of this command by running `git status` again:

    $ git status
    On branch main
    No commits yet
    Changes to be committed:
        (use "git rm --cached <file>..." to unstage)
            new file:   README.md

TODO: Describe effect, add `reset/checkout/..?` example

The index contains all changes that will be included in the next commit.
We are ready for now, so let's commit the current changes.

    $ git commit -m "Initial commit with a README.md"
    [main (root-commit) 9963ad2] Initial commit with a README.md
     1 file changed, 1 insertion(+)
     create mode 100644 README.md

Try executing `git status` once more and you will see that the working directory is now *clean* again, i.e., there are no uncommited changes left.
To see your commit, you can run `git log`:

    $ git log
    commit 9963ad2601f37e353aec0d1b01f23374ea2e2c8e (HEAD -> main)
    Author: Sebastian Proksch <development@mail.proks.ch>
    Date:   Fri Feb 24 15:28:42 2023 +0100
        Initial commit with a README.md

#### Remotes

At this point, your commit only exists in your local repository.
If you refresh the website of your private repository on GitLab, it will still show an empty repository.
In order to synchronize your local repository with GitLab, you need to register GitLab as a *remote*.

    $ git remote add origin git@gitlab.ewi.tudelft.nl:cse1105/<year>/students/oopp-<netid>.git

You can find the concrete URL that you need to use here when to press the `Clone` button in your repository overview.
In this case, we gave the remote the name *origin*.

You can now push your changes to the remote:

    $ git push -u origin main
    Enumerating objects: 3, done.
    Counting objects: 100% (3/3), done.
    Writing objects: 100% (3/3), 251 bytes | 251.00 KiB/s, done.
    Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
    To gitlab.ewi.tudelft.nl:cse1105/<year>/students/oopp-<netid>.git
     * [new branch]      main -> main
    branch 'main' set up to track 'origin/main'.

From the output, you can see that the contents have been pushed, a new branch `main` has been added to the remote, and that locally, the remote branch will be identified through the name `origin/main`.
If you refresh the website now, you should the the `README.md` in your repository.

A synchronization might also be necessary in the other direction.
To illustrate this case, first open the `README.md` in your GitLab overview.
You can find a blue `Edit` button that allows to to change your file directly in the browser.
Change `Hello World!` to `Hello <your name>!`.
You cannot `save` this file though, the website only allows you to `commit` the file, which requires you to define a commit message and a target branch.
Use the default values for both fields and commit the change.

The website will now show you the new content of the `README.md`, locally, however, the commit does not yet exist and a `git log` only shows the first commit.
To change that, you need to synchronize the remote repository with your local repository.
You can achieve this by *fetching* all changes.

    $ git fetch origin
    remote: Enumerating objects: 5, done.
    remote: Counting objects: 100% (5/5), done.
    remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
    Unpacking objects: 100% (3/3), 253 bytes | 84.00 KiB/s, done.
    From gitlab.ewi.tudelft.nl:cse1105/git-assignment
        9963ad2..58193d1  main       -> origin/main

The output of the command shows you what changed.
Most importantly, it will show you that the remote branch `origin/main` has changed and it will move the local pointer for the remote branch.
Use `git log --all` to see the state of both the local and the remote branch.

    $ git log --all
    commit 58193d18379671f334b74fc14ec7d8d048e89438 (origin/main)
    Author: Sebastian Proksch <s.proksch@tudelft.nl>
    Date:   Fri Feb 24 15:49:44 2023 +0100
        Update README.md
    
    commit 9963ad2601f37e353aec0d1b01f23374ea2e2c8e (HEAD -> main)
    Author: Sebastian Proksch <development@mail.proks.ch>
    Date:   Fri Feb 24 15:28:42 2023 +0100
        Initial commit with a README.md

From this output, you get two important information.
First, your current working directory (`HEAD`) is using the `main` branch, which is currently pointing to commit `9963ad`.
Second, the remote branch `origin/main` has a newer commit `58193d`.

To integrate the new commit, you need to *merge* the changes into your current branch.

    git merge origin/main
    Updating 9963ad2..58193d1
    Fast-forward
        README.md | 2 +-
        1 file changed, 1 insertion(+), 1 deletion(-)

The output shows you that all changes could be successufuly merge into your current branch.
You can see that it was a *fast-forward* merge, i.e., no additional merge commit was necessary to solve conflicts or to join multiple parent commits.

Calling `git log --all` again will now show you that also your local branch now points to the new commit.
The remote changes have been successfully synced to the local repository.

To avoid having to type both commands (`fetch` and `merge`) all the time, Git has a shortcut.
You can use `git pull` to *automatically* perform both operations together in one go.

### Use Feature Branches for Code Contributions


.gitignore

branch
checkout

diff
reset 

push to GL
On GitLab, open MR, explore the different fields, merge.


### Conflicts

git clone into new directory (?? local/remote?)
?? git remote rename
?? git add remote

1) F1: rename endpoint class
...
Open MR

2) F2: change endpoint content
...
open MR


Merge F1
Try to merge F2 :/

Locally merge both, look at Patch notation
introduce merge commit
push F2v2

Merge MR


### Visualization

branches, tags, tree are important

Hard to understand the state of multiple repositories in a flattened git log list... use visualizations to explore the tree

Thsi can be done via

`git log --oneline --decorate --graph --all`

Even better, use a GUI tool like Sourcetree, which shows all information in a nice layout and gives convenient access to many basic operations (add/reset)


### Completion

You know that you have successfully completed the assignment, when the visualization of your local repository looks similar to what you have seen before and when all these changes have been pushed to the repo.
TA will check the repo and the MRs.




