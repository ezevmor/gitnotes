# Git notes

* [Remotes](#remotes)
* [Branches](#branches)
* [Longpaths](#longpaths)
* [Commits](#commits)
* [Update](#update)
* [Stash](#stash)
* [Undo local changes](#undo)
* [Import commit](#import)
* [Merge branches](#merge)
* [Conflicts](#conflicts)
* [Logs](#logs)
* [Rebase](#rebase)

<a name="remotes"></a>
## Remotes
Link local repository to a remote one:
```
git remote add <new_remote_name> https://remoteurl
```

List configured remotes
```
git remote -v
```

<a name="branches"></a>
## Branches
Create new branch:
```
git branch <branch_name>
```

Delete branch:
```
git push --delete <remote_name> <branch_name> // delete the remote branch
git branch -d <branch_name> // delete the local branch
```

<a name="longpaths"></a>
## Longpaths
Clone repository enabling long name files support in windows:
```
git clone -c core.longpaths=true repourl
```

<a name="commits"></a>
## Commits
Commit changes:
```
git commit -am "any description"
```

Rename the last commit name:
```
git commit --amend
// this command opens vim editor with the commit name in it
// we neet to press 'i' key to enter edit mode
// do the change
// press 'esc' to exit edit mode
// finally write: ':x' to save and exit
// if the commit has been pushed to the remote repository we need to do: 
// 'git push --force' (to push the change)
```

Rename certain commit name:
```
git rebase -i <commit_id> // <commit_id> is the commit before we want to change
// or 'git rebase -i HEAD~<n>' where <n> is the number of commits from the last
// that you want to see.
// This command opens vim editor with a list of commits in it; something like this:
// pick <commit_id1> commit name 1
// pick <commit_id2> commit name 2
// and information about the available commands.
// press 'i' key to enter edit mode
// change 'pick' word to 'reword' or 'r' in the line of whe commit that you want to change the name
// press 'esc' key to exit edit mode
// write: ':x' to save and exit
// now the vim editor will open with the commit name that you want to change in it
// do the change, save and exit
// if this commit has been pushed we need to do:
// 'git push --force' to push the change
```

<a name="update"></a>
## Update

Get new information without applying in the local:
```
git fetch
``` 

Download new remote repo changes in local:
```
git pull
```

Upload changes:
```
git push // push current branch to the origin/branch repo
git push <remote_name> // push current branch to the <remote_name>/currentbranch repo
git push <remote_name> <branch_name> // push <branch_name> to the <remote_name>/<branch_name> repo
```


<a name="stash"></a>
## Stash
List all stash positions:
```
git stash list
```

View the stored change in the "n" stash position:
```
git stash show -p stash@{n}
```

Store all changes in the stash container:
```
git add *
git stash save "any description"
```

Recover stored changes:
```
git stash pop //recover the last changes stored
git stash pop stash@{n} //recover the changes stored in the "n" stash position 
```

Resolve conflicts recovering changes in the right branch:
```
// the first step is resolve conficts in the files
git reset
git stash drop
```

Revert changes recovering changes in the wrong branch:
```
git reset HEAD --hard
```

Delete whole stash:
```
git stash clear
```

Delete changes stored in the "n" stash position:
```
git stash drop stash@{n}
```

<a name="undo"></a>
## Undo local changes
Delete all in working copy:
```
git reset --hard // delete changes in tracked files
git clean -fd // delete non tracked new folders and files
```

Undo last commit:
```
git reset HEAD~1 // undo last commit mantaining commit changes in working copy
git reset --hard HEAD~1 // undo last commit and delete commit changes
```

Back to a commit:
```
git reset --hard <commit_id>
```

<a name="import"></a>
## Import commit
Import commit to the current branch:
```
git cherry-pick <commit_id> // import the commit
git cherry-pick --abort // useful if cherry-pick produces conflict
```

<a name="merge"></a>
## Merge branches
Merge branches:
```
git merge <branch_name> // merge current branch with a local one
git merge <remote_name>/<branch_name> // merge current branch with a remote one
git merge --abort // useful if merge produces conflict
```

<a name="conflicts"></a>
## Conflicts
View all conflicts:
```
git diff --name-only --diff-filter=U
// then open file
// resolve each conflict
// and commit changes
```

<a name="logs"></a>
## Logs
View logs:
```
git log --pretty=oneline
```

View git activity:
```
git reflog
```
