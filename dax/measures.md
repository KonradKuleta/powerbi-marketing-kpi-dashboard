# DAX Measures

**KPI scope:** ROAS / CPA / CAC / AOV are calculated for **paid marketing channels only** (organic excluded),
unless stated otherwise.

```DAX
Net Revenue = SUM(fact_orders[order_net_revenue])

Paid Revenue =
CALCULATE(
    [Net Revenue],
    fact_orders[channel] <> "Organic"
)

Non-Organic Orders =
CALCULATE(
    [Orders],
    fact_orders[channel] <> "Organic"
)

Paid Spend =
CALCULATE(
    [Marketing Spend],
    fact_marketing_spend_daily[channel] <> "Organic"
)

AOV = DIVIDE([Paid Revenue], [Non-Organic Orders])

CPA =
DIVIDE ( [Paid Spend], [Non-Organic Orders] )

ROAS =
DIVIDE( [Paid Revenue], [Paid Spend] )

CAC =
DIVIDE( [Paid Spend], [New Customers] )

Product Rank (Revenue) =
RANKX(
    ALL(dim_product[product_name]),
    [Net Revenue(Orders)],
    ,
    DESC,
    DENSE
)

Revenue Target =
CALCULATE (
    SUM ( fact_targets[target_value] ),
    fact_targets[metric] = "Revenue",
    TREATAS ( VALUES ( dim_date[year_month] ), fact_targets[period] )
)

Revenue % of Target =
DIVIDE ( [Net Revenue], [Revenue Target] )
