---
type: evidence
topic: PostgreSQL 
---
- Topic : #VeilleIT/PostgreSQL 
- Tags : #VeilleIT/Sysadmin 

# Idea


Create user and his database

```Bash
createuser --no-superuser --createdb --no-createrole pg-$ACRON$RCT
psql << EOR
alter user \"pg-$ACRON$RCT\" with encrypted password '$PASSWORD';
EOR
```



Sources :

## West : Similar

## East : Opposite

## North : Theme / Question

[[How to manage PostgreSQL databases]]

## South : What does it lead to

