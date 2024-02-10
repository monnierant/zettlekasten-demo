---
type: methode
topic: Powershell 
---
Topic : #Powershell 
Tags : #VeilleIT/Sysadmin 

# Idea

Get the sum of file size per file name (used to group logs by day for multiple users)
```Powershell
get-childitem -path "C:\Users\*\AppData\Roaming\path\to\log" -Include *.log -Recurse | Group-Object -Property Name | Select-Object Name, @{Name = "sumSize"; Expr = { ($_.Group.length | Measure-Object -Sum).Sum }} 
```

Get the average file size per file name (used to group logs by day for multiple users)
```Powershell
get-childitem -path "C:\Users\*\AppData\Roaming\path\to\log" -Include *.log -Recurse | Group-Object -Property Name | Select-Object Name, @{Name = "sumSize"; Expr = { ($_.Group.length | Measure-Object -Sum).Sum }} | Measure-Object -Property sumSize -Average
```

Sources : [Group and Sum Objects issue : r/PowerShell](https://www.reddit.com/r/PowerShell/comments/fwjvr6/group_and_sum_objects_issue/)

## West : Similar
[[Powershell Sum File Size]]

## East : Opposite

## North : Theme / Question

## South : What does it lead to

