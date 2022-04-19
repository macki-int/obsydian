`git log --pretty=oneline` - one line log

`git log origin/main..HEAD` - log of locale and remote commits 
`git diff origin/main..HEAD` - diff of locale and remote commits 

`git branch -r` - list both of branches
`git branch -r` - list of remote branches
`git log --branches --not --remotes` - all branches not pushed yet

`git cherry -v`  - list of commits not pushed yet

`git config --global user.name`
`git config --global user.email`
`git config -l` - config list
`git config --global credential.helper cache` - local computer remembers the token
`git config --global --unset credential.helper` - clear the token from the local computer

`git reset --soft HEAD~1` - reset last commit
`git reset <file>` - reset  add file before commit 