# Pulling Sales Info from Database in SQL

```SQL
SELECT
    a.increment_id AS 'Order ID',
    a.created_at AS 'Order Date',
    b.region AS 'State Shipping',
    b.postcode AS 'ZIP Code Shipped',
    a.base_subtotal_invoiced AS 'Pretax Subtotal',
    a.base_shipping_invoiced AS 'Shipping and Handling',
    a.base_tax_amount AS 'Sales Tax Collected',
    a.base_total_invoiced AS 'Grand Total'
FROM
    sales_flat_order a
JOIN
    sales_flat_order_address b
ON
    a.entity_id = b.parent_id
WHERE
    a.status = 'complete' AND
    a.created_at >= '2016-10-09 00:00:00' AND
    a.created_at <= '2016-12-02 23:59:59'
GROUP BY
    a.entity_id;
```

Source: https://magento.stackexchange.com/questions/30876/query-only-completed-orders
