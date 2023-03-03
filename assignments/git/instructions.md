---
layout: page
title: Instructions
parent: Git
grand_parent: Assignments
nav_order: 3
---

# {{ page.title }}

This assignment follows the introductory [Tools][tools] lecture, please make sure that you have watched the lecture before starting this assignment, so you are familiar with the terminology.

The goal of this assignment is two-fold:

1. You will learn how a basic Spring Boot application is setup.
This will allow you to recognize all the modifications that have already been introduced in the OOPP template project of your team.
2. You will learn about the basic Git commands and exercise day-to-day Git usage.



[tools]: {% link material/index.md %}

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

Double check that you have run `git init` in the right folder that contains your netid.
The rest of this assignment assumes that you are running commands from within this directory.

Make sure that you have setup the [Recommended Git configuration][git-setup].
Run `git config -l` to see the configured details, which should contain entries for your *name*, *email address* and for *line-endings* (`autocrlf`).
If any of these are missing, set them now.
Most importantly, ensure that your *email address* ends in a `@student.tudelft.nl` or you won't be able to push your commits to the server.

[git-setup]: {% link assignments/git/install.md %}

At this point, `oopp-<netid>` is a fully working local repository that you can use for versioning files.

#### Adding Content

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

The *status* shows you some information like the open changes or the branch that you are currently working on.
If your current branch is `master` and not `main`, rename your branch with `git branch -m main`.
We will cover more details on branching later.

The *status* output shows you that Git sees the change in the `README.md`, but does not consider it, as the file is not tracked.
Start tracking the file by adding it to the index, either by invoking `git add README.md` (to add this one file) or by adding *all* changes and untracked files by invoking `git add -A`.
You can investigate the effect of this command by running `git status` again:

    $ git status
    On branch main
    No commits yet
    Changes to be committed:
        (use "git rm --cached <file>..." to unstage)
            new file:   README.md

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

### Reverting Unwanted Changes

Sometimes, ideas do not work out and changes need to be reverted.
There are multiple ways to do so, which depend on what you want to revert.
You need to consider two relevant dimensions.

1. Has the change been *staged*, i.e., been added to the *staging area*?
2. Are the changed files already *tracked*, i.e., are they under version control?

Reverting *staged* changes is always the same, regardless of whether the file has been tracked before.
Create a new file `LICENSE` *and* introduce new changes to the `README.md` file.
Then stage both changes.

    $ echo "..." > LICENSE
    $ echo "123" >> README.md # append content to the file
    $ git add -A # stage all changes

Running `git status` will tell you that both changes are *to be committed*.
For this example, we do not want to commit these changes and want to revert them to their previous state.
To remove the individual changes from the *staging area* again, simply *reset* each file.

    $ git reset LICENSE
    $ git reset README.md

This will only reset the *staging area* though, the *working area* stays untouched.
If you look at `git status` again, you will see that the changes still exist, but they no longer appear as *to be committed*, but as changes in a tracked and in an untracked file.

If you want to get rid of these, you need to consider the previous state of the file.
If it was under version control before then you can restore a previous version.

    $ git restore README.md

Check the output of `git status` once more, you will see that the `README.md` no longer has open changes.
You can also use `git restore` to recover an accidentally deleted file when it was under version control.
Delete `README.md` and restore it again.

    $ rm README.md
    $ git restore README.md

The approach is different for files that are not under version control, like the `LICENSE` file, which is now simply marked as new.
If you want to remove these changes, you can either just delete this file directly on the file system, or you can use `git clean` to remove all untracked files from the whole working area at once.

Be aware that you can loose unsaved work with this operation if you are not careful, as such, it is recommended to *always* perform a dry run first, before deleting anything.

    git clean -dn # first inspect all differences
    git clean -df # remove everything that is not under version control

In a typical programming task, many files will be changed at once and it is cumbersome to *reset*, *restore*, *delete*, ... multiple individual files.
For these situations, you can use advanced parameters of the *reset* command that alter its behavior.
The two most useful are:

