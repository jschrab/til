# How to change a product dropdown attribute to a multiselect in Magento

First, update the attribute input type to multiselect:

```SQL
UPDATE eav_attribute SET
entity_type_id = '4',
attribute_model = NULL,
backend_model = 'eav/entity_attribute_backend_array',
backend_type = 'varchar',
backend_table = NULL,
frontend_model = NULL,
frontend_input = 'multiselect',
frontend_class = NULL
WHERE attribute_id = 'YOUR_ATTRIBUTE_ID_HERE';
```
Next, copy the attribute values from the old table to the new:
```SQL
INSERT INTO catalog_product_entity_varchar ( entity_type_id, attribute_id, store_id, entity_id, value)
SELECT entity_type_id, attribute_id, store_id, entity_id, value
FROM catalog_product_entity_int
WHERE attribute_id = YOUR_ATTRIBUTE_ID_HERE;
```
Finally,  remove the old values or they will conflict with the new setup (the old values will load, but Magento will save new values to the varchar table):
```SQL
DELETE FROM catalog_product_entity_int
WHERE entity_type_id = 4 and attribute_id = YOUR_ATTRIBUTE_ID_HERE;
```
The value for "entity_type_id" that you'll want to use may not always be "4" as referenced above. You'll want to check the table "eav_entity_type" and find the entry that has the "entity_type_code" set to "catalog_product". The "entity_type_id" for that record is the value you need to use. In most cases this value is either "4" or "10", but this may vary in future versions of Magento.


Source: http://swarminglabs.com/how-to-change-a-product-dropdown-attribute-to-a-multi-select/
