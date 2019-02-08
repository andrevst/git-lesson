# Git version control


## Version control

The main point of a version control system is help to maintain a detailed history of the project as well as the ability to work on different versions of it. 

*You’ve probably created your own version control system without realizing it. Got any files like this?*

MyResumeOct2015.doc
- MyResumeResumeMar2016.doc
- logov3.png
- logov4.png
- logo-old.png

Our shared folder/naming system is fine for class projects or one-time papers. But for software development? No way, it's almost impossible to work that way and too risk.

Large, fast-changing projects with many authors need a Version Control System to track changes and avoid general chaos. A good VCS does the following:

- Backup and Restore. Files are saved as they are edited, and you can jump to any moment in time. Need that file as it was on Feb 23, 2007? No problem.

- Synchronization. Lets people share files and stay up-to-date with the latest version.

- Short-term undo. Monkeying with a file and messed it up? (That’s just like you, isn’t it?). Throw away your changes and go back to the “last known good” version in the database.

- Long-term undo. Sometimes we mess up bad. Suppose you made a change a year ago, and it had a bug. Jump back to the old version, and see what change was made that day.

- Track Changes. As files are updated, you can leave messages explaining why the change happened (stored in the VCS, not the file). This makes it easy to see how a file is evolving over time, and why.

- Track Ownership. A VCS tags every change with the name of the person who made it. 

- Sandboxing, or insurance against yourself. Making a big change? You can make temporary changes in an isolated area, test and work out the kinks before “checking in” your changes.

- Branching and merging. A larger sandbox. You can branch a copy of your code into a separate area and modify it in isolation (tracking changes separately). Later, you can merge your work back into the common area.

There are a number of Version Control Systems out there. Three of the most popular version control systems are:

 - Git
 - Subversion
 - Mercurial

And there are two main models of vcs:

- the centralized model - all users connect to a central, master repository
- the distributed model - each user has the entire repository on their computer

## Git

- First developed by Linux Kernel Creator, Linus Torvalds.

- Git is a distributed VSC, so there is no singular centralized code base that the code can be pulled from.

- As a fast and efficient system, many developers and open-source projects use Git to power their repos.

## Github

- GitHub is a Git repository hosting service, but it adds some of its own features. 

- It provides access control and several collaboration features, such as wikis and basic task management tools for every project.

The flagship functionality of GitHub is Forking. Which is the ability to copy a repository from one user’s account to another. 

If you make changes you’d like to share, you can send a notification called a “pull request” to the original owner. 

That user can then, with a click of a button, merge the changes found in your repo with the original repo.

These three features – fork, pull request and merge – are what make GitHub so powerful.


## Terminology

Git have so many functionalities so above are the basic terminology to understand how git works.

### Commit

Git thinks of its data like a set of snapshots of a mini filesystem. Every time you commit (save the state of your project in Git), it basically takes a picture of what all your files look like at that moment and stores a reference to that snapshot. You can think of it as a save point in a game - it saves your project's files and any information about them.

Everything you do in Git is to help you make commits, so a commit is the fundamental unit in Git.

Repository / repo
A repository is a directory which contains your project work, as well as a few files (hidden by default on Mac OS X) which are used to communicate with Git. Repositories can exist either locally on your computer or as a remote copy on another computer. A repository is made up of commits.

### Working Directory

The Working Directory is the files that you see in your computer's file system. When you open your project files up on a code editor, you're working with files in the Working Directory.

This is in contrast to the files that have been saved (in commits!) in the repository.

When working with Git, the Working Directory is also different from the command line's concept of the current working directory which is the directory that your shell is "looking at" right now.

### Checkout

A checkout is when content in the repository has been copied to the Working Directory.

Staging Area / Staging Index / Index
A file in the Git directory that stores information about what will go into your next commit. You can think of the staging area as a prep table where Git will take the next commit. Files on the Staging Index are poised to be added to the repository.

### SHA

