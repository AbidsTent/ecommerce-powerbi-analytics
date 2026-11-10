# Data dictionary

| CSV | Rows | Grain |
|---|---:|---|
| `olist_orders_dataset.csv` | 99,441 | One row per order |
| `olist_order_items_dataset.csv` | 112,650 | One row per order and item sequence |
| `olist_customers_dataset.csv` | 99,441 | One row per order-associated customer ID |
| `olist_products_dataset.csv` | 32,951 | One row per product |
| `product_category_name_translation.csv` | 71 | One row per Portuguese category in the lookup |

| Source | Column | Reporting role |
|---|---|---|
| Orders | `order_id` | Order key for distinct counts and the item join |
| Orders and customers | `customer_id` | Customer record key used to associate an order with its location |
| Customers | `customer_unique_id` | Buyer identifier that can recur across orders |
| Customers | `customer_state` | State attributed to the order through the customer join |
| Orders | `order_status` | Recorded order outcome, including delivered |
| Orders | `order_purchase_timestamp` | When the order was placed, used to group the trend |
| Orders | `order_approved_at` | Recorded order approval time |
| Orders | `order_delivered_carrier_date` | Recorded handoff to the carrier |
| Orders | `order_delivered_customer_date` | Recorded delivery to the customer |
| Orders | `order_estimated_delivery_date` | Expected delivery date |
| Order items | `order_item_id` | Item sequence within an order, unique together with `order_id` |
| Order items and products | `product_id` | Product key used to attach category attributes to item lines |
| Order items | `shipping_limit_date` | Shipping deadline for the item |
| Order items | `price` | Item price in BRL |
| Order items | `freight_value` | Freight amount attributed to the item in BRL |
| Products and translation | `product_category_name` | Portuguese category and translation join key |
| Translation | `product_category_name_english` | English category label where a lookup match exists |

Other supplied CSVs profiled locally were geolocation (1,000,163 rows), payments (103,886), reviews (99,224) and sellers (3,095). They fall outside the documented report inputs.

