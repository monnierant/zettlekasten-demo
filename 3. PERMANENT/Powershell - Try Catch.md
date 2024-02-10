---
type: evidence
topic: Sysadmin 
---
- Topic : #VeilleIT/Sysadmin 
- Tags : #dev #Powershell 

# Idea

Try catch can be used to collect error in the code without crashing the script and allowing to react to the errors


## Basic exemple

```Powershell
$Fichier = "C:\Windows\System32\drivers\etc\**monfichier**"
try
{
   $ContenuFichier = Get-Content $Fichier -ErrorAction Stop
   Write-Host -ForegroundColor Green "Contenu du fichier récupéré ($Fichier)"
}
catch
{
   Write-Host "Attention, le fichier $Fichier est introuvable !" -ForegroundColor Red
}
```

## Use catch to write the real error message

Error info can be access with : `$_.Exception.Message`

```Powershell
$Fichier = "C:\Windows\System32\drivers\etc\monfichier"
try
{
   $ContenuFichier = Get-Content $Fichier -ErrorAction Stop
   Write-Host -ForegroundColor Green "Contenu du fichier récupéré ($Fichier)"
}
catch
{
   Write-Host $_.Exception.Message -ForegroundColor Red
}
```

## Use catch to isolate some errors

```Powershell
$Fichier = "C:\TEMP\CATCH\fichier2.txt"

try
{
   New-Item -ItemType File -Path $Fichier -ErrorAction Stop
   Write-Host -ForegroundColor Green "Création du fichier : $Fichier"
}
catch [System.Management.Automation.DriveNotFoundException]
{
   Write-Host "Le lecteur ciblé par la commande New-Item n'existe pas" -ForegroundColor Red
}
catch [System.IO.DirectoryNotFoundException]
{
   Write-Host "Le dossier cible n'existe pas, on relance la création en forçant la création du dossier" -ForegroundColor DarkYellow
   New-Item -ItemType File -Path $Fichier -Force -ErrorAction Stop
}
catch
{
   Write-Host $_.Exception.Message -ForegroundColor Red
}
```

# Links

Sources : [IT Connect # Comment utiliser Try, Catch et Finally avec PowerShell ?](https://www.it-connect.fr/powershell-try-catch-finally-tuto/)

## West : Similar

## East : Opposite

## North : Theme / Question

[[How to write better Powershell script that are reusable]]

## South : What does it lead to

