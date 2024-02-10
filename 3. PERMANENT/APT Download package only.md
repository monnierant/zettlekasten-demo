---
type: methode
topic: bash 
---
- Topic : #bash 
- Tags : 

# Idea


## Simple way

Use `--download-only`:
```
sudo apt-get install --download-only pppoe
```
This will download `pppoe` and any dependencies you need, and place them in `/var/cache/apt/archives`. That way a subsequent `apt-get install pppoe` will be able to complete without any extra downloads.

## Ensure dependencies 

```Bash
apt-get download $(apt-rdepends "${package}" | grep -v ^\ )
```

## Change destination folder

```Bash
aptitude -d -o Dir::Cache:archives=/home/alex/aptitude-test/ install alsaplayer
```


Sources :
- [debian - How to download a package and its dependencies with aptitude? - Unix & Linux Stack Exchange](https://unix.stackexchange.com/questions/313101/how-to-download-a-package-and-its-dependencies-with-aptitude/313117#313117)
- [How to download package not install it with apt-get command? - Unix & Linux Stack Exchange](https://unix.stackexchange.com/questions/408346/how-to-download-package-not-install-it-with-apt-get-command)
- 

## West : Similar

[[APTITUDE - Download linux package]]

## East : Opposite

## North : Theme / Question

## South : What does it lead to

[[Unable to locate package error ubuntu]]

