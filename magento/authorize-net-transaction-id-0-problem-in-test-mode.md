# Magento / Authorize.net "Transaction ID 0" problem in test mode

_Upon investigation, while Authorize.net approved the transaction, because it’s in test [sic "text"] mode it doesn’t set a transaction id (or sets it to zero). Magento obviously doesn’t like this (probably quite rightfully so), so it shows the error and doesn’t process the order. Apparently this is normal._

Minor modification of **/Mage/Authorizenet/Model/Directpost.php** file and changed the if-statement in the checkTransId() method to:
```php
public function checkTransId()
{
    if (!$this->getConfigData('test') && !$this->getResponse()->getXTransId()) {
        Mage::throwException(
            Mage::helper('authorizenet')->__('Payment authorization error. Transaction id is empty.')
        );
    }
    return true;
}
```
... will allow for Transaction ID's of 0 (zero) to work in test mode. It would be best if this was a method override instead of core hack.

Source: http://www.pixeldistribution.co.uk/blog/ecommerce/integration-of-magento-with-authorize-net
