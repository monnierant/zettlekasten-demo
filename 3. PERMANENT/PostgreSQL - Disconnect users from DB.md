---
type: evidence
topic: PostgreSQL
---

- Topic : #VeilleIT/PostgreSQL 
- Tags : #VeilleIT/Sysadmin 

# Idea


```SQL
SELECT pg_terminate_backend(pid)
FROM pg_stat_activity
WHERE datname = 'medtra5'
AND leader_pid IS NULL;
```


# Links

Sources :

## West : Similar

## East : Opposite

## North : Theme / Question

## South : What does it lead to

