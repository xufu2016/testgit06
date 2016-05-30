# info
git log --oneline --graph
git shortlog
git shortlog -sne

git show Head
git show Head~1 (commit just revised)
git log oneline (first line just commit)
 
git show 45645 (show the commit detail)
 
 git remote
 git remote -v (fetch/push)
 
Git protocol
        cat .git/config
View branches/Tags
    
    git branch
    git branch -r (merged from)
    
    git tag
    
    git remote -v
    git remote add origin https://github.com/....
    
    git fetch
    git fetch origin
    
    git log origin/master
    
    git merge origin/master (fast-forward) -->  move header pointer to new location
    git log
    
    git fetch; git merge origin/master ==> the same as git pull (shortcut)
    
    
    git branch --set-upstream master origin/master (branch master set up to track branch master from origin)

Pushing to Remote
    git commit -am "sharing is easy"
    git push
    
        ##step below can add without username and password
    git remote rm origin 
    git remote -v
    git remote add origin git@github.com:username@gitfundameental.git
    git push

Creating and Verfying Tags
    git tag v1.0
    git tag
    git tag -a v1.0_withmessage
    git tag -s v1.0_signed (sign)
     user ESC:q!  to close text window

Pulling Tags to a REmote
    git push --tags    
    github (master branch dropdown to find out tags) 
    
    
