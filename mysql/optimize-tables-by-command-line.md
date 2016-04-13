# Optimize Tables By Command Line
```
mysqlcheck -u username -p --auto-repair --optimize --all-databases
```
InnoDB tables *will* be locked when they are processed. This could be a temporary but serious performance concern.

*InnoDB doesn't support the OPTIMIZE the way MyISAM does. It does something different. It creates an empty table, and copies all of the rows from the existing table into it, and essentially deletes the old table and renames the new table, and then runs an ANALYZE to gather statistics. That's the closest that InnoDB can get to doing an OPTIMIZE.* (via http://stackoverflow.com/a/30635926)

The informational message for InnoDB tables will be:
```
Table does not support optimize, doing recreate + analyze instead
```

Making a backup is, of course, strongly recommended...
