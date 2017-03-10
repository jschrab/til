# Reloading a collection is sometimes necessary

Certain operations on collections cause caching of results that can lead to confusing situations. Assume the following:

```php
$collection = Mage::getModel('my_mod/my_items')->getCollection();

echo $collection->count();

$collection->addFieldToFilter('address',
   array(
       array('eq' => $address)
   )
);

echo $collection->count();
```
You would think that the **$collection->addFieldToFilter()** would reduce the result set and the second count() call would reflect that. But the first **$collection->count()** has been cached, so the second **$collection->count()** call would be the same.

Calling **$collection->clear()** allows for reloading of the collection and the second **$collection->count()** will have a sensible result.
