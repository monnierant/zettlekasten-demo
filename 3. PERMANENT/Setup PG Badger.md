---
type: evidence
topic: Sysadmin 
---

- Topic : #VeilleIT/Sysadmin 
- Tags : #VeilleIT/PostgreSQL 

# Idea


Afin de permettre un usage de PGBadger pour bien comprendre ce qui se passe sur le serveur postgres il faut augmenter le niveau de log du postgres

Pour cela, il faut éditer le fichier `data/postgresql.conf`


Dans la section
```
#------------------------------------------------------------------------------
# ERROR REPORTING AND LOGGING
#------------------------------------------------------------------------------
```

Il faut éditer les lignes suivantes pour les décomenter et mettre les réglages suivants
```
log_checkpoints = on
log_connections = on
log_disconnections = on
log_error_verbosity = default
log_line_prefix = '%t [%p]: client=%h '
log_lock_waits = on
log_temp_files = 0

log_min_duration_statement =  1000 # Log request taking more than 1 second
```

Ensuite on va recharger les réglages sans redémarer le serveur ni coupé les connexions en cours

[[PostgreSQL reload conf without restarting]]

# Links

Sources : [GitHub - darold/pgbadger: A fast PostgreSQL Log Analyzer](https://github.com/darold/pgbadger)

## West : Similar

## East : Opposite

## North : Theme / Question

- [[How to deploy a performant and reliable PostgreSQL database infrastructure]]

## South : What does it lead to

