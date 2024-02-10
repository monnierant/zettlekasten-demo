---
type: methode
topic: Powershell 
---
Topic : #Powershell 
Tags : #VeilleIT/Sysadmin 

# Idea

Get the Average size of file
```Powershell
get-childitem -path "." -Include *.log -Recurse | Measure-Object -Property length -Average 
```

Get the Sum size of file
```Powershell
get-childitem -path "." -Include *.log -Recurse | Measure-Object -Property length -Sum 
```


Sources : [Group and Sum Objects issue : r/PowerShell](https://www.reddit.com/r/PowerShell/comments/fwjvr6/group_and_sum_objects_issue/)

## West : Similar

- [[Powershell Sum File Size per grouping]]
- [[Powershell ZIp File]]

## East : Opposite


## North : Theme / Question

## South : What does it lead to

🔧🧰💡🕯️