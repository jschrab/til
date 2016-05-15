# Backup Large Databases

Recommended options for **mysqldump** for large database exports.

```
mysqldump -u db_user -pPassword --single-transaction --quick --lock-tables=false db_name > db_backup.sql
```
**--single-transaction** : Creates a consistent snapshot by dumping all tables in a single transaction.

**--quick** : Retrieve rows for a table from the server a row at a time

**--lock-tables=false** : Do not lock all tables before dumping them

Source - http://www.dhimanv.com/backup-large-mysql-database/
