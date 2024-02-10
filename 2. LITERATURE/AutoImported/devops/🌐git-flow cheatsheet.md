---
raindrop_id: 556540955
raindrop_last_update: 2023-06-27T21:40:20.532Z
type: literature
status: to-view
topic: devops
---
- Topic : #VeilleIT/devops
- Tags : #git #gitflow


Source :  
- https://danielkummer.github.io/git-flow-cheatsheet/index.fr_FR.html
- [Installing on Windows · petervanderdoes/gitflow-avh Wiki · GitHub](https://github.com/petervanderdoes/gitflow-avh/wiki/Installing-on-Windows)

# Ideas

> [!tip] 
> Utiliser `git add -p .` pour faire un ajout partielle et avoir un commit message par aspect rajouter 

## Init git flow

```bash
git flow init
```

## Feature

### Basic usage
Feature are only on dev computer repo

Start a feature
```Bash
git flow feature start MYFEATURE
```

When feature is finish, finish it, it will be merged into develop and deleted

```Bash
git flow feature finish MYFEATURE
```

### Teamwork

Publish feature :

```Bash
git flow feature publish MYFEATURE
```

Pull feature :

```Bash
git flow feature pull origin MYFEATURE
```
## Release

Start a release will create a `release/vX.X.X` branch

```Bash
git flow release start RELEASE [BASE]
git flow release publish RELEASE
```

Then when it's well done we can publish the release 

```Bash
git flow release finish RELEASE
git push --tags
```

> [!important] 
> This will merge **release** into `dev` and `master/main` and also create a `vX.X.X` tag on `master/main`

## Hotfix


Start a hotfix branch with `VERSION` the future version number

```Bash
git flow hotfix start VERSION [BASE]
```

Then when it's well done we can publish the release 

```Bash
git flow hotfix finish VERSION
```

> [!warning] 
> This will merge the **hotfix** into `dev` and `master/main` and also create a `VERSION` tag on `master/main`

Linked Sources :

