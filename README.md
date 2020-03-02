# git-cheatsheet
Common and/or useful Git commands

#### Info on branches
```bash
# see branches that have been merged and can be cleaned up 
$ git branch --merged 

# see all branches local and remote 
$ git branch -a 
```

#### Checkout a branch/commit/tag from local or another host
```bash
# checkout to a commit, branch, or tag
$ git checkout [COMMIT_OR_BRANCH_OR_TAG] 

# checkout to the previously fetch remote version of master
$ git checkout origin/master  

# create a new branch and check it out at the same time
$ git checkout -b branch-name 

# toggle between previous checked out branch
$ git checkout -  

# create new branch based on fetched remote master 
$ git checkout -b MY_NEW_BRANCH origin/master 
```

#### More on branches
```bash
# rename a branch
$ git branch -m old-name new-name 

# delete a local branch
$ git branch -d branch_name 

# force delete a local branch (make sure you want to delete it)
$ git branch -D branch_name 

# delete a remote branch
$ git push origin --delete branch_name 
```

#### Committing your changes to your current local branch
```bash
# add a new file; must do this before commit
$ git add my_new_file.txt 

# stage and commit all modified files 
$ git commit -a -m "commit message"   
 
# Commit a single file
$ git commit path/to/my/file.ext -m "commit message"
 
# Update the last commit message. Useful when you forget to update or mess up the commit message
$ git commit --amend -m "New commit message" 

# show last commit
$ git log -1 
```
   
#### Working with the latest code from origin
```bash
# fetch any changes, but don't merge
$ git fetch origin     

# merge the remote changes previously fetched
$ git merge origin/master  

# push your current branch to same name at remote
$ git push origin HEAD  

# push a specific local branch (not current branch) at remote
$ git push origin branch-name 
```

####  Differences, merging ancestors, rebase
```bash
# compare differences
$ git diff [COMMIT_OR_BRANCH1] [COMMIT_OR_BRANCH2]

# compare current local branch with remote BRANCH_NAME  
$ git diff origin/[BRANCH_NAME] 

# Compare changes in locally modified file to last commit (in current local branch)
$ git diff -- myfile.xyz

# find common ancestor
$ git merge-base BRANCH1 BRANCH2  

# rebase current branch onto origin/master starting with COMMIT
$ git rebase --onto origin/master [COMMIT] 

# determine ancestor and use it for rebase
$ git rebase --onto BRANCH_OR_COMMIT1 --fork-point BRANCH_OR_COMMIT1
  
# allows you to squash, reorder, or omit commits, along with updating commit messages
$ git rebase -i [COMMIT]  
```

#### What's in a specific commit
```bash
# show diff of what changed in this commit 
$ git show COMMIT 
```

#### Look at history (git log ...)
```bash
# show signed commits 
$ git log --show-signature 

# limit log of commits that changed these files
$ git log -- [FILE_OR_DIR_PATH]

# show branch and merges  
$ git log --graph  

# show inserts/deletes for files
$ git log --compact-summary

# show only 8 char commit and first line of commit message  
$ git log --oneline  
```

#### Save for later/retrieve it (git stash ...)
```bash
# save changed files for potential later use, resets them to HEAD
$ git stash save [MSG]  

# reapply changes from last stash
$ git stash pop  
```

#### Do-overs
```bash
# reset changed files to what is in last commit
$ git reset --hard HEAD  

# undo last commit, resetting files to status before the commit
$ git reset HEAD~1 

# reset a single file
$ git checkout filename
```  

#### Tags
```bash
# 2 Commands that shows all tags applied on remote
$ git fetch --tags # Command 1 of 2
$ git tag # Command 2 of 2

# Delete local tag
$ git tag -d [TAG_NAME]  

# delete remote tag
$ git push origin :refs/tags/[TAG_NAME] 

# Create a new branch at a specific tag
$ git checkout -b [BRANCH_NAME] [TAG_NAME] 
```

#### Bisect to iterate commits
```bash
# helps you iterate through commits in binary search style to find problem
$ git bisect [BAD_COMMIT] [GOOD_COMMIT]  
```

#### Merge changes from a specific commit into your current branch
```bash
# apply just the changes in this commit to your current local branch
$ git cherry-pick [COMMIT]  
```