- `--mixed` resets the staging area, but not the working area
- `--hard` reset both the staging area and the working area

To investigate the effects of these options, first perform three changes and stage two of it.

    $ echo "..." >> README.md # append content to the file
    $ echo "..." > LICENSE # create a new file
    $ echo "..." > CONTRIBUTORS
    $ git add LICENSE # only stage LICENSE

The effect of running these commands is that you now have three different types of files: a file that was previous under version control that now has unstaged changes (`README.md`), a new file with staged changes (`LICENSE`), and a new file with unstages changes (`CONTRIBUTORS`).

Now use `git reset --mixed` and use `git status` to see the effects.
Re-introduce all changes and repeat the same with the `--hard` option.
You will see that the latter will reset all changes in your index *and* your working area at the same time, but only for files that are either *staged* or *tracked*.
The untracked `CONTRIBUTORS` file is is not touched, so remove it manually or use a *clean* to get rid of it.
At this point, `git status` should report a clean working area again and an empty index.


### Remotes

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

It is time to add some actual contents to the repository.
For this, we will download and add a basic Spring Boot starter application.
Open the [Spring Initializer][spring-init].
You can leave all setting at their default values, but make sure to add the *Spring Web* dependency.
Generate and download the starter package, unzip the download, and move all contents (not just the `demo` directory itself) into the root of your repository.
Make sure that you do not forget to move the hidden `.gitignore` file.

Try to build the project with Gradle now to see if your system has all the required software installed.

    $ ./gradlew build
    BUILD SUCCESSFUL in 747ms
    7 actionable tasks: 7 up-to-date

