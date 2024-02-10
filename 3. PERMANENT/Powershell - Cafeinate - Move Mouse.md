---
type: evidence
topic: Powershell
---

- Topic : #Powershell 
- Tags : #cafeinate

# Idea

Keep mouse moving with powershell to keep computer awake


```Powershell


$MOVEMENTSIZE = 200
$SLEEPTIME = 5

Add-Type -AssemblyName System.Windows.Forms
while ($true) {
$POSITION = [Windows.Forms.Cursor]::Position
$POSITION.x += $MOVEMENTSIZE
$POSITION.y += $MOVEMENTSIZE
[Windows.Forms.Cursor]::Position = $POSITION
Start-Sleep -Seconds $SLEEPTIME
$POSITION = [Windows.Forms.Cursor]::Position
$POSITION.x -= $MOVEMENTSIZE
$POSITION.y -= $MOVEMENTSIZE
[Windows.Forms.Cursor]::Position = $POSITION
Start-Sleep -Seconds $SLEEPTIME
}

```


# Links

Sources :

## West : Similar

## East : Opposite

## North : Theme / Question

## South : What does it lead to

