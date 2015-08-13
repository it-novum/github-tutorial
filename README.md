This is a quick start guide for developers that are interested in learning git
# Install git on your maschine
Ubuntu and Debian:
````
apt-get install git
````

Mac OS X
On Mac OS you need to download [Xcode](https://itunes.apple.com/de/app/xcode/id497799835?mt=12) from the Mac App Store

# Should I use a GUI or the command line?
A nice and easy to use GUI is the [GitHub for Windows](https://desktop.github.com/) or [GitHub for Mac](https://desktop.github.com/) but I recommend to use the command line. It's very easy and fast!

# The most important commands
### How to clone a repository (Called checkout in SVN world)
Let use clone this repository.
````
git clone https://github.com/it-novum/github-tutorial.git
````
With **git clone** you create a clone of the repository on your local maschine.

By default git will create a directory with the name of the repository. So the clone is inside of **github-tutorial/** on your maschine now.

### Git status
The command **git status** show you all the files your touched, changed, created or delete in your local repository.

As you can see in the following example I modified the file **playground** AND i created the file **README.md**

So at the moment only the playground file is tracked by git.

Now we want to add our new README.md to git as well. The git shell shows you the command to do this.

````
[14:10]git@gitexample~/Documents/GitHub/github-tutorial# git status
On branch master
Your branch is ahead of 'origin/master' by 1 commit.
  (use "git push" to publish your local commits)
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   playground

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	README.md

no changes added to commit (use "git add" and/or "git commit -a")
````
To add the README.md file type
````
git add README.md
````

### Git diff
As you already expected by the name, **git diff** is able to show you the modifications your did in a file.
````
[14:13]git@gitexample~/Documents/GitHub/github-tutorial# git status
On branch master
Your branch is ahead of 'origin/master' by 2 commits.
  (use "git push" to publish your local commits)
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   playground
````
As you can see in the git status I modified the playground file. So lets see what I did there.
````diff
[14:13]git@gitexample~/Documents/GitHub/github-tutorial# git diff playground
diff --git a/playground b/playground
index c187135..b5b8618 100644
--- a/playground
+++ b/playground
@@ -1,4 +1,4 @@
 This is a file you can play around with...
 Have a lot of fun
 
-foobar
\ No newline at end of file
+This is code or text or..
````
I replace the line **foobar** with **This is code or text or..**

### Git checkout (Revert (SVN wording) a file or branch)
Lets say you did some changes you don't like anymore. So you want to revert your file back to the original file again.

In this case I want my **foobar** line in the playground file back and remove the **This is code or text or..** stuff.
So we type
````
git checkout playground
````

````
[14:22]git@gitexample~/Documents/GitHub/github-tutorial# git status
On branch master
Your branch is up-to-date with 'origin/master'.

nothing to commit, working directory clean
````

As you can see in **git diff** my changes are gone and the **playground** file is not marked as changed anymore.

### Git branch
Git is able to create branches. This is basicly the same than create a folder "Final", "Final_1", "Realy_final_now" to save different version of development but its handled by git itself.

By default git will create you a branch called **master**. **Usually you will never work in master branch!**

You can check your current branch with the command **git branch**
````
[14:25]git@gitexample~/Documents/GitHub/github-tutorial# git branch
* master
````
At the moment there is only the master branch. It is flagged with a ** * ** because it is the active branch at the momen.

#### Create a new branch
Please create new a new branch with the command **git branch <name>**
````
git branch daniel
````

If you type in **git branch** you see ther is a new on:
````
[14:25]git@gitexample~/Documents/GitHub/github-tutorial# git branch
  daniel
* master
````

#### Change to the new branch (Checkout)
You can jump betwen your branches by type **git checkout <branch name>**
````
[14:26]git@gitexample~/Documents/GitHub/github-tutorial# git checkout daniel
````

````
[14:26]git@gitexample~/Documents/GitHub/github-tutorial# git branch
* daniel
  master
````
As you can see, now the branch called **daniel** is tagged with the ** * ** and is the active branch now.

#### Rename a local branch
````
git branch -m <old name> <new name>
````

### Commit changes to your local repository
Please change your playground file now and leave me a notice if you like this tutorial or not - or so...

If you are done run the commands git status and git diff to check your changes...

To commit your changes you can use the command **git commit -a -m "Some message"**

This command will add your changes to the command and you are able to type in a commit message.
````
[14:27]git@gitexample~/Documents/GitHub/github-tutorial# git commit -a -m "Update playground"
[daniel 5b842ce] Update playground
 1 file changed, 62 insertions(+), 1 deletion(-)
````

### Push changes to GitHub (Commit in SVN)
With git all the commits your do are just localy on your maschine. To publish or backup them on GitHub, you need to push the changes.

To push your local repository to the remote GitHub servers type **git push origin <branch name>**

````
[14:39]git@gitexample~/Documents/GitHub/github-tutorial# git push origin daniel
Total 0 (delta 0), reused 0 (delta 0)
To https://github.com/it-novum/github-tutorial.git
 * [new branch]      daniel -> daniel
[14:39]dziegler@daniels-mbp~/Documents
````
As you can see, your changes are now available on GitHub.

#### Push changes to GitHub with a different branch name
````
git push origin <local name>:<remote name>
````

### Pull changes from GitHub to my local machine (SVN update)
Usually you are only update your local **master** branch

Change to the master branch (git checkout master) and type in **git pull**.

### Merge remote master to your local branch
In some cases you need to update your local branch to remote master because you need a feature, function or method someone else developed.

First of all, push all your changes to GitHub to create a backup!
````
git rebase master
````

If you have any conflicts please solve them.
You are resolving a conflict by editing the conflicted file and merge it with your hands :-)

After you solved the conflicts you need to add the files
````
git add path/to/conflicted/file
````
and continue with the rebase
````
git rebase --continue
````

# Did I missed something?
You are welcome to extend this README :-)

# License
MIT License