# A Crash Course in PostgreSQL

#### Login to postgresql:
```
psql -d mydb -U myuser -W
psql -h myhost -d mydb -U myuser -W
psql -U myuser -h myhost "dbname=mydb sslmode=require" # ssl connection
```

#### Default Admin Login:
```
sudo -u postgres psql -U postgres
sudo -u postgres psql
```

#### List databases on postgresql server:
```
psql -l [-U myuser] [-W]
```
Turn off line pager pagination in psql:
```
\pset pager
```

#### Determine system tables:
```sql
SELECT * FROM pg_tables WHERE tableowner = 'postgres';
```

#### List databases from within a pg shell:
```
\l
```

#### List databases from UNIX command prompt:
```
psql -U postgres -l
```

#### Describe a table:
```
\d tablename
```

#### Quit psql:
```
\q
```

#### Switch postgres database within admin login shell:
```
\connect databasename
```

#### Reset a user password as admin:
```sql
ALTER USER usertochange with password 'new_passwd';
```

#### Show all tables:
```
\dt
```

#### List all Schemas:
```
\dn
```

#### List all users:
```
\du
```

#### Load data into postgresql:
```
psql -W -U username -H hostname < file.sql
```

#### Dump (Backup) Data into file:
```
pg_dump -W -U username -h hostname database_name > file.sql
```

#### Increment a sequence:
```sql
SELECT nextval('my_id_seq');
```

#### Create new user:
```sql
CREATE USER jjasinski WITH PASSWORD 'myPassword';
```

... or ...
```
sudo -u postgres createuser jjasinski -W
```

#### Change user password:
```sql
ALTER USER Postgres WITH PASSWORD 'mypass';
```

#### Grant user createdb privilege:
```sql
ALTER USER myuser WITH createdb;
```
#### Create a superuser user:
```sql
CREATE USER mysuper with password '1234' SUPERUSER
```
... or even better ...
```sql
CREATE USER mysuper with password '1234' SUPERUSER CREATEDB CREATEROLE INHERIT LOGIN REPLICATION;
```
...or...
```
sudo -u postgres createuser jjasinski -W -s
```

#### Upgrade an existing user to superuser:
```sql
ALTER USER mysuper with superuser;
```
... or even better ...
```sql
ALTER USER mysuper with SUPERUSER CREATEDB CREATEROLE INHERIT LOGIN REPLICATION
```
#### Show Database Version:
```sql
SELECT version();
```

#### Change Database Owner:
```sql
ALTER DATABASE database_name owner TO new_owner;
```

#### Copy a database:
```sql
CREATE DATABASE newdb WITH TEMPLATE originaldb;
```
http://www.commandprompt.com/ppbook/x14316

#### View Database Connections:
```sql
SELECT * FROM pg_stat_activity;
```
View show data directory (works on 9.1+; not on 7.x):
```sql
show data_directory;
```

#### Show run-time parameters:
```sql
show all;
SELECT * FROM pg_settings;
```

#### Show the block size setting:
```
show block_size;

block_size
------------
8192
(1 row)
```

#### Show stored procedure source:
```sql
SELECT prosrc FROM pg_proc WHERE proname = 'procname'
```
#### Grant examples:
##### Readonly to all tables for myuser
```sql
GRANT SELECT ON all tables IN schema public to myuser;
```
##### All privileges on table1 and table2 to myuser
```sql
GRANT all privileges ON table1, table2, table3 to myuser;
```

#### Restore Postgres .dump file:
```
pg_restore --verbose --clean --no-acl --no-owner -h localhost -U myuser -d mydb latest.dump
```

Source: http://jazstudios.blogspot.com/2010/06/postgresql-login-commands.html
