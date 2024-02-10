---
type: evidence
topic: linux 
---

- Topic : #linux 
- Tags : #VeilleIT/devops 

# Idea


## Create and publish repo

```Bash
aptly repo create -config=/config/aptly.conf -distribution=stable -component=main -architectures=amd64 -comment="Installer Local repo" inst-local-repo
aptly repo add -config=/config/aptly.conf inst-local-repo ./amd64
aptly repo show -config=/config/aptly.conf inst-local-repo

aptly publish repo -config=/config/aptly.conf -distribution=stable -component=main -architectures=amd64 inst-local-repo filesystem:cdrom:
```

The `./amd64` is the folder where all the deb files are located

We can use [[APT Download package only]] or [[APTITUDE - Download linux package]] to download deb package from official repository 

## aptly.conf

```conf{
  "rootDir": "/tmp/.aptly",
  "downloadConcurrency": 4,
  "downloadSpeedLimit": 0,
  "architectures": [],
  "dependencyFollowSuggests": false,
  "dependencyFollowRecommends": false,
  "dependencyFollowAllVariants": false,
  "dependencyFollowSource": false,
  "dependencyVerboseResolve": false,
  "gpgDisableSign": false,
  "gpgDisableVerify": false,
  "gpgProvider": "gpg",
  "downloadSourcePackages": false,
  "skipLegacyPool": true,
  "ppaDistributorID": "ubuntu",
  "ppaCodename": "",
  "FileSystemPublishEndpoints": {
    "cdrom": {
      "rootDir": "/tmp/bootiso/local-repo",
      "linkMethod": "copy",
      "verifyMethod": "md5"
    }
  },
  "enableMetricsEndpoint": false,
  "logLevel": "debug",
  "logFormat": "default",
  "serveInAPIMode": false
}
```


# Links

Sources : 
- [aptly - Overview](https://www.aptly.info/doc/overview/)
- [[🌐aptly - Debian repository management tool]]

## West : Similar

- [[🌐How to create a local repository using apt-mirror and mirrorkit]]
- [[🌐How to create a local APT repository - Ubuntu]]
- [[🌐How to generate the `Release` file on a local package repository]]


## East : Opposite

## North : Theme / Question

- [[How to create a local apt repo]]

## South : What does it lead to

