---
title: "Tips para sesiones con Postgres"
description: "Manejo de consultas y administración de procesos"
tags: database
---

Listar todos los procesos activos de Postgres:

```sql
SELECT
    datid, datname, pid, usesysid, usename,
    application_name, client_addr, client_hostname, client_port,
    backend_start, xact_start, query_start, state_change,
    wait_event_type, wait_event, state, backend_xid,
    backend_xmin, query, backend_type
FROM pg_stat_activity
WHERE state != 'idle'
    AND datname = '{DATABASE_NAME}';
```

Eliminar un proceso:

```sql
SELECT pg_terminate_backend(pid);
```

Generar las consultas de sql necesarias para poder terminar los procesos activos:

```sql
SELECT
    'SELECT pg_terminate_backend(' || pid ||');' AS matar_consulta, query_start, query, state, wait_event_type, usename, application_name, client_addr
FROM pg_stat_activity
WHERE state != 'idle'
    AND datname = '{DATABASE_NAME}';
```

Otra consulta para matar procesos activos:

```sql
SELECT pg_terminate_backend(pg_stat_activity.pid)
FROM pg_stat_activity
WHERE datname = '{DATABASE_NAME}'
    AND pid <> pg_backend_pid();
```
