# Delete old master branch and create new from scratch

>>This will create a new master branch pointing to initial commit:

git branch -D master
git checkout -b master <initial commit hash>

>>This will create a totally new master branch unrelated to whatever you had:

git branch -D master
git checkout --orphan master
git rm -rf *
But actually you can simply save current repository to some other place and create a new repository instead.


# Adding only unstaged file changes 

git add -u

# Git: Delete a branch (local or remote)

>> To delete a local branch

git branch -d the_local_branch


>>To remove a remote branch (if you know what you are doing!)

git push origin :the_remote_branch
or
git push origin --delete the_remote_branch

# I don't have master in my local but my repository does, and I want to switch to master.

git checkout -t -b master origin/master


# Remove history of the branch and create initial commit

Note: 
It also removes the configuration of the repository.
This does NOT work if the repository has submodules! If you are using submodules, you should use e.g. interactive rebase

Step 1: remove all history (Make sure you have backup, this cannot be reverted)

rm -rf .git

Step 2: reconstruct the Git repo with only the current content

git init
git add .
git commit -m "Initial commit"

Step 3: push to GitHub.

git remote add origin <github-uri>
git push -u --force origin master
