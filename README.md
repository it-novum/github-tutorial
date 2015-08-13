This is a quick start guide for developers that are interested in learning git
# Install git on your maschine
Ubuntu and Debian:
````
apt-get install git
````

Mac OS X
On Mac OS you need to download [Xcode](https://itunes.apple.com/de/app/xcode/id497799835?mt=12) from the Mac App Store

# Should I use a GUI or the command line?
A nice and easy to use GUI is the [GitHub for Windows](https://desktop.github.com/) or [GitHub for Mac](https://desktop.github.com/) but i recommend to use the command line. It's very easy and fast!

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
