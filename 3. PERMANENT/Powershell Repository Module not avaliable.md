---
type: evidence
topic: Powershell
---

- Topic : #Powershell 
- Tags : #troubleshoot 

# Idea


## Issue:

```
_PackageManagement\Install-Package : No match was found for the specified search criteria and module name 'PowerShellGet'. Try Get-PSRepository to see all available registered module repositories._
```

## Solution:
```Powershell
[Net.ServicePointManager]::SecurityProtocol = [Net.ServicePointManager]::SecurityProtocol -bor [Net.SecurityProtocolType]::Tls12
Register-PSRepository -Default -Verbose
```


# Links

Sources : [Trying to Install-Module AzureAD but Get-PSRepository "WARNING: Unable to find module repositories." - Microsoft Community Hub](https://techcommunity.microsoft.com/t5/windows-powershell/trying-to-install-module-azuread-but-get-psrepository-quot/m-p/202819)


## West : Similar

## East : Opposite

## North : Theme / Question

## South : What does it lead to

- [[Powershell - SFTP - Posh-SSH]]
