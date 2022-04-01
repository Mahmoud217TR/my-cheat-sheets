# Git in General

**Table of Contents:**
* [Initialize](#initialize)
* [Staging Area](#staging-area)
* [Status](#status)
* [Commits](#commits)
* [Branches](#branches)
* [Repos](#repos)
* [Deleting](#deleting)

## Initialize

- Initilizing a repository `git init`.


## Staging Area

- Adding a files: to staging area: `git add <file>`.

- Adding all files to staging area: `git add .`. 
		
- Removing a file from staging area `git rm --cached <file>` or `git restore <file>`


## Status

Checking tracked or untracked files `git status`.


# Commits 

- Making a new commit `git commit -m <message>`

- Adding everything to staging area and commiting `git commit -am <message>`.


# Branches

- Switching to a branch `git checkout <branch>`.

- Switching to a **new** branch `git checkout -b <branch>`.
		
- Get all branchs `git branch`.
		
- To merge another branch with the current branch `git merge extended`.
		
- Renaming a branch:
	- Go to the brach you want to rename it `git checkout -b <branch>`.
	- Change the branch name `git branch -M <branch>`.
		

# Repos

- Adding a remote repository `git remote add origin <url>`.
		
- Checking the remote repositories `git remote`.
		
- Pushing changes to remote repository `git push -u <repo> <branch>`.
		
- Pulling Changes `git pull`.
		
- Clone a project `git clone <url>`.


# Deleting

- Removing a file form repo `git rm <file>`

- Removing a folder form repo `git rm <folder> -r`