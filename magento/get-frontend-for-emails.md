# Get FrontEnd for Emails

Within a Magento admin/shopping-cart context, Magento "knows" the proper 'frontend' theme for the store. But in a shell command or cron called situation, it probably won't. So go get it.

```php
// Set store
$previousStore = Mage::app()->getStore();
Mage::app()->setCurrentStore($_order->getStore()->getCode());
Mage::getDesign()->setArea('frontend');

/* Your email sending code */

// Restore config
Mage::app()->setCurrentStore($previousStore->getCode());
```

Source: http://stackoverflow.com/a/39368266/12694
