# Migrate a Wordpress Database (manually)

WordPress cooks in protocol/domains into URLs in its database, which makes migrations a pain. The following is what needs to be changed before an import into a target deployment.

```sql
UPDATE wp_options SET option_value = replace(option_value, 'http://www.oldurl', 'http://www.newurl') WHERE option_name = 'home' OR option_name = 'siteurl';

UPDATE wp_posts SET guid = replace(guid, 'http://www.oldurl','http://www.newurl');

UPDATE wp_posts SET post_content = replace(post_content, 'http://www.oldurl', 'http://www.newurl');

UPDATE wp_postmeta SET meta_value = replace(meta_value,'http://www.oldurl','http://www.newurl');
```
Source: https://wpbeaches.com/updating-wordpress-mysql-database-after-moving-to-a-new-url/
