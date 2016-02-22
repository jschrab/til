# How to get product categories and the parent category of a subcategory in Magento


If you have the product as an object, for this example we say your product object is $product. The following should work:

```php
$product->getCategory()->getParentCategory();
```

That should return the parent category as an object of Mage_Catalog_Model_Category.

If you don't have the product but say have the product id then the following should be enough to get the product.

```php
$product = Mage::getModel('catalog/product')->load($product_id);
```
But note that a product could have more than one category assigned to in.

If you have more than one category per product you can use getCategoryCollection() to get all the categories.

```php
foreach ($product->getCategoryCollection() as $category) {
   $parent_category = $category->getParentCategory();
}
```

Source: https://stackoverflow.com/questions/16650242/how-to-get-immediate-parent-category-from-a-product