If the build is not successful, make sure that you have a current Java version installed and that it is correctly setup (e.g., the `JAVA_HOME` environment variable is set correctly).
At this point, import the repository directory into your IDE.
Popular IDEs like [IntelliJ](https://www.jetbrains.com/idea/) or [Eclipse](https://www.eclipse.org/ide/) have wizards for importing existing Gradle project to simplify this step.



[spring-init]: https://start.spring.io/

We want to use a feature branch to commit our changes to the repository.
Invoking `git branch` will show you that you are currently on the `main` branch, so we will add new branch called `spring`.

    $ git branch
    * main
    $ git branch spring

If you invoke `git branch` again, you will see that the branch has been created, but that `main` is still the active branch.
Use `git checkout` to switch to the new branch.

    $ git branch
      spring
    * main
    $ git checkout spring
    ... some output ...
    $ git branch
    * spring
      main

Git provides a shortcut for creating branches.
You can use `git checkout -b <name>` to create and switch to a new branch in one command.

We are now at the point to add the Spring starter application to the repository.
Run `git add -A` to add all files to the staging area and inspect the effect with `git status`.

    $ git status
    On branch spring
    Changes to be committed:
      (use "git restore --staged <file>..." to unstage)
        new file:   .gitignore
        new file:   build.gradle
        new file:   gradle/wrapper/gradle-wrapper.jar
        new file:   gradle/wrapper/gradle-wrapper.properties
        new file:   gradlew
        new file:   gradlew.bat
        new file:   settings.gradle
        new file:   src/main/java/com/example/demo/DemoApplication.java
        new file:   src/main/resources/application.properties
        new file:   src/test/java/com/example/demo/DemoApplicationTests.java

If your status shows more files in the staging area, you likely forgot to move the `.gitignore` file from the starter pack.
Use `git reset --mixed` to reset the staging area.
After you have fixed your `.gitignore` file, you need to add all files once more (`git add -A`).

Inspect the `.gitignore` file now.
Files that match any of the entries will be ignored by Git.
To test this feature, hide you `.gitignore` from Git by renaming it to any other abitray name and run `git status` again.
You will then see that, for example, the folder `.gradle/` and `build/` are now shown as untracked.
Rename the file back to `.gitignore` and these changes will disappear once more.

As a useful *rule of thumb*, you should generally only add *genuine* files to your repository (e.g., \*.java, build.xml) and avoid committing *derived* files that will be generated during the build.

When your index is in the same state as in the previous listing of `git status`, *commit the changes* and *push the commit* to GitLab.

    $ git branch # double check that you are on the right branch
      main
    * spring
    $ git commit -m "Add Spring starter application"
    $ git push origin spring
    Enumerating objects: 27, done.
    Counting objects: 100% (27/27), done.
    Delta compression using up to 8 threads
    Compressing objects: 100% (15/15), done.
    Writing objects: 100% (26/26), 60.17 KiB | 10.03 MiB/s, done.
    Total 26 (delta 0), reused 0 (delta 0), pack-reused 0
    remote:
    remote: To create a merge request for spring, visit:
    remote:   https://gitlab.ewi.tudelft.nl/cse1105/<year>/students/oopp-<netid>/-/merge_requests/new?merge_request%5Bsource_branch%5D=spring
    remote:
    To gitlab.ewi.tudelft.nl/cse1105/<year>/students/oopp-<netid>
     * [new branch]      spring -> spring

Open your GitLab repository in the browser.
GitLab will tell you about your recent commit and give you the option to create a *Merge Request*.
Create an MR and explore the various options.
Usually, an MR will be reviewed by team members before merging, but for this example, merge the MR into `main` yourself.
Make sure that the repository overview shows you all the files that you have just committed.

Your local repository does not yet know about the changes on `main`, because the merge was only performed remotely.
Switch your working area to the `main` branch and inspect the directory contents.

    $ git checkout main
    $ ls # you should not see any of the files that you have committed

To finalize the work on the feature branch, two more steps are required.
You need to `pull` the latest changes from the remote to get the updates on `main`.
We also still need to delete the (now integrated) `spring` feature branch.

    $ git pull
    ...
    $ git branch -d spring
    Deleted branch spring (was 8f8003a).
    $ git branch
    * main

These two steps present the finalization of a complete workthrough through a feature-based development cycle.

You will practice this cycle once more by adding a first simple *Hello World* endpoint to the Spring application.
Create a new branch `helloworld` in your project and add the following class.

    package com.example.demo;
    
    import org.springframework.stereotype.Controller;
    import org.springframework.web.bind.annotation.GetMapping;
    import org.springframework.web.bind.annotation.RequestMapping;
    import org.springframework.web.bind.annotation.ResponseBody;
    
    @Controller
    @RequestMapping("/")
    public class HelloWorld {
    
        @GetMapping("/")
        @ResponseBody
        public String index() {
            return "Hello world!";
        }
    }

After adding this class, you can start the Spring applciation via Gradle (`./gradlew bootRun`) and open [localhost:8080](http://localhost:8080/) to see a "Hello World" greeting.
Once you are sure that the endpoint is working, follow the same feature-branch development style from before.

After merging the feature, make sure to pull your local `main` branch to integrate all changes.


### Conflicts

In your day-to-day work, you will face situations, in which parallel work will result in incompatible changes.
This part will create such a conflict and illustrate how to fix it.

#### Change greeting

As the first task, change the greeting of the `HelloWorld` endpoint from `"Hello world!"` to `"Hi world!"`.
Perform this change on a feature branch called `greeting` and follow the same pattern as before (branch » edit » add » commit » push » open MR), but do NOT merge the MR just yet.

#### Make uppercase

The second task will mimic work that happens in parallel to the fist one.
Switch back to the main branch (`git checkout main`) and double check that this also reverts the greeting to the old phrase.
As the second task, make the greeting uppercase (i.e., `"HELLO WORLD!!"`)
Perform this change on a feature branch called `uppercase` and follow the same pattern as before (branch » edit » add » commit » push » open MR), but do NOT merge the MR just yet.

#### Conflict resolution

We will now try to merge all changes back into the `main` branch.
Start by merging the MR that contains the changed greeting, which should still work as expected.
The conflict will appear when you now try to merge the uppercase feature as well.
GitLab will inform you that the merge is blocked, because merge conflicts exist that need to be resolved first.
While our trivial example could even be solved in the website, a regular programming feature is much more complex, so we will explore how to solve the issue on your computer.

The problem is that both changes affect the same line, so Git does not know how to resolve that automatically and a manual merge is required.
The first task has already been merge back into `main`, so you need to pull the updates from the remote.

    $ git checkout main
    $ git pull

After that, checkout the branch that has the merge conflict and merge the updates of main into the feature branch.

    $ git checkout uppercase
    $ git merge main
    Auto-merging src/main/java/com/example/demo/HelloWorld.java
    CONFLICT (content): Merge conflict in src/main/java/com/example/demo/HelloWorld.java
    Automatic merge failed; fix conflicts and then commit the result.

Git will inform you about the merge conflict and ask you to fix the conflict.
Use `git status` to understand which files are affected.

    $ git status
    On branch uppercase
    Your branch is up to date with 'origin/uppercase'.
    
    You have unmerged paths.
      (fix conflicts and run "git commit")
      (use "git merge --abort" to abort the merge)
    
    Unmerged paths:
      (use "git add <file>..." to mark resolution)
        both modified:   src/main/java/com/example/demo/HelloWorld.java
    
    no changes added to commit (use "git add" and/or "git commit -a")

In this example, the `HelloWorld` class is the only unmerged file.
When you open this class, you will see that Git has marked the conflict in [diff notation][wikipedia-diff] that contains both versions of the conflicting code.

[wikipedia-diff]: https://en.wikipedia.org/wiki/Diff

    <<<<<<< HEAD
        return "HELLO WORLD!!";
    =======
        return "Hi world!";
    >>>>>>> main

You need to solve this conflict yourself.
Replace the whole diff block with the correct solution, for the example, use `"HI WORLD!!"` as the greeting.
Ensure that the resulting file is valid Java code before you continue.
Once you have solved the conflict, add the file to the staging area (`git add src/main/java/com/example/demo/HelloWorld.java`) and run `git commit`, the commit message will be an auto-generate merge message.
You can now push the `uppercase` branch to GitLab.

If you open your `uppercase` MR on the GitLab website again, you will see that both commits (the original change and the conflict resolution) are now assocated with the MR.
With the conflict being resolved, it also became possible now to merge the MR into `main`.
Merge the MR and pull the changes to your local `main` branch.


### Visualization and Branch Hygiene

So far, we have mainly used `git log`, `git branch`, and `git status` to understand the current state of the working area, staging area, and the two repositories.
It is very important though to understand the current state of all branch pointers, the available commits, and differences between the local and the remote repository, so such a textual representation quickly comes to its limits.

It is highly recommended to visualize the histories to get a better overview of whats going on.
As a very simple first step, `git log` can be used to render a graph and not just a list.
The current state of your repository should look something like the following.

    $ git log --oneline --decorate --graph --all
    *   79ee43a (HEAD -> main, origin/main) Merge branch 'uppercase' into 'main'
    |\
    | *   beee1d9 (origin/uppercase, uppercase) Merge branch 'main' into uppercase
    | |\
    | |/
    |/|
    * |   0f480e5 Merge branch 'greeting' into 'main'
    |\ \
    | * | bc2e211 (origin/greeting, greeting) Change greeting
    |/ /
    | * 8281d5f Make uppercase
    |/
    *   c537aee Merge branch 'helloworld' into 'main'
    |\
    | * 7e82be2 (origin/helloworld, helloworld) Add endpoint
    |/
    *   9c5cbd9 Merge branch 'spring' into 'main'
    |\
    | * 8835e49 (origin/spring, spring) Add Spring starter application
    |/
    * 58193d1 Update README.md
    * 9963ad2 Initial commit with a README.md

This provides a much better overview over the repository by not just listing all commits, but also by visualizing the history and by showing the current locations of all branch pointers.
While this is already a great improvement over a basic `git log`, we strongly recommend you to consider using a graphical Git client.
The following shows a rendering in the Sourcetree application:

![Graphical representation of the repository]({% link assignments/git/images/sourcetree-all-branches.png %})

The presented information is the same, but the graphical capabilities of a UI application not only allow for a much nicer layouting, you will also get convenient, context-specific access to many basic operations just by clicking on the various elements.
The graphic representation also tends to be easier to consume when the repository grows.

Regardless of which visualization you decide to use, it becomes obvious that even this tiny example has already created a complex history.
We strongly recommend you to practice basic repository hygiene, like performing a branch clean-up after completing a feature or using advanced features to avoid countless merge commits that make it hard to follow the history.

#### Delete old branches

When merging an MR on GitLab, you have the option to *delete the source branch*.
This is a reasonable default, as a branch is no longer needed when it has been merged into `main`.
You can check in your GitLab overview (Left Menu » Repository » Branches), whether you have already deleted the branches in your remote repository.

If the branches do not exist on GitLab anymore, the deletion still needs to be propagated to your local repository.
You should already know that `git fetch` synchronizes all changes from a remote repository to your local repository, but it is a non-destructive operation by default.
You need to explicitly instruct it to *prune tracking branches* that do *no longer exist remotely* by using the `-p` option.

    $ git fetch -p
    Fetching origin
    From gitlab.ewi.tudelft.nl/cse1105/<year>/students/oopp-<netid>
     - [deleted]         (none)     -> origin/greeting
     - [deleted]         (none)     -> origin/helloworld
     - [deleted]         (none)     -> origin/spring
     - [deleted]         (none)     -> origin/uppercase
    Already up to date.

If the branches still exist remotely, you can either delete them in the GitLab overview, or you delete them directly with Git.

    $ git push -d origin greeting # repeat for all branches that should be deleted
    To gitlab.ewi.tudelft.nl/cse1105/<year>/students/oopp-<netid>
     - [deleted]         greeting

As the last step, ensure that you have deleted your local branches as well.
If you forgot to delete a branch after finishing the work, you can to delete it with the `git branch` command.

    $ git branch -d greeting # repeat for all branches that should be deleted
    Deleted branch greeting (was bc2e211).

Git tries to actively prevent the pruning of information that is not merged in to `main`, so you might encounter situations, in which local branches cannot be deleted.
If you are sure, you can use an upper case `-D` option (instead of `-d`) to enforce the deletion in these cases.

To finalize this part, ensure that the only branch that you have left *locally and remotely* is `main`.


#### Advanced Git Usage

Printing the commit log of this tiny exercise has shown that it quickly becomes difficult to follow the project history, when many branches and merge commits exist.
To avoid this situation, many advanced Git users [advocate for maintaining a linear history][git-linear-history] (good write-up of the subject).

[git-linear-history]: https://www.bitsnbites.eu/a-tidy-linear-git-history/

In short, the solution is to either [squash][gittower-squash] feature branches into a single commit that is then appended onto `main`, or to [rebase][atlassian-rebase] the feature branch onto `main`, before merging it in a *fast-forward* merge (i.e., a merge that does not require the creation of a merge commit).
Both styles have their advantages over a basic *merge*, but they require a better understanding of Git and might overwhelm beginners.
Additionally, rebasing a feature branch requires *force pushing*.
While this is safe on feature branches, as they should not be developed by multiple developers anyways, it can potentially break the repository when you don't know what you are doing.

Given the steep learning curve and the challenges of *squashing* and *rebasing*, we do not expect that every student will adopt the advanced concepts.
Just sticking with a basic *merge* is fine for the course.
However, we encourage you to learn about rebase/squash and to try them out, so you can make an educated decision on which merging strategy you prefer and grow as a developer.

[gittower-squash]: https://www.git-tower.com/learn/git/faq/git-squash/
[atlassian-rebase]: https://www.atlassian.com/git/tutorials/merging-vs-rebasing#the-golden-rule-of-rebasing


### Completion

You know that you have successfully completed the assignment, when all your changes have been merged to `main` and when the branches have been deleted from the repository.
Your TA will check your personal repository and the MRs to validate that you have completed the assignment.




