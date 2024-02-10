---
type: evidence
topic: PostgreSQL 
---
- Topic : #VeilleIT/PostgreSQL 
- Tags : #VeilleIT/Sysadmin 

# Idea


DB Command : `\du`

SQL Requette :
```SQL
SELECT usename AS role_name,
	CASE
	WHEN usesuper AND usecreatedb THEN
		CAST('superuser, create database' AS pg_catalog.text)
	WHEN usesuper THEN
		CAST('superuser' AS pg_catalog.text)
	WHEN usecreatedb THEN
		CAST('create database' AS pg_catalog.text)
	ELSE
		CAST('' AS pg_catalog.text)
	END role_attributes
FROM pg_catalog.pg_users 
ORDER BY role_name desc;
```

Sources : [PostgreSQL List Users: Shows PostgreSQL Users](https://www.postgresqltutorial.com/postgresql-administration/postgresql-list-users/)

## West : Similar

## East : Opposite

## North : Theme / Question

[[How to manage PostgreSQL databases]]

## South : What does it lead to

