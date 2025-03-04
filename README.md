# Dashboards
<div class='tableauPlaceholder' id='viz1741124370462' style='position: relative'><noscript><a href='#'><img alt='Dashboard 1 ' src='https:&#47;&#47;public.tableau.com&#47;static&#47;images&#47;Sa&#47;Sales_17411241874230&#47;Dashboard1&#47;1_rss.png' style='border: none' /></a></noscript><object class='tableauViz'  style='display:none;'><param name='host_url' value='https%3A%2F%2Fpublic.tableau.com%2F' /> <param name='embed_code_version' value='3' /> <param name='site_root' value='' /><param name='name' value='Sales_17411241874230&#47;Dashboard1' /><param name='tabs' value='no' /><param name='toolbar' value='yes' /><param name='static_image' value='https:&#47;&#47;public.tableau.com&#47;static&#47;images&#47;Sa&#47;Sales_17411241874230&#47;Dashboard1&#47;1.png' /> <param name='animate_transition' value='yes' /><param name='display_static_image' value='yes' /><param name='display_spinner' value='yes' /><param name='display_overlay' value='yes' /><param name='display_count' value='yes' /><param name='language' value='en-GB' /></object></div>                <script type='text/javascript'>                    var divElement = document.getElementById('viz1741124370462');                    var vizElement = divElement.getElementsByTagName('object')[0];                    if ( divElement.offsetWidth > 800 ) { vizElement.style.width='100%';vizElement.style.height=(divElement.offsetWidth*0.75)+'px';} else if ( divElement.offsetWidth > 500 ) { vizElement.style.width='100%';vizElement.style.height=(divElement.offsetWidth*0.75)+'px';} else { vizElement.style.width='100%';vizElement.style.height='1277px';}                     var scriptElement = document.createElement('script');                    scriptElement.src = 'https://public.tableau.com/javascripts/api/viz_v1.js';                    vizElement.parentNode.insertBefore(scriptElement, vizElement);                </script>

This interactive dashboard tracks sales, quantity, and profit trends with dynamic year selection. It features YoY growth indicators (▲/▼), weekly trends, and sub-category performance. Custom formatting highlights key insights, helping businesses analyze trends and optimize sales strategies
📊 Tableau Sales Performance Dashboard – Project Documentation
📌 Project Overview
This Tableau dashboard provides a comprehensive sales performance analysis, helping stakeholders track key metrics such as total sales, quantity sold, profit trends, and sub-category comparisons over time. The dashboard is interactive, allowing users to filter data dynamically using a parameter-based year selection.

🔹 Data Modeling & Structure
The dashboard is built using multiple CSV files:

Customers.csv – Contains customer details (ID, Segment, Region).
Orders.csv – Includes transaction-level details (Order ID, Date, Sales, Quantity, Profit).
Products.csv – Lists product categories, subcategories, and IDs.
Location.csv – Contains geographic data for mapping (Country, State, Postal Code).
Data Relationships:
Orders table is linked to Customers via Customer ID.
Orders table is linked to Products via Product ID.
Orders table is linked to Location via Postal Code.
This star schema structure ensures optimized performance while filtering and aggregating data.

🔹 Key Calculated Fields (Dynamically Computed Metrics)
1️⃣ Total Sales vs. Previous Year (YoY Growth)
Tableau
Copy
Edit
YoY Growth = (SUM([Sales]) - LOOKUP(SUM([Sales]), -1)) / LOOKUP(SUM([Sales]), -1)
This formula calculates the percentage change in total sales compared to the previous year.
Used in the Total Sales KPI with an upward/downward trend indicator.
2️⃣ Sales Quantity YoY Comparison
Tableau
Copy
Edit
YoY Quantity Change = (SUM([Quantity]) - LOOKUP(SUM([Quantity]), -1)) / LOOKUP(SUM([Quantity]), -1)
Used in the Quantity KPI to display the growth percentage vs. previous year.
3️⃣ Custom Header Formatting with Trend Indicator
To display an upward arrow (▲) or downward arrow (▼) based on YoY sales growth:

Tableau
Copy
Edit
IF [YoY Growth] > 0 THEN "▲ " + STR(ROUND([YoY Growth]*100,2)) + "%" 
ELSE "▼ " + STR(ROUND([YoY Growth]*100,2)) + "%" END
Green "▲" → Indicates sales increase.
Red "▼" → Indicates sales decline.
4️⃣ Running Total for Weekly Sales & Profit Trends
Tableau
Copy
Edit
RUNNING_SUM(SUM([Sales]))
Used in the Weekly Trend Line Chart for cumulative sales visualization.
🔹 Creating Parameters & Dynamic Filters
1️⃣ Year Selection Parameter
Created a parameter called select Year (Integer type) to allow users to choose a year dynamically.
Added values: 2020, 2021, 2022, 2023.
Used in a calculated field:
Tableau
Copy
Edit
IF YEAR([Order Date]) = [select Year] THEN [Sales] ELSE NULL
This ensures that only the selected year’s data is displayed.
Linked with all charts & KPIs for interactive filtering.
2️⃣ Dynamic Filters
Applied filters using:
Date (Order Date)
Product Sub-category
Customer Segment
Region
This allows users to drill down into specific time periods or product categories.

🔹 Visual Elements & Charts
1️⃣ KPI Cards
Total Sales (compared to previous year)
Quantity Sold (YoY change percentage)
Profit Trend
Indicators (▲ / ▼) for performance tracking
2️⃣ Weekly Sales & Profit Trend
Line charts for sales & profit across weeks.
Displays weekly seasonality & fluctuations.
3️⃣ Sub-Category Comparison
Bar chart visualizing sales and profit by product sub-category.
Color-coded to highlight high and low-performing categories.
4️⃣ Yearly Comparison Line Chart
Shows sales growth over time with the ability to select a specific year.
🔹 Use Cases of the Dashboard
✔ Sales Performance Tracking

Helps business leaders track total revenue, profit, and sales trends.
✔ Identifying High & Low Performing Categories

The Sub-Category Comparison chart allows stakeholders to identify which products contribute most to revenue.
✔ Yearly Sales Trend Analysis

Users can select different years to compare sales performance dynamically.
✔ Understanding Weekly Trends

Helps in forecasting future sales by recognizing seasonal sales patterns.
✔ Interactive & Customizable Reporting

Enables sales teams to filter data by product, region, or customer type for detailed analysis.
🚀 Summary
✅ Data Model: Star schema with Orders, Customers, Products, and Location tables.
✅ Calculated Fields: YoY Growth, Running Totals, Custom KPI Headers.
✅ Parameters: Select Year dynamically filters all visuals.
✅ Custom Formatting: ▲/▼ markers for trend visualization.
✅ Use Cases: Sales performance tracking, forecasting, and sub-category analysis.

Would you like me to help enhance this dashboard further, such as adding forecasting, advanced filters, or profit margin calculations? 🚀

You said:
write a short decription noe
ChatGPT said:
📊 Tableau Sales Performance Dashboard
This interactive Tableau dashboard provides a comprehensive view of sales performance, allowing users to track total sales, quantity sold, and profit trends over time. The dashboard features dynamic year selection using a parameter, enabling users to analyze specific time periods.

Key insights include YoY growth indicators (▲/▼), a weekly sales and profit trend, and a sub-category performance comparison. Custom formatting highlights upward/downward trends, while filters allow for deep analysis by product, region, and customer segment.

This dashboard helps businesses monitor key metrics, identify top-performing categories, and optimize sales strategies. 🚀
