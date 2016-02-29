# Finding Current Skin Path in Magento

There are multiple ways...

Just the path variable:  

```php
Mage::getDesign()->getSkinBaseDir()
```

Probably the best way for .phtml files:  

```php
echo $this->getSkinUrl('your_image_folder_under_skin/image_name.png');
```

Source: http://stackoverflow.com/questions/10360096/get-skin-path-in-magento
