### Change the baseurl Directly in the MySQL Database

Magento writes the domain it lives at in its database. Moving database copies around on servers could cause redirects back to the origin website. So the *Baseurl* needs to be changed.

The variables exists in the *core_config_data* table and there are two to change - secure and unsecure.

```sql
mysql> SELECT * FROM core_config_data WHERE PATH LIKE '%base_url%';
+-----------+---------+----------+-----------------------+-----------------------------------------+
| config_id | scope   | scope_id | path                  | value                                   |
+-----------+---------+----------+-----------------------+-----------------------------------------+
|        38 | default |        0 | web/unsecure/base_url | http://<domain>/<basepath>/             |
|        43 | default |        0 | web/secure/base_url   | https://<domain>/<basepath>/            |
+-----------+---------+----------+-----------------------+-----------------------------------------+
```

So...

```sql
UPDATE core_config_data SET value='http://<newdomain>/<newbasepath>/' WHERE PATH = 'web/unsecure/base_url';
UPDATE core_config_data SET value='https://<newdomain>/<newbasepath>/' WHERE PATH = 'web/secure/base_url';
```

Of related use, "Use Secure in Frontend/Admin" is in the same table:
```sql
mysql> SELECT * FROM core_config_data WHERE path LIKE '%secure/use%';
+-----------+---------+----------+-----------------------------+-------+
| config_id | scope   | scope_id | path                        | value |
+-----------+---------+----------+-----------------------------+-------+
|        48 | default |        0 | web/secure/use_in_frontend  | 1     |
|        49 | default |        0 | web/secure/use_in_adminhtml | 1     |
+-----------+---------+----------+-----------------------------+-------+
```

Which could be turned off...

```sql
UPDATE core_config_data SET value='0' WHERE PATH = 'web/secure/use_in_frontend';
UPDATE core_config_data SET value='0' WHERE PATH = 'web/secure/use_in_adminhtml';
```

fin
