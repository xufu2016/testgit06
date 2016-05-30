visual tranches
    git log --graph --oneline
    git log --graph --oneline --all -decorate (will display info including label,tag,branch ...)
    
    
Set alias in global
    git config --global alias.lga "log --graph --oneline --all --decorate"
    git lga
    cat ~/.git.config (view the detail of git config)

Create local branch
    git branch feature
    git checkout feature
    echo "Feature1" >> readme.md
    git status
    git commit -am "Added feature1"
    
difference between branched and tags
    branch will continue with commits, tages will always on the same commit
    
    git branch fix1 9754393e
    git checkout fix1
    echo "Fixing bug#123">> readme.md

Renaming branch/Delete branch
    git branch -m fix1 bug1234  (rename branch)
    
    git branch -d bug1234 (will try to delete branch but only fully merge)
    git branch -D bug1234 (will delete anyway)
    
    git checkout -b feature2 (will create branch and switch to feature2 branch)

Recovering delted commits
    git reflog (list all branch)
    git branch bug1234 5a78c8b (delete branch keep 30 days)
    
Stashing Changes
    
    git stash (switch to other branch but don't want to lose changes)
    git stash list
    
    --switch to other branch and back
    git stash apply
    git stash list
    git reset --hard Head
    git status
    
    --or use 
    git stash pop 
    
    differenece: not found on git stash list
    
    echo "more changes"> newfile.md
    git stash
    git add newfile.md
    git stash
    
    
    
Merge
    git merge feature
    git config --global merge.tool kdiff3
    git mergetool -t kdiff3
    
    git diff --cached (compare repo with stashing area)
    
    git commit -m "Merged feature into master"
    
Rebase
    git rebase master
    git rebase --continue

Cherry-Picking Changes
    git cherry-pick 6fa434 (able to pick only 1 changes) 
    

git reset --mixed, --soft, and --hard
    git reset changes, at minimum, where the current branch (HEAD) is pointing
    The difference between --mixed and --soft is whether or not your index is also modified. So, if we're on branch master with this series of commits:
    
    git reset --soft B, master (and thus HEAD) now points to B, but the index still has the changes from C
    git reset --mixed B. (Note: --mixed is the default option). Once again, master and HEAD point to B, but this time the index is also modified to match B
    If we're at C and run git reset --hard B, then the changes added in C, as well as any uncommitted changes you have, will be removed, and the files in your working copy will match commit B
    
    git reset --soft and --mixed leave your files untouched.
    git reset --hard actually change your files to match the commit you reset to.
    
    
    
    
    $ git commit -m "Something terribly misguided"              (1)
    $ git reset --soft HEAD~                                    (2)
    << edit files as necessary >>                               (3)
    $ git add ...                                               (4)
    $ git commit -c ORIG_HEAD                                   (5)
    
    
    git revert commit-id (To get the commit ID, just use git log)
    
    
    If you are planning undoing a local commit entirely, whatever you changes you did on the commit, and if you don't worry anything about that, just do the following command.
    git reset --hard HEAD^1
    
    git reset --soft HEAD^1
    git reset HEAD
    
    git reset --soft HEAD^
    git rm --cached [files you do not need]
    git add [files you need]
    git commit -c ORIG_HEAD