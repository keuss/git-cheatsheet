# git-cheatsheet
Some basic &amp; usefull git commands

## Repository creation, clone & 101

- `git init <directory>` : transform the current directory into a Git repository. This adds a .git folder to the current directory and makes it possible to start recording revisions of the project.
- `git clone <repo> <directory>` : clone the repository into the folder on the local machine (makes a git repositpry copy from a remonte source).
- `git stauts` : lists all new or modified files to be commited.
- `git log` : viewing the commit history.
- `git diff --staged` : shows file differences between staging and the last file version.
- create a new repository on the command line (The -u option is for "Upstream" and automatically sets that upstream for you) :

```
echo "# MyProject" >> README.md
git init
git add README.md
git commit -m "my first commit"
git remote add origin url.git
git push -u origin master
```

 - `git config --global --edit` : edit the global config file

## Saving changes & resetting

- `git add <file> or <directory>` (example : ` git add app/src/test.txt` or `git add .`) : adds a change in the working directory to the staging area. It tells Git that you want to include updates to a particular file in the next commit.
- `git reset --hard` : resets your index and working directory to the state of your last commit (reset HEAD, index and working tree). Any changes to tracked files in the working directory since your last commit are discarded. Opposite of git add.
- `git reset --keep` : remove files from the staging area, but leave the working directory unchanged (reset HEAD but keep local changes).
- `git reset -- <file>` : remove the specified file from the staging area, but leave the working directory unchanged.
- `git commit -m <message>` : the staged snapshot is committed to the project history.
- `git commit -am <message>` : the staged snapshot is committed to the project history + git add for the already tracked files.
- `git reset --hard HEAD^` : to undo a local commit + resets your index and working directory.
- `git reset --soft HEAD^` : to undo a local commit + but leaving the working directory state unchanged

## Synchronization

- `git fetch` : fetches all the objects (files, branch, ...) from the remote repository that are not present in the local one (example `git fetch origin`).
- `git pull` : fetches the files from the remote repository and merges it with your local one (git fetch + git merge), example `git pull origin master`.
- `git push` : Pushes all the modified local objects to the remore repository, example `git push origin master`.

## Branch management

- `git branch -a` : show all branch.
- `git branch -r` : show remote branch.
- `git checkout <existing-branch>` : check out the specified branch.
- `git checkout -b <new-branch>` : create and check out new-branch.
- `git push -u origin <new-branch>` : pushes new-feature to the central repository (origin), and the -u flag adds it as a remote tracking branch. After setting up the tracking branch, git push can be invoked without any parameters to automatically push the <new-branch> branch to the central repository
- `git merge <branch>` : merge the specified branch into the current branch. Git will determine the merge algorithm automatically.
- `git merge --no-ff <branch>` : merge the specified branch into the current branch, but always generate a merge commit (even if it was a fast-forward merge). This is useful for documenting all merges that occur in your repository.
- `git branch -d <branch>` or `git branch -D <branch>` : delete Local Branch
- `git push <remote> --delete <branch>` : delete Remote Branch (example : `git push origin --delete feature/5073-explo`

## Tag management

- `git tag` : list all tags.
- `git tag -a <tagname> -m "<tagcomment>"` : create tag.
-	`git push origin --tags` : push tags.
- `git checkout -b <branchname> <tagname>` : checking out tag in branch, example `git checkout -b version2 v2.0.0`.

## Remote

- `git remote -v` : see what url belongs to each remote by using (origin is an alias on your system for a particular remote repositor, it is a local alias set as a key for the remote repository URL). Remotes are simply an alias that store the url of repositories. You can see what url belongs to each remote by using the command.
- `git remote get-url origin` : display url of the repo
- `git remote set-url origin <newurl>` : set new url

## Misc

- What is `origin` : origin is an alias on your system for a particular remote repository. It's not actually a property of that repository (see [here](http://stackoverflow.com/questions/9529497/what-is-origin-in-git)).
- What is `HEAD` : you can think of the HEAD as the "current branch. "HEAD" (uppercase) refers exclusively to the currently active head (see [here](http://stackoverflow.com/questions/2304087/what-is-head-in-git)). HEAD always refers to the most recent commit on the current branch. When you change branches, HEAD is updated to refer to the new branch’s latest commit.

## .gitconfig

WIP ...

## Links

- https://gist.github.com/JamesMGreene/cdd0ac49f90c987e45ac
- https://services.github.com/on-demand/downloads/github-git-cheat-sheet.pdf
- https://confluence.atlassian.com/bitbucketserver/basic-git-commands-776639767.html
