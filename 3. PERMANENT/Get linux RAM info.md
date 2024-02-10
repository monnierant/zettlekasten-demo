---
type: evidence
topic: Sysadmin 
---

- Topic : #VeilleIT/Sysadmin 
- Tags : #linux 

# Idea

## Basic info

Use command `free -h` to get basic info about ram


Result :
> [!example] 
> ```
> 			 total        used        free      shared  buff/cache   available
> Mem:            15G        7.2G        2.2G        927M        6.2G        7.2G
> Swap:          510M        3.5M        507M
> ``` 


## Get RAM speed

`dmidecode --type memory`


> [!example]  
> ```
> Handle 0x0017, DMI type 17, 27 bytes
> Memory Device
> 	Array Handle: 0x0016
> 	Error Information Handle: No Error
> 	Total Width: 72 bits
> 	Data Width: 64 bits
> 	Size: 2048 MB
> 	Form Factor: DIMM
> 	Set: 1
> 	Locator: DIMM1A
> 	Bank Locator: Bank1
> 	Type: DDR2
> 	Type Detail: Synchronous
> 	Speed: 667 MHz
> 	Manufacturer: 5185
> 	Serial Number: 05009F22
> 	Asset Tag: Not Specified
> 	Part Number: 72T232220HFA3SB
> ``` 

# Links

Sources : [Linux Ram Info Command](https://www.cyberciti.biz/faq/linux-ram-info-command/)

## West : Similar

## East : Opposite

## North : Theme / Question

[[How to know Linux VM ressources]]

## South : What does it lead to

