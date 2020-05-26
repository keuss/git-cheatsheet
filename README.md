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
 - `git config --global core.autocrlf true` : Checkout Windows-style, commit Unix-style

## Saving changes & resetting

- `git add <file> or <directory>` (example : ` git add app/src/test.txt` or `git add .`) : adds a change in the working directory to the staging area. It tells Git that you want to include updates to a particular file in the next commit.
- `git reset --hard` : resets your index and working directory to the state of your last commit (reset HEAD, index and working tree). Any changes to tracked files in the working directory since your last commit are discarded. Opposite of git add.
- `git reset --keep` : remove files from the staging area, but leave the working directory unchanged (reset HEAD but keep local changes).
- `git reset -- <file>` : remove the specified file from the staging area, but leave the working directory unchanged.
- `git commit -m <message>` : the staged snapshot is committed to the project history.
- `git commit -am <message>` : the staged snapshot is committed to the project history + git add for the already tracked files.
- `git reset --hard HEAD^` : to undo a local commit + resets your index and working directory.
- `git reset --soft HEAD^` : to undo a local commit + but leaving the working directory state unchanged
- `git commit --amend` : update last commit message
- `git stash` : when you want to record the current state of the working directory and the index, but want to go back to a clean working directory. The command saves your local modifications away and reverts the working directory to match the HEAD commit. `git stash pop` to come back

## Synchronization

- `git fetch` : fetches all the objects (files, branch, ...) from the remote repository that are not present in the local one (example `git fetch origin`).
- `git pull` : fetches the files from the remote repository and merges it with your local one (git fetch + git merge), example `git pull origin master`.
- `git pull --rebase` : rebase mode (example `pull --rebase origin develop`). Perfome git fetch + git rebase against tracking upstream branch. To set this mode by default `git config --global pull.rebase true`
- `git push` : Pushes all the modified local objects to the remore repository, example `git push origin master`.

## Branch management

- `git branch -a` : show all branch.
- `git branch -r` : show remote branch.
- `git checkout <existing-branch>` : check out the specified branch.
- `git checkout -b <new-branch>` : create and check out new-branch.
- `git push -u origin <new-branch>` : pushes new-feature to the central repository (origin), and the -u flag adds it as a remote tracking branch. After setting up the tracking branch, git push can be invoked without any parameters to automatically push the <new-branch> branch to the central repository
- `git merge <branch>` : merge the specified branch into the current branch. Git will determine the merge algorithm automatically.
- `git merge --no-ff <branch>` : merge the specified branch into the current branch, but always generate a merge commit (even if it was a fast-forward merge). This is useful for documenting all merges that occur in your repository.
- `git branch -d <branch>` or `git branch -D <branch>` : delete Local Branch (must checkout branch once)
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

## Conflicts

- 1/ Solve merge conflict(s) (here without tool)
- 2/ `git add <filename>` to mark the file as resolved by hand (for each files)
- 3/ `git commit` 

- `git merge --abort` : undo a merge
- `git reset --hard` : to start over again
- `git merge --strategy-option theirs <branchname>` : merge branchname in current branch with the recursive "theirs" strategy option

```
ours
    This option forces conflicting hunks to be auto-resolved cleanly by 
    favoring our version. Changes from the other tree that do not 
    conflict with our side are reflected to the merge result.

    This should not be confused with the ours merge strategy, which does 
    not even look at what the other tree contains at all. It discards 
    everything the other tree did, declaring our history contains all that
    happened in it.

theirs
    This is opposite of ours.
```

## Misc

- What is `origin` : origin is an alias on your system for a particular remote repository. It's not actually a property of that repository (see [here](http://stackoverflow.com/questions/9529497/what-is-origin-in-git)).
- What is `HEAD` : you can think of the HEAD as the "current branch. "HEAD" (uppercase) refers exclusively to the currently active head (see [here](http://stackoverflow.com/questions/2304087/what-is-head-in-git)). HEAD always refers to the most recent commit on the current branch. When you change branches, HEAD is updated to refer to the new branch’s latest commit.

## .gitconfig

Alias :

```
[alias]
	co = checkout
	br = branch
	st = status
	last = log -1 HEAD
	ci = commit
	gdiff = diff-tree --no-commit-id --name-only -r
	gdesc = log -1 --pretty='%H (%cn on %cD) %s'
	lg = log --graph --all --date-order --pretty=tformat:'%Cred%h%Creset -%C(auto)%d%Creset %s %Cgreen(%an %ar)%Creset'
	lgb = log --graph --date-order --pretty=tformat:'%Cred%h%Creset -%C(auto)%d%Creset %s %Cgreen(%an %ar)%Creset'
	glog = log --decorate --oneline --graph --all
	graph = log --graph --all --format=format:'%C(cyan)%h%C(reset) - %C(green)(%ar)%C(reset) %C(black)%s%C(reset) %C(blue)? %an%C(reset)%C(yellow)%d%C(reset)' --abbrev-commit --date=relative
	oops = commit --amend --no-edit
	wdiff = diff --word-diff --color-words=. --word-diff-regex=.
 ```
 
Proxy and SSL verify false :

```
[http]
	sslVerify = false
	proxy = <host:port>
```

## Links

- https://gist.github.com/JamesMGreene/cdd0ac49f90c987e45ac (A comparison of using `git flow` commands versus raw `git` commands.)
- https://confluence.atlassian.com/bitbucketserver/basic-git-commands-776639767.html
- https://www.atlassian.com/git/tutorials/comparing-workflows/feature-branch-workflow
- Merge & Rebase : https://delicious-insights.com/fr/articles/bien-utiliser-git-merge-et-rebase/
