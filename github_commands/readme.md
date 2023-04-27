# Basic Commands

Level 1:

Working Directory ---> Staging Area ---> Local Repo  |  Remote Repo

git add
git commit
git push

git fetch
git merge
git pull
git clone
git checkout


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

Error: Failed to push some references to:
$ git fetch

$ git merge origin/your-branch-name
$git push

Recover From hard reset:

$ git reflog

## References
https://medium.com/geekculture/git-useful-tips-part-one-1ad2dbdab7bf
