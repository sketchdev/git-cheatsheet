# git-cheatsheet
Common and/or useful Git commands

#### Info on branches
```bash
# see branches that have been merged and can be cleaned up 
$ git branch --merged 

# see all branches local and remote 
git branch -a 
```

#### Checkout a branch/commit/tag from local or another host
```console
# checkout to a commit, branch, or tag
$ git checkout [COMMIT_OR_BRANCH_OR_TAG] 

# checkout to the previously fetch remote version of master
git checkout origin/master  

# create a new branch and check it out at the same time
git checkout -b branch-name 

# toggle between previous checked out branch
git checkout -  

# create new branch based on fetched remote master 
git checkout -b MY_NEW_BRANCH origin/master 
```

#### More on branches
* git branch -m old-name new-name # rename a branch
* git branch -d branch_name # delete a local branch
* git branch -D branch_name # force delete a local branch (make sure you want to delete it)
* git push origin --delete branch_name # delete a remote branch

#### Committing your changes to your current local branch
* git add my_new_file.txt # add a new file; must do this before commit
* git commit -a -m "commit message" # stage and commit all modified files    
* git commit path/to/my/file.ext -m "commit message" # Commit a single file
* git commit --amend -m "New commit message" # Update the last commit message. Useful when you forget to update or mess up the commit message
* git log -1 # show last commit
   
#### Working with the latest code from origin
* git fetch origin # fetch any changes, but don't merge    
* git merge origin/master  # merge the remote changes previously fetched  
* git push origin HEAD # push your current branch to same name at remote 
* git push origin branch-name # push a specific local branch (not current branch) at remote

####  Differences, merging ancestors, rebase
* git diff [COMMIT_OR_BRANCH1] [COMMIT_OR_BRANCH2] # compare differences 
* git diff origin/[BRANCH_NAME] # compare current local branch with remote BRANCH_NAME
* git merge-base BRANCH1 BRANCH2 # find common ancestor 
* git rebase --onto origin/master [COMMIT] # rebase current branch onto origin/master starting with COMMIT 
* git rebase --onto BRANCH_OR_COMMIT1 --fork-point BRANCH_OR_COMMIT1 # determine ancestor and use it for rebase 
* git rebase -i [COMMIT] # allows you to squash, reorder, or omit commits, along with updating commit messages 

#### What's in a specific commit
* git show COMMIT # show diff of what changed in this commit 

#### Look at history (git log ...)
* git log --show-signature # show signed commits 
* git log -- [FILE_OR_DIR_PATH] # limit log of commits that changed these files 
* git log --graph # show branch and merges 
* git log --compact-summary # show inserts/deletes for files 
* git log --oneline # show only 8 char commit and first line of commit message 

#### Save for later/retrieve it (git stash ...)
* git stash save [MSG] # save changed files for potential later use, resets them to HEAD 
* git stash pop # reapply changes from last stash 

#### Do-overs
* git reset --hard HEAD # reset changed files to what is in last commit 
* git reset HEAD~1 # undo last commit, resetting files to status before the commit
* git checkout filename # reset a single file 

#### Tags
* git fetch --tags # Command 1 of 2
* git tag # Command 2 of 2 to see all tags applied on remote
* git tag -d [TAG_NAME] # Delete local tag 
* git push origin :refs/tags/[TAG_NAME] # delete remote tag
* git checkout -b [BRANCH_NAME] [TAG_NAME] # Create a new branch at a specific tag

#### Bisect to iterate commits
* git bisect [BAD_COMMIT] [GOOD_COMMIT] # helps you iterate through commits in binary search style to find problem 

#### Merge changes from a specific commit into your current branch
* git cherry-pick [COMMIT] # apply just the changes in this commit to your current local branch 
