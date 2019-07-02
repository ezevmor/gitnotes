# Git notes

* [Remotes](#remotes)
* [Branches](#branches)
* [Longpaths](#longpaths)
* [Stash](#stash)

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

List configured remotes
```
git remote -v
```

<a name="longpaths"></a>
## Longpaths
Clone repository enabling long name files support in windows:

```
git clone -c core.longpaths=true repourl
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
