# Set First Gallery Image to Base Image (and more...)

The following loops through _all_ products and sets the first image in the image gallery of each product to be 1) the base image source, 2) the small_image source, and 3) the thumbnail image source.

```php
require 'app/Mage.php';
Mage::app();

$products = Mage::getModel('catalog/product')->getCollection()->addAttributeToSelect('*');

foreach ($products as $product) {
  $product = Mage::getModel('catalog/product')->load($product->getId());
  $mediaGallery = $product->getMediaGallery();

  print $product->getName().PHP_EOL;
  print "Found images:".count($mediaGallery['images']).PHP_EOL;

  if (isset($mediaGallery['images'])){
      //loop through the images
      foreach ($mediaGallery['images'] as $image){
          //set the first image as the base image
          Mage::getSingleton('catalog/product_action')->updateAttributes(array($product->getId()), array(
            'image'=>$image['file'],
            'small_image'=>$image['file'],
            'thumbnail'=>$image['file'],
          ), 0);
          //stop
          break;
      }
  }
}
```

Source: http://stackoverflow.com/a/19154055/12694 (Marius comes through - again!)
