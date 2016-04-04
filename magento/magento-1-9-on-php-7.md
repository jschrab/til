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

Source: http://afilina.com/magento-1-9-on-php7
