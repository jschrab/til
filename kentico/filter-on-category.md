# Filter on Category

```sql
DocumentID IN (SELECT DocumentID FROM CMS_DocumentCategory WHERE CategoryID IN (SELECT CategoryID FROM CMS_Category WHERE CategoryName LIKE 'Technology'))
```

... this seems expensive to me...

Source: http://devnet.kentico.com/forums?forumid=45&threadid=27333https://devnet.kentico.com/forums/f65/fp27/t38510/filter-a-repeater-bsaed-on-categories
