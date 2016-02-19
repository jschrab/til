# Deleting Gallery Images Quick

Every time you run a product image import, Magento copies the image from /media/import into a subdirectory of the /media/catalog/product folder. Annoyingly, it does not replace the image but rather adds it to the product and creates a copy __filename_2.jpg__ etc. So after several imports, you will have several copies of each image in your media folder and duplicate images on each product.

You can remove the duplicate images from the product data with a script, and delete unused duplicate images with an extension. However, when importing the complete catalog several times, I found it simpler to:

Delete the /media/catalog/product folder.  
Delete the product image references in the Magento database using the following SQL...

```SQL
DELETE FROM catalog_product_entity_media_gallery
DELETE FROM catalog_product_entity_media_gallery_value
```

Be warned! Only do this to clear all product images and start again.

Once you have successfully imported all images, you can safely delete any images in /media/import to free up server space.

Source - http://www.mootpoint.org/blog/magento-bulk-product-import-images/
