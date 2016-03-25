# Basic user privilege adding

List out users...
```sql
\du
```

```sql
 Role name |                   Attributes                   | Member of
-----------+------------------------------------------------+-----------
 demo_role | Cannot login                                   | {}
 postgres  | Superuser, Create role, Create DB, Replication | {}
 test_user |                                                | {}
```

Give **test_user** the same privileges as **postgres** itself:

```sql
ALTER USER test_user WITH SUPERUSER CREATEROLE CREATEDB REPLICATION
```

Source: https://www.digitalocean.com/community/tutorials/how-to-use-roles-and-manage-grant-permissions-in-postgresql-on-a-vps--2
