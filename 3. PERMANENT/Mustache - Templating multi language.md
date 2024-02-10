---
type: tool
topic: Sysadmin 
---
- Topic : #VeilleIT/Sysadmin 
- Tags : #templating #development #VeilleIT/devops 

# Idea

Use a templating for file with `{{VARIABLE}}` mustache format


## Bash

Can be installed and used in Bash script

### Used in docker

```Dockerfile
RUN mkdir -p /usr/local/bin/

ADD https://github.com/tests-always-included/mo/archive/refs/tags/3.0.2.tar.gz /tmp/mo.tar.gz

RUN tar -xzf /tmp/mo.tar.gz -C /tmp/ && \
    mv /tmp/mo-3.0.2/mo /usr/local/bin/ && \
    rm -rf /tmp/*
```

### Usage

```Bash
/usr/local/bin/mo </source/file.template >/dest/file
```


Sources : [{{ mustache }}](https://mustache.github.io)

## West : Similar

## East : Opposite

## North : Theme / Question

## South : What does it lead to

