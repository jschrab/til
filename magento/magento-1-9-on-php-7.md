# Magento 1.9 on PHP7

File: **app/code/core/Mage/Core/Model/Layout.php**   
Inside **function getOutput()**, change this line:

```php
$out .= $this->getBlock($callback[0])->$callback[1]();
```
...to...
```php
$out .= $this->getBlock($callback[0])->{$callback[1]}();
```
This is because of [Uniform Variable Syntax](https://wiki.php.net/rfc/uniform_variable_syntax) requirements in PHP7.

**UPDATE**: As of 5-Apr-2016, I think this is a little premature. There are other articles that show there are multiple places that UVS needs to be applied, as well as admin login session management that may not be perfect. Summary: Sit tight on PHP7 for Magento for a few months longer.

Source: http://afilina.com/magento-1-9-on-php7
