Commit: every time you commit, it basically takes a picture of what all your files look like at that moment and stores a reference to that snapshot

Repository: a directory which contains your project work, as well as a few files (hidden by default on Mac OS X) which are used to communicate with Git

Working Directory: the files that you see in your computer's file system. When you open your project files up on a code editor, you're working with files in the Working Directory

Checkout: when content in the repository has been copied to the Working Directory.

Staging Area / Staging Index / Index: a file in the Git directory that stores information about what will go into your next commit. You can think of the staging area as a prep table where Git will take the next commit. Files on the Staging Index are poised to be added to the repository

SHA: an ID number for each commi

Branch: when a new line of development is created that diverges from the main line of development. This alternative line of development can continue without altering the main line

---

git init

git clone

git status: display the current status of the repository

git log: display all of the commits of a repository, show SHA, author, date, message, use q to exit

git log --oneline: list one commit per line, show the first 7 characters of the SHA and message

git log --stat: display the files that have been modified, number of lines that have been added/removed, a summary line

git log -p: display the files that have been modified, location of the lines, actual changes that have been made

git log --oneline --decorate --graph: add the bullets and lines to the leftmost part of the output

git show <SHA>: show only one commit, default with -p

git add: move files from the Working Directory to the Staging, use .gitignore for files that do not want to be added

git commit: take files from the Staging Index and saves them in the repository
  
git commit --amend: alter the most-recent commit

git diff: see changes that have been made but haven't been committed

git tag -a TAG SHA: add a marker on a specific commit

git branch: list out the branches in a repository

git branch <name> <SHA>: create a new branch NAME at SHA, does not switch to the new branch

git branch -d <name>: delete branch, cannot delete a branch currently on

git checkout <name>: switch branch

git checkout -b <name>: create a new branch

git merge <other branch>: combine branches

git revert <SHA>: undo the changes that were made by the commit, create a new commit to record the change
  
git reset <reference-to-commit>: erase commit, move the HEAD and current branch pointer to the referenced commit, HEAD^ = HEAD~1 = parent commit
  
git reset --mixed <reference-to-commit>: default, move to working directory
  
git reset --soft <reference-to-commit>: move to staging

git reset --hard <reference-to-commit>: move to trash
  
  
  
