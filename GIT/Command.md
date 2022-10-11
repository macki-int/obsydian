`git log --pretty=oneline` - one line log

`git log origin/main..HEAD` - log of locale and remote commits 
`git diff origin/main..HEAD` - diff of locale and remote commits 

`git branch -r` - list both of branches
`git branch -r` - list of remote branches
`git log --branches --not --remotes` - all branches not pushed yet
`git branch -r --contains $commit` - list remote branches that contain $commit

`git cherry -v`  - list of commits not pushed yet

in project dir (local config)
`git config user.name`
`git config user.email`
`git config -l` - local config list

`git config --global user.name`
`git config --global user.email`
`git config --global -l` - global config list
`git config --global credential.helper cache` - local computer remembers the token
`git config --global --unset credential.helper` - clear the token from the local computer

`git reset --soft HEAD~1` - reset last commit
`git reset <file>` - reset  add file before commit 

`cherry -v origin/main` - show commits  that not pushed to remote repo yet

`git remote add origin <remote_repo_url>`` 
`git push --all origin` 
If you want to set all of your branches to automatically use this remote repo when you use git pull, add --set-upstream 
to the push: 
`git push --all --set-upstream origin`

`git reflog` 