# git-cheatsheet
Some basic &amp; usefull git commands

## Repository creation, clone & 101

- `git init <directory>` : transform the current directory into a Git repository. This adds a .git folder to the current directory and makes it possible to start recording revisions of the project.
- `git clone <repo> <directory>` : clone the repository into the folder on the local machine (makes a git repositpry copy from a remonte source).
- `git stauts` : lists all new or modified files to be commited.
- `git log` : viewing the commit history.
- `git diff --staged` : shows file differences between staging and the last file version.

## Saving changes & resetting

- `git add <file> or <directory>` (example : ` git add app/src/test.txt` or `git add .`) : adds a change in the working directory to the staging area. It tells Git that you want to include updates to a particular file in the next commit.
- `git reset --hard` : resets your index and working directory to the state of your last commit (reset HEAD, index and working tree). Any changes to tracked files in the working directory since your last commit are discarded. Opposite of git add.
- `git reset --keep` : remove files from the staging area, but leave the working directory unchanged (reset HEAD but keep local changes).
- `git reset -- <file>` : remove the specified file from the staging area, but leave the working directory unchanged.
- `git commit -m <message>` : the staged snapshot is committed to the project history.
- `git commit -am <message>` : the staged snapshot is committed to the project history + git add for the already tracked files.
- `git reset --hard HEAD^` : to undo a local commit + resets your index and working directory.

## Synchronization

 - `git fetch` : fetches all the objects from the remote repository that are not present in the local one (example `git fetch origin`).

## Branch management

- `git branch -a` : show all branch.
- `git branch -r` : show remote branch.
- `git checkout <existing-branch>` : check out the specified branch.
- `git checkout -b <new-branch>` : create and check out new-branch.
- `git merge <branch>` : merge the specified branch into the current branch. Git will determine the merge algorithm automatically.
- `git merge --no-ff <branch>` : merge the specified branch into the current branch, but always generate a merge commit (even if it was a fast-forward merge). This is useful for documenting all merges that occur in your repository.

## Tag management

- `git checkout -b version2 v2.0.0` : checking out tag in branch

## Remote

- `git remote -v` : see what url belongs to each remote by using (origin is an alias on your system for a particular remote repositor, it is a local alias set as a key for the remote repository URL).
- `git remote get-url origin` : display url of the repo
- `git remote set-url origin <newurl>` : set new url

## Misc

## .gitconfig

WIP ...

## Links

- https://gist.github.com/JamesMGreene/cdd0ac49f90c987e45ac
- https://services.github.com/on-demand/downloads/github-git-cheat-sheet.pdf
- https://confluence.atlassian.com/bitbucketserver/basic-git-commands-776639767.html
