Hey guys! These are the commands I'll be using in the screencast. Do follow along with me. And ask if you have any doubts!

Initialize a git repo
```bash
git init
```

View status of the repository
```bash
git status
```

*Create a new file named 'new.txt'*

Now view status again.
```bash
git status
```

Add the new file.
```bash
git add new.txt
```

View status again
```bash
git status
```

Now commit the addition of the new file.
git commit -m "Message describing change eg. Added file new"

View history
```bash
git log
```

*Add some content onto new.txt*

Observe the status message.
```bash
git status
```
Follow same workflow - Add and commit.

```bash
git add new.txt
git commit -m "Content to new.txt"
git log
```

Now try this command.
```bash
git branch
```
The output will look like '* master'. This means you are on the 'master' branch. 
While developing, a good practice is to create a branch for a feature or change, work on that branch and once you are done merge it back to master!
This way your master branch will remain 'clean'!

Create a new branch
```
git branch newBranch
```

Switch to that branch
```bash
git checkout newBranch
```

*Now add one more line to the new.txt file, and follow the same workflow*
```bash
git add .
git commit -m "Added second line"
git log
```
Hint: See how I did 'git add .'? This is a shortcut that adds all files! 

Now try switching back to master and viewing the log.
```bash
git checkout master
git log
```
You'll see that it doesn't have the last commit we made in 'newBranch'. Now, we need to merge these two branches. 

To merge, we need to switch to master and run the following command.
```bash
git checkout master
git merge newBranch
```

Check the log! You'll see that the commit we made in 'newBranch' has appeared here! new.txt has also been updated with the new content.

Now that we are done with the branch, let's delete it off.
```bash
git branch -d newBranch
```

While merging two branches, we may also run into conflicts. Let's illustrate this.

Make a branch 'conflictBranch'.
Now on master, add a line to new.txt and commit it.
Checkout to conflictBranch, and add a line with different content and commit that.
Now try to merge these 2 branches.

The merge will fail and will ask you to fix conflicts! Fear not! This is not as hard as it sounds. Open up the new.txt file. You'll see some new things have appeared. The lines between the line where <<<.. HEAD and ====... appears is the content that is present on the current branch. The lines from ==... to <<<<<.. *branch_name* is the content in the branch that is trying to be merge.

Just remove the things you dont need and after this just add the file and commit it! 

Another good practice is to commit often. Think of Hansel and Gretel leaving breadcrumbs! Your commits are these breadcrumbs. They let you go back to a point in history! To do this:

```bash
git reset <first 5 char of the commit hash you want to go back to> 
```
'git reset' alone will set it back to the latest commit. 

The git reset command just clears your staging area. If you want to set your file contents also back to that point, use 'git reset --hard'.

The commit hash is the huge number you see next to commit when you type git log.

If you're here, then you've got a working knowledge of git. Now, this is just a basic tutorial.
Git has a lot more amazing features, which I'll leave to you to explore and find out!

#Remotes

So till now we were working with only one copy on our system right? But usually we store one copy of this on a remote server and then maintain both remote and local repositories. [GitHub](https://github.com) is a site which lets you host your repositories for free. You can also use [BitBucket](https://bitbucket.org/). For this exercise, we will be using GitHub.

So now think of having 2 copies. One on your machine and one on a server. There are 2 git commands that let us synchronise these 2 copies. 
 
'git push'  pushes the content from your local repo to the remote one.
'git pull' will fetch the content from the remote repo and attempt to merge it with your local repo.

Do look up forking, cloning and pull requests. GitHub explains them pretty well.

So now as exercise, fork this repository, clone it, and then inside the about folder, create a file with your name, describe yourself in the contents, add and commit, push to your fork and then issue a pull request! 
