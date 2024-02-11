---
type: evidence
topic: PostgreSQL
---

- Topic : #VeilleIT/PostgreSQL 
- Tags : #pg_dump #troubleshoot 

# Idea

Error during backup of a database.

> [!error] 
> This is a **Critical** error 
> ```
> pg_dump: erreur : Sauvegarde du contenu de la table « boxdocument » échouée : échec de PQgetResult().
> pg_dump: erreur : Message d'erreur du serveur : ERROR:  invalid page in block YYYYY of relation base/xxxxx/xxxx
> pg_dump: erreur : La commande était : COPY public.boxdocument (id_bx, com_bx, extension_bx, nom_bx, id_br_bx, id_ut_proprietaire_bx, 
> est_inutile_nomade_bx, dth_creation_bx, dth_modification_bx, contenu_bx, taille_bx) TO stdout;
> ```

This is caused by a failled checksum on a data block

# To Fi x

## Zeroed out bad pages

> [!attention] 
> This methode will zeroed out the data so it lead to data lost 

```sql
SET zero_damaged_pages = on;

VACUUM FULL foo.some_table;
```

> [!example] 
> ```
> WARNING:  invalid page in block 54809 of relation base/48461770/48462009; zeroing out page
> WARNING:  invalid page in block 54810 of relation base/48461770/48462009; zeroing out page
> ```

```sql

REINDEX TABLE foo.some_table;

SET zero_damaged_pages = off;

```

# Links

Sources : 
- [sql - Postgresql pg\_dump for "invalid page in block" database does not work properly - Stack Overflow](https://stackoverflow.com/questions/62422298/postgresql-pg-dump-for-invalid-page-in-block-database-does-not-work-properly)
- [S6: Invalid page / page verification failed (data corrupted) · pganalyze](https://pganalyze.com/docs/log-insights/server/S6)
- [Database Soup: De-corrupting TOAST Tables](http://www.databasesoup.com/2013/10/de-corrupting-toast-tables.html)

## West : Similar

## East : Opposite

## North : Theme / Question

## South : What does it lead to

