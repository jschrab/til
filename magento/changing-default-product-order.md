# Changing the Default Order of Products

While it's possible to change the default _field_ on which products are sorted, it is not possible 1) to define anything other than ASC order and 2) one cannot have a multi-key sort. To actually do this requires some code.

```php
// Default getLoadedProductCollection() in /template/catalog/product/list.phtml
$_productCollection=$this->getLoadedProductCollection();

// Reset default sorting preference and add our own
$_productCollection->clear();
$_productCollection->getSelect()->reset(Zend_Db_Select::ORDER);
$_productCollection->addAttributeToSort('price', 'DESC');
$_productCollection->addAttributeToSort('name', 'ASC');
```

Source: https://stackoverflow.com/questions/20262567/magento-sort-product-collection-by-using-addattributetosort-for-custom-attribu

* * *

Supposedly it's possible to define this in a **layout.xml** override but I could never get it to work.
