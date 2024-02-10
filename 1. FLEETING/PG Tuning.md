
maxconnexion reduce 2:1 or 4:1 par CPU cores

use a pooler

pgpool or pgbounce (simplier one)

idle in transaction session timeout

autovacuum max worker 5 is a good starting point

pg stat statement plugin help to analyse bad requests

DONT use Select ... where X not in (select ...)

Explain analyse between begin rollback blocs

Reload [[PG Tuning]] without reload : [[PostgreSQL reload conf without restarting]]

Theme: [[How to deploy a performant and reliable PostgreSQL database infrastructure]]