A SHA is basically an ID number for each commit. Here's what a commit's SHA might look like: e2adf8ae3e2e4ed40add75cc44cf9d0a869afeb6.

It is a 40-character string composed of characters (0–9 and a–f) and calculated based on the contents of a file or directory structure in Git. "SHA" is shorthand for "Secure Hash Algorithm". If you're interested in learning about hashes, check out our Intro to Computer Science course.

## Branch
A branch is when a new line of development is created that diverges from the main line of development. This alternative line of development can continue without altering the main line.

Going back to the example of save point in a game, you can think of a branch as where you make a save point in your game and then decide to try out a risky move in the game. If the risky move doesn't pan out, then you can just go back to the save point. The key thing that makes branches incredibly powerful is that you can make save points on one branch, and then switch to a different branch and make save points there, too.

With this terminology in mind, let's take a high-level look at how we'll be using Git by looking at the typical workflow when working with version control.

## Basic Commands

Now I will show you some basic commands to understand how to work on Git.


### Git Init

```
$ git init
```

 Create a new, empty repository in the current directory.

### Git Clone

```
$ git clone <path-to-repository-to-clone>
```

Create the new repo inside the current working directory, which means that the current working directory is still outside of this new Git repo. Make sure you cd into the new repository.

 - Takes the path to an existing repository
 - By default will create a directory with the same name as the repository that's being cloned
 - Create the new repository inside of the current working directory

### Git Status

```
$ git status
```

The result:
```
On branch master
Your branch is up-to-date with 'origin/master'.
nothing to commit, working directory clean
```
The output tells us two things:

 - On branch master – this tells us that Git is on the master branch.
 - Your branch is up-to-date with 'origin/master'. – Because git clone was used to copy this repository from another computer, this is telling us if our project is in sync with the one we copied from.
 - nothing to commit, working directory clean – this is saying that there are no pending changes. No staging to commit and no change to add.

### Git Log

 ```
 $ git log
 ```

Shows the commit story of the repository/branch

By default, this command displays:

 - the SHA - git log will display the complete SHA for every single commit. Each SHA is unique, so we don't really need to see the entire SHA. We could get by perfectly fine with knowing just the first 6-8 characters. Wouldn't it be great if we could save some space and show just the first 5 or so characters of the SHA?
 - the author - the git log output displays the commit author for every single commit! It could be different for other repositories that have multiple people collaborating together, but for this one, there's only one person making all of the commits, so the commit author will be identical for all of them. Do we need to see the author for each one? What if we wanted to hide that information?
 - the date - By default, git log will display the date for each commit. But do we really care about the commit's date? Knowing the date might be important occasionally, but typically knowing the date isn't vitally important and can be ignored in a lot of cases. Is there a way we could hide that to save space?
 - the commit message - this is one of the most important parts of a commit message...we usually always want to see this

Navigating the log:

 - to scroll down, press:
   - j or ↓ to move down one line at a time
   - d to move by half the page screen
   - f to move by a whole page screen
 - to scroll up, press:
   - k or ↑ to move up one line at a time
   - u to move by half the page screen
   - b to move by a whole page screen
 - press q to quit out of the log (returns to the regular command prompt)

#### --oneline flag is used to alter how git log displays information:

```
 $ git log --oneline
```

 - lists one commit per line
 - shows the first 7 characters of the commit's SHA
 - shows the commit's message

#### --stat flag is used to alter how git log displays information:

```
$ git log --stat
```

 - displays the file(s) that have been modified
 - displays the number of lines that have been added/removed
 - displays a summary line with the total number of modified files and lines that have been added/removed

#### -p flag (which is the same as the --patch flag) is used to alter how git log displays information:

```
$ git log -p
```

 - displays the files that have been modified
 - displays the location of the lines that have been added/removed
 - displays the actual changes that have been made

### Git Show

```
$ git show [SHA]
```

