# Github CheatSheet

**Table of Contents:**
* [Dealing with Github](#dealing-with-github)

## Dealing with Github
- Initilizing a repository `git init`.
		
- Add a file to staging area:
	- Adding a specific file `git add <file name>`.
	- Adding all Files `git add .`. 
		
- Remove a file from staging area `git rm --cached <file name>`.
	
- Checking tracked or untracked files `git status`.
		
- Making a new commit `git commit -m <message>`

- Adding everything to staging area and commiting `git commit -am <message>`.
		
- Switching to a branch `git checkout <branch name>`.

- Switching to a **new** branch `git checkout -b <branch name>`.
		
- Get all branchs `git branch`.
		
- To merge another branch with the current branch `git merge extended`.
		
- Renaming a branch:
	- Go to the brach you want to rename it `git checkout -b <branch name>`.
	- Change the branch name `git branch -M <new branch name>`.
		
- Adding a remote repository `git remote add origin <repo url>`.
		
- Checking the remote repositories `git remote`.
		
- Pushing changes to remote repository `git push -u <remote repository> <branch name>`.
		
- Pulling Changes `git pull`.
		
- Clone a project `git clone <repo url>`.
	
- Removing a file form repo `git rm <file path>`

- Removing a folder form repo `git rm <folder path> -r`