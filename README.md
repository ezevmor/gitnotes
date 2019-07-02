# Git notes

1. [Instalación](#instalacion)

* [Longpaths](#longpaths)
* [Stash](#stash)

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

## Instalación <a name="instalacion"></a>