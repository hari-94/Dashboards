# 📊 Tableau Sales Performance Dashboard

## 🔗 View the Interactive Dashboard
[View on Tableau Public](https://public.tableau.com/views/Sales_17411241874230/Dashboard1)

![Dashboard Preview](https://public.tableau.com/static/images/Sa/Sales_17411241874230/Dashboard1/1.png)

## 📌 Project Overview
This Tableau dashboard provides a comprehensive analysis of sales performance, enabling users to track key metrics such as **total sales, quantity sold, profit trends, and sub-category comparisons** over time. The dashboard is **interactive**, allowing for dynamic filtering using a **year selection parameter**.

## 🔹 Data Modeling & Structure
The dashboard integrates multiple CSV datasets:
- `Customers.csv` – Customer details (ID, Segment, Region)
- `Orders.csv` – Transaction details (Order ID, Date, Sales, Quantity, Profit)
- `Products.csv` – Product categories and subcategories
- `Location.csv` – Geographic data (Country, State, Postal Code)

### **Schema Design**
The data follows a **star schema**, ensuring optimized performance:
- **Orders** table links to **Customers** via `Customer ID`
- **Orders** table links to **Products** via `Product ID`
- **Orders** table links to **Location** via `Postal Code`

## 🧮 Key Calculated Fields

### 1️⃣ **Year-over-Year (YoY) Growth**
```tableau
YoY Growth = (SUM([Sales]) - LOOKUP(SUM([Sales]), -1)) / LOOKUP(SUM([Sales]), -1)
```
📌 This formula calculates the percentage change in sales compared to the previous year and is used in KPI indicators.

### 2️⃣ **Sales Quantity YoY Comparison**
```tableau
YoY Quantity Change = (SUM([Quantity]) - LOOKUP(SUM([Quantity]), -1)) / LOOKUP(SUM([Quantity]), -1)
```

### 3️⃣ **Custom KPI Header with Trend Indicators**
```tableau
IF [YoY Growth] > 0 THEN "▲ " + STR(ROUND([YoY Growth]*100,2)) + "%" 
ELSE "▼ " + STR(ROUND([YoY Growth]*100,2)) + "%" END
```
✅ **Green ▲** → Sales increase  
❌ **Red ▼** → Sales decrease

### 4️⃣ **Running Total for Weekly Sales & Profit Trends**
```tableau
RUNNING_SUM(SUM([Sales]))
```
Used in weekly trend charts to visualize cumulative sales performance.

## 🎛️ Dynamic Filtering & Parameters

### 1️⃣ **Year Selection Parameter**
- Created an **integer parameter** `select Year` for dynamic year selection.
- Applied in calculated fields:
```tableau
IF YEAR([Order Date]) = [select Year] THEN [Sales] ELSE NULL
```
- Dynamically filters all charts & KPIs.

### 2️⃣ **Filters Applied**
✅ Order Date  
✅ Product Sub-category  
✅ Customer Segment  
✅ Region  
Allows users to drill down into specific time periods and product categories.

## 📊 **Visual Elements & Charts**
- **KPI Cards**: Total Sales, Quantity Sold, Profit Trend, YoY Growth Indicators
- **Weekly Sales & Profit Trend**: Line chart for weekly fluctuations
- **Sub-Category Comparison**: Sales and profit bar charts by category
- **Yearly Sales Trend**: Line chart showing long-term sales performance

## 🚀 Use Cases
✅ **Sales Performance Tracking** – Monitor revenue, profit, and sales trends  
✅ **Identifying High & Low Performing Categories** – Optimize product strategy  
✅ **Yearly Sales Trend Analysis** – Understand long-term growth patterns  
✅ **Weekly Trends for Forecasting** – Identify seasonal patterns for better planning  
✅ **Custom Reporting** – Analyze sales across regions, product types, and time periods  

## ✅ Summary
✔ **Data Model**: Star schema with Orders, Customers, Products, and Location tables  
✔ **Calculated Fields**: YoY Growth, Running Totals, Custom KPI Headers  
✔ **Dynamic Parameters**: Year selection for filtering all visuals  
✔ **Custom Formatting**: ▲/▼ indicators for sales performance  
✔ **Interactive Analysis**: Drill-down capabilities for deeper insights  



