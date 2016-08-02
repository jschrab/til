# Delete Test Orders

Magento makes it intentionally difficult to delete orders, even just development test orders. Here's a trivial script to do so:

```php
<?php

require 'app/Mage.php';
Mage::app('admin')->setUseSessionInUrl(false);
// replace your own orders numbers here:
$test_order_ids=array(
  '100000001',
);
foreach($test_order_ids as $id) {
    try {
        Mage::getModel('sales/order')->loadByIncrementId($id)->delete();
        echo "order #".$id." is removed".PHP_EOL;
    } catch (Exception $e) {
        echo "order #".$id." could not be removed: ".$e->getMessage().PHP_EOL;
    }
}
echo "complete.";
?>
```

Source: http://stackoverflow.com/a/4532177/12694
