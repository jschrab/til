# How to View and/or Set the Order Incremental ID

#### Find the Current Increment IDs for All Stores
```SQL
SELECT
  core_store_group.name AS group_name,
  core_website.name AS website_name,
  core_store.name AS store_name,
  core_store.store_id,
  increment_prefix,
  increment_last_id,
  entity_type_code
FROM
  eav_entity_store
INNER JOIN
  eav_entity_type ON eav_entity_type.entity_type_id = eav_entity_store.entity_type_id
INNER JOIN
  core_store ON core_store.store_id = eav_entity_store.store_id
INNER JOIN
  core_store_group ON core_store_group.group_id = core_store.group_id
INNER JOIN
  core_website ON core_website.website_id = core_store.website_id
WHERE
  eav_entity_store.store_id != 0 ORDER BY eav_entity_store.store_id;
```
This will display your current increment ID and prefix for all document types (quotes, orders, invoices, shipments, and credit memos). In addition it will show you the website group, website name, store name, and store ID for each type of increment ID to help you in updating a specific store among multiple stores.

#### Find the Current Increment IDs for All Stores
```SQL
UPDATE
  eav_entity_store
INNER JOIN
  eav_entity_type ON eav_entity_type.entity_type_id = eav_entity_store.entity_type_id
SET
  eav_entity_store.increment_last_id='XXXXXXXXXX'
WHERE
  eav_entity_type.entity_type_code='order' AND eav_entity_store.store_id = 'Y';
```
Replace the X‘s with your desired order number, replace Y with the store ID of the store you want to modify, then run the query.

Source: https://www.warpconduit.net/2012/04/18/how-to-change-the-order-increment-id-and-prefix-in-magento/
