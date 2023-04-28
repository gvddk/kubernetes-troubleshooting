# Basic Commands

Level 1:

Working Directory ---> Staging Area ---> Local Repo  |  Remote Repo
````
git add
git commit
git push

git fetch
git merge
git pull
git clone
git checkout
````

Level 2:

Check recent commit:
git show

Update commit message:

git commit --ammend --only -m "Text"

Update username and email:
$ git commit --amend --author="New Author Name <new.author@example.com>"


Remove Specific File From Last Commit:
$ git reset HEAD^ path/to/your-file.ext
$ git commit --amend --no-edit

The --no-edit option ensures that the commit message remains unchanged.

Delete Last Pushed Commit:
git reset HEAD^ --hard 

Here is a break down of the reset:
````
git reset: The reset command is used to reset the current HEAD (the tip of the current branch) to a specified state.
HEAD^: This is a shorthand reference to the parent commit of the current HEAD. HEAD refers to the current commit, and the ^ character points to its parent.
In this case, you're telling Git to reset the current branch to the previous commit.

--hard: This option tells Git to perform a "hard" reset, which means that it will discard all changes in the working directory and staging area since 
the specified commit. This is in contrast to a "soft" reset (--soft), which keeps changes in the working directory and staging area, or a "mixed" reset 
(default behavior, no flag), which keeps changes in the working directory but unstages them.
```
Error: Failed to push some references to:
This error occurs when you try to push your local changes to a remote repository, but the remote branch has commits that you don’t have in your local branch.

$ git fetch

$ git merge origin/your-branch-name
$git push

Recover From hard reset:

$ git reflog

## References
https://medium.com/geekculture/git-useful-tips-part-one-1ad2dbdab7bf
