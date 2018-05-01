Git CheatSheet

##Clone to folder
git clone remote_repo_url local_name


##To create a local branch
>>git branch ---> shows curr_branch
>>git checkout -b my_new_branch_copy_off_curr_branch
>>git branch ---> my_new_branch_copy_off_curr_branch


##delete local branch
Move to some other branch
git branch -d the_local_branch_name_to_be_deleted

##To see logs of different branch:
>>git log [branch_name] ----- if we dont specify branch, it will pick the current, else it will show logs of branch specified


##If you want to pick commit in some feature branch and want to merge it in master.
##cherry-picking
suppose we are on master:
git branch -----> master
git log ft-branch -------> will show log...and you can find sha1 hash of commit on ft branch..say abcdefghij123
git cherry-pick abcdefghij123  ------> this will merge the commit from ft branch to master.


---another way to cherrypick
#br3 is branch checked out of br2
git branch --> br1
git cherry-pick origin/br2..br3 ------> This will pick all the checkins that have been made in the br3 branch since it has been branchedout of br2 and will merge into br1


##To check whether commit exist in branch
git branch --contains SHA1

##squash your commits
Supoose you want to squash last n commits:
git rebase -i HEAD~5
Then it will open editor.
will show:
pick 5
pick 4
pick 3
pick 2
pick 1

suppose i want to squash all in 1
replace pick with squash
squash 5
squash 4
squash 3
squash 2
pick 1
 It will have all the commits with commit of 1.
 
 ##Clean all the things::
git clean -d -n -x
                -n shows what would be removed without doing it
git clean -d -f -x
                -d removes directories too
                -f is force
                -x removes .gitignore files as well (build products)
                
##The many ways to make a patch:
git format-patch -1 392a0ea071e054612d02232de7b3d2a2b7e9c1d8
git diff HEAD HEAD~3 > my.patch


##Reset branch to remote:
git fetch origin
git reset --hard origin/master
note: throws out any commits you have that aren’t pushed, be careful!


##Amend last commit by adding/changing old file into last commit:
Suppose you made a commit.
Now we have changed another file but want to commit under last commit.
git add file-changed
git commit --amend.

It will open editor with last. You can amend the commit statement of just save it.
The new change is under the last commit itself.


##How to find logs by one user only::
git log --author=name

##to find log of one user on particular branch
git log --author=name [branch-name]

## apply patch
git diff > difffile
and to apply the diff > git apply difffile

##If nothing has changes except the file permissions, and you want to ignore in git status, use
"git config core.fileMode false".

##Reverting your last commit
git revert hash_of_commit

##How can one change the timestamp of an old commit in Git?
git commit --amend --date="Wed Feb 16 14:00 2011 +0100"

