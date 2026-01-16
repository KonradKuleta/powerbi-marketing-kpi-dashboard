# Data Generation (Synthetic)
This project uses a synthetic dataset generated in Python to simulate a **fitness products e-commerce store**
in Germany (2025) with product categories such as **equipment, accessories, and supplements**.

Generation assumptions (high level):
- Seasonality: revenue peaks in **Q4**.
- Channel mix: **Paid Search, Paid Social, Organic, Email, Affiliate**.
- Paid media spend is generated for paid channels; **Organic has 0 spend**.
- Product performance includes a "hero product" effect (revenue concentrated among top products).
- Monthly revenue targets are generated and mapped to the calendar period.
  
## Files in this folder
This folder contains the exported tables used in the Power BI model:
- Dimensions: `dim_date`, `dim_product`, `dim_customer`, `dim_channel`
- Facts: `fact_orders`, `fact_order_items`, `fact_marketing_spend_daily`, `fact_targets`
