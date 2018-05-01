Git CheatSheet</br>
</br>
##Clone to folder</br>
git clone remote_repo_url local_name</br>
</br>

##To create a local branch
>>git branch ---> shows curr_branch</br>
>>git checkout -b my_new_branch_copy_off_curr_branch</br>
>>git branch ---> my_new_branch_copy_off_curr_branch</br>
</br>
</br>

</br>
##delete local branch</br>
Move to some other branch</br>
git branch -d the_local_branch_name_to_be_deleted</br>
</br>
##To see logs of different branch:</br>
>>git log [branch_name] ----- if we dont specify branch, it will pick the current, else it will show logs of branch specified</br>
</br>
</br>
##If you want to pick commit in some feature branch and want to merge it in master.</br>
##cherry-picking</br>
suppose we are on master:</br>
git branch -----> master</br>
git log ft-branch -------> will show log...and you can find sha1 hash of commit on ft branch..say abcdefghij123</br>
git cherry-pick abcdefghij123  ------> this will merge the commit from ft branch to master.</br>
</br>
</br>
---another way to cherrypick</br>
#br3 is branch checked out of br2</br>
git branch --> br1</br>
git cherry-pick origin/br2..br3 ------> This will pick all the checkins that have been made in the br3 branch since it has been branchedout of br2 and will merge into br1</br>
</br>
</br>
##To check whether commit exist in branch</br>
git branch --contains SHA1</br>
</br>
##squash your commits</br>
Supoose you want to squash last n commits:</br>
git rebase -i HEAD~5</br>
Then it will open editor.</br>
will show:</br></br>
pick 5</br>
pick 4</br>
pick 3</br>
pick 2</br>
pick 1</br>
</br>
suppose i want to squash all in 1</br>
replace pick with squash</br>
squash 5</br>
squash 4</br>
squash 3</br>
squash 2</br>
pick 1</br>
 It will have all the commits with commit of 1.</br>
 </br>
 ##Clean all the things::</br>
git clean -d -n -x</br>
                -n shows what would be removed without doing it</br>
git clean -d -f -x</br>
                -d removes directories too</br>
                -f is force</br>
                -x removes .gitignore files as well (build products)</br>
                </br>
##The many ways to make a patch:</br>
git format-patch -1 392a0ea071e054612d02232de7b3d2a2b7e9c1d8</br>
git diff HEAD HEAD~3 > my.patch</br>
</br>
</br>
##Reset branch to remote:</br>
git fetch origin</br>
git reset --hard origin/master</br>
note: throws out any commits you have that aren’t pushed, be careful!</br>
</br>
</br>
##Amend last commit by adding/changing old file into last commit:</br>
Suppose you made a commit.</br>
Now we have changed another file but want to commit under last commit.</br>
git add file-changed</br>
git commit --amend.</br>
</br>
It will open editor with last. You can amend the commit statement of just save it.</br>
The new change is under the last commit itself.</br>
</br>
</br>
##How to find logs by one user only::</br>
git log --author=name</br>
</br>
##to find log of one user on particular branch</br>
git log --author=name [branch-name]</br>
</br>
## apply patch</br>
git diff > difffile</br>
and to apply the diff > git apply difffile</br>
</br>
##If nothing has changes except the file permissions, and you want to ignore in git status, use</br>
"git config core.fileMode false".</br>
</br>
##Reverting your last commit</br>
git revert hash_of_commit</br>
</br>
##How can one change the timestamp of an old commit in Git?</br>
git commit --amend --date="Wed Feb 16 14:00 2011 +0100"</br>
</br>
</br>
