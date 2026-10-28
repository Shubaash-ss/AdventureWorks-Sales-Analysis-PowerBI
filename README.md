# AdventureWorks-Sales-Analysis-PowerBI
# 🚲 AdventureWorks Sales & Profitability Analysis (Power BI)

## 📌 Project Overview
This project delivers an end-to-end Business Intelligence solution built using **Power BI Desktop**. The analysis evaluates company performance for **AdventureWorks** (H1 2017 (Jan–Jun 2017)), tracking **Revenue, Profit, Costs, Customer Growth, Product Profitability, and Geographic Performance**.

---

## 🏗️ Data Architecture & Star Schema
The raw dataset comprises 6 tables structured into a **Star Schema** model:
- **Fact Table:** `AdventureWorks_Sales_2017`
- **Dimension Tables:** `AdventureWorks_Products`, `AdventureWorks_Product_Subcategories`, `AdventureWorks_Customers`, `AdventureWorks_Territories`, `AdventureWorks_Calendar`

---

## 📊 Key DAX Measures Formulated

### 1. Core Financial & Volume KPIs
```dax
Total Revenue = SUMX(AdventureWorks_Sales_2017, AdventureWorks_Sales_2017[Order Quantity] * RELATED(AdventureWorks_Products[Product Price]))

Total Cost = SUMX(AdventureWorks_Sales_2017, AdventureWorks_Sales_2017[Order Quantity] * RELATED(AdventureWorks_Products[Product Cost]))

Total Profit = [Total Revenue] - [Total Cost]

Profit Percentage = DIVIDE([Total Profit], [Total Revenue], 0)

Total Quantity Sold = SUM(AdventureWorks_Sales_2017[Order Quantity])

Total Orders = DISTINCTCOUNT(AdventureWorks_Sales_2017[Order Number])

2. Time Intelligence Measures

YTD Revenue = TOTALYTD([Total Revenue], AdventureWorks_Calendar[Date])

MTD Revenue = TOTALMTD([Total Revenue], AdventureWorks_Calendar[Date])

QTD Revenue = TOTALQTD([Total Revenue], AdventureWorks_Calendar[Date])

Previous Month Revenue = CALCULATE([Total Revenue], DATEADD(AdventureWorks_Calendar[Date], -1, MONTH))

MoM Revenue Change = [Total Revenue] - [Previous Month Revenue]

MoM Revenue Growth % = DIVIDE([MoM Revenue Change], [Previous Month Revenue], 0)

3. Contribution Analysis

Revenue Contribution % = DIVIDE([Total Revenue], CALCULATE([Total Revenue], ALL(AdventureWorks_Products)), 0)




🖥️ Dashboard Architecture
Page 1: Executive Overview
KPI Summary Cards: Highlighting Total Revenue, Total Profit, Total Cost, and Total Customers.

Revenue Trend Line Chart: Tracking monthly sales performance across 2017.

MoM Revenue Growth KPI: Conditional dynamic color formatting showing positive or negative month-over-month shifts.

Page 2: Product Analysis
Top 10 Products Bar Chart: Identifies peak revenue-generating individual items.

Revenue vs. Cost Scatter Chart: Visualizes product margins and highlights high-cost outliers.

Subcategory Bar Chart: Clear comparative representation of subcategory revenue performance.

Page 3: Customer & Regional Insights
Territory Filled Map: Global visual representation of revenue across territories and countries.

Customer Leaderboard Table: Ranked listing of top revenue-generating customers by order volume and total spend.

🛠️ Tools & Technologies Used
Power BI Desktop

DAX (Data Analysis Expressions)

Power Query (ETL)

Excel (Data Source)


