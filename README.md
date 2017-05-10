# git-cheatsheet
Some basic &amp; usefull git commands

## Repository creation & clone

## Saving changes & resetting

- `git add <file> or <directory>` (example : ` git add app/src/test.txt` or `git add .`) : adds a change in the working directory to the staging area. It tells Git that you want to include updates to a particular file in the next commit.
- `git reset --hard` : resets your index and working directory to the state of your last commit (reset HEAD, index and working tree). Any changes to tracked files in the working directory since your last commit are discarded. Opposite of git add.
- `git reset --keep` : remove files from the staging area, but leave the working directory unchanged (reset HEAD but keep local changes).
- `git reset -- <file>` : remove the specified file from the staging area, but leave the working directory unchanged.
- `git commit -m <message>` : the staged snapshot is committed to the project history 
- `git commit -am <message>` : the staged snapshot is committed to the project history + git add for the already tracked files
- `git reset --hard HEAD^` : to undo a local commit + resets your index and working directory.

WIP ...

## Links

- https://gist.github.com/JamesMGreene/cdd0ac49f90c987e45ac
- https://services.github.com/on-demand/downloads/github-git-cheat-sheet.pdf
- https://confluence.atlassian.com/bitbucketserver/basic-git-commands-776639767.html
