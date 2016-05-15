# I Can't Login to Magento Admin

There are a host of reasons for this but the one that perplexed me for hours dealt with two environments with the same base domain but different subdomains. Cookie creation for login creates an "adminhtml" cookie. But with multiple domain cookies, Magento chooses wrongly. Clearing cookies all the time helps. The deeper solution...


> **The fix**
>
> The fix should be obvious: straighten out your cookie domains. Either configure them so that they're absolutely identical or set up your staging, local, and production to be on different root domains.

Summary: **Make cookie domains _completely_ different or _perfectly_ the same.**

Source: https://blog.philwinkle.com/i-cant-login-to-magento-admin/

---

If this _isn't_ your problem, maybe the answer is here: http://magento.stackexchange.com/a/26083/33450

---

If you are migrating a database from one site to another, your **cookie_domain** may be causing problems:

```sql
mysql> SELECT * FROM core_config_data WHERE PATH LIKE '%cookie%';
+-----------+---------+----------+----------------------------------------+----------------+
| config_id | scope   | scope_id | path                                   | value          |
+-----------+---------+----------+----------------------------------------+----------------+
|        60 | default |        0 | web/cookie/cookie_domain               | <yourdomain>   |
+-----------+---------+----------+----------------------------------------+----------------+
```
