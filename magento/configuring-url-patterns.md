# Configuring/Altering URL Patterns

To remove .html from product and category URL's...

**System -> Configuration**  
Then go to Catalog and expand the Search Engine Optimization tab.

Remove the “.html” text from both the input fields. Product URL Suffix and Category URL Suffix.

Do remember to regenerate the URL index:

**System->Index Management**
* Reindex “Catalog URL Rewrites”
* Refresh cache

Source: https://php.quicoto.com/how-to-remove-html-from-magento/

* * *

To insert static elements into a category or product URL, the **Mage_Catalog_Model_Url class** needs to be modified. Use a local copy, of course:

**Copy:**  
/app/code/core/mage/catalog/model/url.php

**To:**  
/app/code/local/mage/catalog/model/url.php

In **getCategoryRequestPath()**, **$requestPath** is where you can alter the URL:

From:
```php
$requestPath = $parentPath . $urlKey . $categoryUrlSuffix;
```

To:
```php
$requestPath = $parentPath . 'category/' . $urlKey . $categoryUrlSuffix;
```

Source: http://www.placementedge.com/blog/how-to-add-a-prefix-to-magento-product-urls/
