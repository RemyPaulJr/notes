Command Commands:
- Setting up and configuring a repo:
	- git init: initialize a new git repo
	- git confg: set config values for user info, aliases, etc
- Basic Commands:
	- git clone <repo>: Clone (or download) a repo from an existing URL
	   - git status: check status of your changes in the working directory
	   - git add <filename>: add changes in the file to the staging area
		   - git add .: add all new and changed files to the staging area
	   - git commit -m "commit message": commit the staged changes with a message
	   - git log: view commit logs
Branching
- git branch: list all local branches
	- git branch <branchname>: switch to a specific branch
- git checkout <branchname>: switch to a specific branch
	- git checkout -b <branchname>: create a new branch and switch to it
- git merge <branchname>: merge the specified branch into the current branch
- git branch -d <branchname>: delete a branch
Remote Repo
- git remote add <name><url>: add a remote repo
- git remote: list all remote repos
- git push <remote><branch>: push a branch to a remote repo
- git pull <remote><branch>: pull changes from a remote repo branch into the current local branch
Undoing changes
- git reset: reset your staging area to match the most recent commit, without affecting the working directory
- git reset --hard: reset the staging area and the working directory to match the most recent commit
- git revert <commit>: create a new commit that undoes all of the changes from a previous commit.
Advanced git
- git stash: temp save changes that are not yet ready for a commit
	- git stash pop: restore the most recently stashed changes
- git rebase <branch>: reapply changes from one branch onto another, often used to integrate changes from one branch into another
- git cherry-pick <commit>: apply changes from a specific commit to the current branch
Git collab and inspection
- git blame <file>: show who made changes to a file and when
- git diff: show changes between commits, commit and working tree, etc.
- git fetch: fetch changes from a remote repo without merging them
Git maintenance and data recovery
- git fsck: check the database for errors
- git gc: clean up and optimize the local repo
- git reflog: record when refs were updated in the local repo, useful for recovering lost commits