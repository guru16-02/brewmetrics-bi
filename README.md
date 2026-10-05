# BrewMetrics Coffee Co. — BI Analytics Solution

A version-controlled Power BI project (.pbip) monitoring store performance, product category distributions, and seasonal sales shifts across four operational hubs.

## Data Model Architecture
The solution converts flat transactional data into an optimized Star Schema:
* **`Fact_Sales`**: Granular record of transactions containing transaction keys, order dates, quantities, and total monetary amounts.
* **`Dim_Date`**: Time intelligence dimension enabling continuous date tracking and monthly roll-ups.
* **`Dim_City` & `Dim_StoreFormat`**: Geographic and architectural profiles covering Coimbatore, Chennai, Bengaluru, and Hyderabad, along with format types (Flagship, Kiosk, Drive-Thru).
* **`Dim_Product`**: Master list of products spanning Bakery, Coffee, and Merchandise.

## Key Business Insights
1. **Seasonal Demand Surges**: Cold Brew revenue spikes heavily across April and May, representing peak seasonal summer demand before declining sharply in June.
2. **Regional Dominance**: Bengaluru leads company-wide performance, consistently outpacing the other three cities.