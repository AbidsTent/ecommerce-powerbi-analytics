# Data model

The saved PBIX diagram metadata lists Orders, Order Items, Customers, Products, DimDate and the category translation table. The report definitions confirm visual bindings to date, category and customer-state fields. Relationship endpoints below come from the project notes. Cardinality in the CSVs was checked independently. The saved relationship settings, active flags and cross-filter directions could not be read from the embedded model.

| Documented join | Source evidence and reporting role |
|---|---|
| Customers `customer_id` to Orders `customer_id` | The customer lookup key is unique and every order matches a customer. The join supports reporting by customer state. |
| Orders `order_id` to Order Items `order_id` | One-to-many in the CSVs. Orders supply status and purchase time to item-level analysis. |
| Products `product_id` to Order Items `product_id` | Products provide the unique lookup side and all item lines match. The join supports category analysis. |
| DimDate date to Orders `order_date` | Documented date-to-order join. Report visuals reference `DimDate.Year` and `DimDate.Year-Month`. |
| Products to translation by `product_category_name` | Documented Power Query left outer merge. The lookup has a unique Portuguese category key. |

The logical path for state and purchase-period analysis runs through orders before reaching item lines. The product path reaches item lines directly. Cross-filter direction controls which selections reach each measure. In Desktop, inspect **Manage relationships** and test both order-grain and item-grain cards under each slicer to confirm the saved behavior.

Use distinct order IDs for order counts when crossing to item grain. For example, 9,803 orders have multiple lines. A row count after joining headers to lines would count those orders repeatedly. Use the composite `(order_id, order_item_id)` key when checking item grain, and sum each line's price and freight separately.