git show command will show only one commit. So don't get alarmed when you can't find any other commits - it only shows one. The output of the git show command is exactly the same as the git log -p command. So by default, git show displays:

 - the commit
 - the author
 - the date
 - the commit message
 - the patch information

However, git show can be combined with most of the other flags we've looked at:

 - --stat - to show the how many files were changed and the number of lines that were added/removed
 - -p or --patch - this the default, but if --stat is used, the patch won't display, so pass -p to add it again
 - -w - to ignore changes to whitespace

### Git Add

 used to move files from the Working Directory to the Staging Index.

```
 $ git add <file1> <file2> … <fileN>
```

 - takes a space-separated list of file names
 - alternatively, the period . (or * or -all) can be used in place of a list of files to tell Git to add the current directory (and all nested files)

### Git Commit

```
$ git commit
```

 - will open the code editor that is specified in your configuration
 - (check out the Git configuration step from the first lesson to configure your editor)

Inside the code editor:

 - a commit message must be supplied
 - lines that start with a # are comments and will not be recorded
 - save the file after adding a commit message
 - close the editor to make the commit

#### -m flag is used to write the commit message directly from the cli

```
$ git commit -m 'my message'
```

### Git Diff

used to see changes that have been made but haven't been committed, yet:
```
$ git diff
```
This command displays:

 - the files that have been modified
 - the location of the lines that have been added/removed
 - the actual changes that have been made

### Changing The Last Commit

 You've already made plenty of commits with the git commit command. Now with the ```--amend flag```, you can alter the most-recent commit.

```
 $ git commit --amend
 ```

### Git Revert
the git revert command is used to reverse a previously made commit:

```
 $ git revert <SHA-of-commit-to-revert>
 ```

 - will undo the changes that were made by the provided commit
 - creates a new commit to record the change

### Git Reset

the git reset command is used erase commits:
```
 $ git reset <reference-to-commit>
```

It can be used to:

 - move the HEAD and current branch pointer to the referenced commit
 erase commits with the --hard flag
 - moves committed changes to the staging index with the --soft flag
 unstages committed changes --mixed flag

Typically, ancestry references are used to indicate previous commits. The ancestry references are:

 - ^ – indicates the parent commit
 - ~ – indicates the first parent commit

### Git Branch

git branch command is used to manage branches in Git:

```
# to list all branches
$ git branch

# to create a new "footer-fix" branch
$ git branch footer-fix

# to delete the "footer-fix" branch
$ git branch -d footer-fix
```

This command is used to:

list out local branches
create new branches
remove branches

### Git Merge 

the git merge command is used to combine branches in Git:
```
$ git merge <other-branch>
```

There are two types of merges:

 - Fast-forward merge – the branch being merged in must be ahead of the checked out branch. The checked out branch's pointer will just be moved forward to point to the same commit as the other branch.
the regular type of merge
two divergent branches are combined
a merge commit is created

 - Merge conflict - A merge conflict happens when the same line or lines have been changed on different branches that are being merged. Git will pause mid-merge telling you that there is a conflict and will tell you in what file or files the conflict occurred.

#### Merge Conflict Indicators

The editor has the following merge conflict indicators:

```
<<<<<<< HEAD everything below this line (until the next indicator) shows you what's on the current branch
||||||| merged common ancestors everything below this line (until the next indicator) shows you what the original lines were
======= is the end of the original lines, everything that follows (until the next indicator) is what's on the branch that's being merged in
>>>>>>> heading-update is the ending indicator of what's on the branch that's being merged in (in this case, the heading-update branch)
```
#### Resolving A Merge Conflict

Git is using the merge conflict indicators to show you what lines caused the merge conflict on the two different branches as well as what the original line used to have. So to resolve a merge conflict, you need to:

 - locate and remove all lines with merge conflict indicators
 - determine what to keep
 - save the file(s)
 - stage the file(s)
 - make a commit
 
_Be careful that a file might have merge conflicts in multiple parts of the file, so make sure you check the entire file for merge conflict indicators - a quick search for <<< should help you locate all of them._



