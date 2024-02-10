---
type: evidence
topic: linux
---
- Topic : #linux 
- Tags : #VeilleIT/Sysadmin #apt

# Idea


> [!error] 
> When running `apt-get install <package_name>`
> ```
> sudo apt-get install package_name
> Reading package lists... Done
> Building dependency tree       
> Reading state information... Done
> E: Unable to locate package package_name
> ``` 


## Update the repository cache

If this is the first time you are using your system after installing, you should run the update command:
```
sudo apt update
```

## Check if package exist for your linux version


![[Get linux version#lsb release]]


Package compatibility can be checked on: [Ubuntu – Recherche de paquets Ubuntu](https://packages.ubuntu.com/?ref=itsfoss.com)


``

Sources : [[Solved] "E: Unable to locate package" Error on Ubuntu](https://itsfoss.com/unable-to-locate-package-error-ubuntu/)

## West : Similar

## East : Opposite

## North : Theme / Question

[[APT Download package only]]

## South : What does it lead to

