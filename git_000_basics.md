# Git Basics

Git Cheat-Sheet

file:///C:/Users/hecto/Downloads/SWTM-2088_Atlassian-Git-Cheatsheet.pdf

## On initial install

- `git --version` - checks the version of the installed locally git

- `git config --global user.name "Your Name"` - sets up the name of the user 

- `git config --global user.email "yourname@somemail.eu" `- sets up the mail of the user

- `git config --list` - lists all the git configurations



#### For help on commands:

`git help <verb>` (e.g. git help config) OR 
`git <verb> --help` 

## General


- `git clone <url>` - the url can come from github
- `git status` - check status

## Add files

- `git add .` - adds all of the files for commiting, put it in the staging area
- `git add newFile.js` - adds specific file

## Remove files

- `git reset` - removes files from staging area (from green to red)
- `git reset newFile.js` - removes somefile.js from the staging area/commit preparation

## Committing

- `git commit -m "This is the commit message"` the files in the staging area are all committed (now if you do git status, you find that it is clean)

## Check log:

- `git log` - shows the commits (and infor: who committed, the message…) 


## View info about the repo:

- `git remote -v` - lists info about the repo
- `git branch -a` - lists all of the branches

- `git diff` - shows the difference made in files (you wrote ‘code calc.py’ changed ‘return x+y’ to ‘return x*y’ and pressed save, then in ‘git status’ it will tell you calc.py was modified, and git diff will show the changed returns)

## Pull before push ALWAYS:

- `git pull origin main` - pulls in the most recent project (the big main one)

Then Push:

- `git push origin main` - <origin> name of remote repo <master>/<main> the branch that we push to. (git push -u origin <name of the branch> - -u coordinates the two branches (local and on server))




## Branch

- `git branch branchName` - create a branch for desired feature (like fixing/creating a certain function/feature), 
- `git branch` - lists all the branches in repository ( the * is the branch you are currently on, use ‘checkout’ to move to another branch)
- `git checkout branchName`  - moves to that branch. Changes done in that branch don’t affect the main branch


- `git push -u origin branchName - mo`
- `git branch -a- mo`

### Merge a branch

- `git checkout main`
- `git pull origin main`

- `git merge branchName` - merge branch to main
- `git branch --merged` - see which branches are merged (before above merge command, you wouldn’t see it, but after ‘subtract’ shows up)

- `git push origin main `



### Delete a branch:

- `git branch -d branchName` - this deletes it locally (we don’t need a separate branch because there is one already merged with the main. So if you do ‘git branch’ you don’t see subtract anymore)
- `git branch -a` - check the repo branches 
- `git push origin --delete branchName` - this deletes it from the repo!