### Git Tag

```
$ git tag -a v1.0
```

This flag tells Git to create an annotated flag. If you don't provide the flag (i.e. ```git tag v1.0```) then it'll create what's called a lightweight tag.

## Working with remote repository

A remote repository is a repository that's just like the one you're using but it's just stored at a different location. To manage a remote repository, use the git remote command:

```
$ git remote
```

 - It's possible to have links to multiple different remote repositories.
 - A shortname is the name that's used to refer to a remote repository's location. Typically the location is a URL, but it could be a file path on the same computer.
 - ```git remote add``` is used to add a connection to a new remote repository.
 - ```git remote -v``` is used to see the details about a connection to a remote.


### Git Push

The git push command is used to send commits from a local repository to a remote repository.

```
$ git push origin master
```

The git push command takes:

 - the shortname of the remote repository you want to send commits to
 - the name of the branch that has the commits you want to send

### Git Pull

If there are changes in a remote repository that you'd like to include in your local repository, then you want to pull in those changes. To do that with Git, you'd use the git pull command. You tell Git the shortname of the remote you want to get the changes from and then the branch that has the changes you want:

```
$ git pull origin master
```

When git pull is run, the following things happen:

 - the commit(s) on the remote branch are copied to the local repository
 - the local tracking branch (origin/master) is moved to point to the most recent commit
 - the local tracking branch (origin/master) is merged into the local branch (master)

Also, changes can be manually added on GitHub (but this is not recommended, so don't do it).

You can think of the git pull command as doing two things:

 - fetching remote changes (which adds the commits to the local repository and moves the tracking branch to point to them)
 - merging the local branch with the tracking branch

### Git Fetch

The git fetch command is just the first step. It just retrieves the commits and moves the tracking branch. It does not merge the local branch with the tracking branch. The same information provided to git pull is passed to git fetch:

 - the shortname of the remote repository
 - the branch with commits to retrieve

```
$ git fetch origin master
```

## Working in someone else repository

### Fork

Forking is an action that's done on a hosting service, like GitHub. Forking a repository creates an identical copy of the original repository and moves this copy to your account. You have total control over this forked repository. Modifying your forked repository does not alter the original repository in any way.

### Multiple developer's repo

The git log command is extremely powerful, and you can use it to discover a lot about a repository. But it can be especially helpful to discover information about a repository that you're collaborating on with others. You can use git log to:

 - group commits by author with git shortlog

```
$ git shortlog
```

 - filter commits with the --author flag

```
$ git log --author="Author Name"
```

 - filter commits using the --grep flag

```
$ git log --grep="border radius issue in Safari"
```

### Best Practices


#### Write Descriptive Commit Messages

While we're talking about naming branches clearly that describe what changes the branch contains, I need to throw in another reminder about how critical it is to write clear, descriptive, commit messages. The more descriptive your branch name and commit messages are the more likely it is that the project's maintainer will not have to ask you questions about the purpose of your code or have dig into the code themselves. The less work the maintainer has to do, the faster they'll include your changes into the project.

#### Create Small, Focused Commits

This has been stressed numerous times before but make sure when you are committing changes to the project that you make smaller commits. Don't make massive commits that record 10+ file changes and changes to hundreds of lines of code. You want to make smaller, more frequent commits that record just a handful of file changes with a smaller number of line changes.

Think about it this way: if the developer does not like a portion of the changes you're adding to a massive commit, there's no way for them to say, "I like commit A, but just not the part where you change the sidebar's background color." A commit can't be broken down into smaller chunks, so make sure your commits are in small enough chunks and that each commit is focused on altering just one thing. This way the maintainer can say I like commits A, B, C, D, and F but not commit E.

#### Update The README

And lastly if any of the code changes that you're adding drastically changes the project you should update the README file to instruct others about this change.

#### DO NOT work on the master branch

make sure to give the topic branch clear, descriptive name
As a general best practice for writing commits:
