---
type: literature
status: to-view
topic: Sysadmin 
---
- Topic : #VeilleIT/Sysadmin 
- Tags : #linux #VeilleIT/devops 

Source : [How to create a local APT repository? - Ask Ubuntu](https://askubuntu.com/questions/170348/how-to-create-a-local-apt-repository)

# Ideas


## Install dpkg-dev

Type in a terminal

```Bash
sudo apt-get install dpkg-dev
```

## The Script update-mydebs

It's a simple three liner:

```Bash
#! /bin/bash
 cd /usr/local/mydebs
 dpkg-scanpackages . /dev/null | gzip -9c > Packages.gz
```



Linked Sources :

# Links

## West : Similar

## East : Opposite

## North : Theme / Question

- [[How to create a local apt repo]]

## South : What does it lead to

