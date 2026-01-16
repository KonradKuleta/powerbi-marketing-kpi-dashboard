# Data Dictionary (Synthetic)

Synthetic dataset simulating a **fitness products e-commerce store** in Germany (2025),
covering categories such as **equipment, accessories, and supplements**.

## fact_orders
**Grain:** 1 row = 1 order (order header)  
**Primary key:** `order_id`  
**Main fields (examples):** `order_date`, `customer_id`, `channel`, `items_count`, `units`, `order_net_revenue`

## fact_order_items
**Grain:** 1 row = 1 product line within an order  
**Keys:** (`order_id`, `product_id`)  
**Main fields (examples):** `order_id`, `product_id`, `qty`, `net_revenue`

## fact_marketing_spend_daily
**Grain:** 1 row = channel-day  
**Keys:** (`date`, `channel`)  
**Main fields:** `date`, `channel`, `spend`

## fact_targets
**Grain:** 1 row = metric-period (monthly)  
**Main fields (examples):** `metric` (e.g., Revenue), `period` (YYYY-MM), `target_value`, (optional: `period_start`), (optional: `channel`)

## dim_date
**Grain:** 1 row = 1 day  
**Primary key:** `date`  
**Main fields:** `month_name_en`, `month_no`, `quarter`, `quarter_start`, `year`, `year_month`

## dim_product
**Grain:** 1 row = 1 product  
**Primary key:** `product_id`  
**Main fields:** `product_name`, `category` (e.g., equipment/accessories/supplements)

## dim_customer
**Grain:** 1 row = 1 customer  
**Primary key:** `customer_id`  
**Main fields (examples):** `acquisition_channel`, `first_order_date`, `days_to_2nd_purchase`

## dim_channel
**Grain:** 1 row = 1 channel  
**Primary key:** `channel`  
**Example values:** Paid Search, Paid Social, Organic, Email, Affiliate
