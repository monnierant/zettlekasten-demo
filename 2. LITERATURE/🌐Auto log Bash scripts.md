---
type: literature
status: checked
topic: bash
---
- Topic : #bash
- Tags : #linux #VeilleIT/Sysadmin #log


Source : [linux - How can I fully log all bash scripts actions? - Server Fault](https://serverfault.com/questions/103501/how-can-i-fully-log-all-bash-scripts-actions)

# Ideas


## complexe exec

I generally put something similar to the following at the beginning of every script (especially if it'll run as a daemon):

```bash
#!/bin/bash
exec 3>&1 4>&2
trap 'exec 2>&4 1>&3' 0 1 2 3
exec 1>log.out 2>&1
# Everything below will go to the file 'log.out':
```

> [!hint] 
> 1. `exec 3>&1 4>&2`
>   
>     Saves file descriptors so they can be restored to whatever they were before redirection or used themselves to output to whatever they were before the following redirect.
  >   
> 2. `trap 'exec 2>&4 1>&3' 0 1 2 3`
>     
>     Restore file descriptors for particular signals. Not generally necessary since they should be restored when the sub-shell exits.
>     
> 3. `exec 1>log.out 2>&1`
>     
>     Redirect `stdout` to file `log.out` then redirect `stderr` to `stdout`. Note that the order is important when you want them going to the same file. `stdout` _must_ be redirected before `stderr` is redirected to `stdout`.
>     

From then on, to see output on the console (maybe), you can simply redirect to `&3`. For example, 
```bash
echo "$(date) : part 1 - start" >&3
```

will go to wherever `stdout` was directed, presumably the console, prior to executing line 3 above.

## simple all log

Following off of what others said, the set [manual](https://www.gnu.org/savannah-checkouts/gnu/bash/manual/bash.html#The-Set-Builtin) is a good resource. I put:

```bash
#!/usr/bin/env bash
exec 1> command.log 2>&1
set -x
```

At the top of scripts I wish to keep going, or `set -ex` if it should exit upon error.




Linked Sources :