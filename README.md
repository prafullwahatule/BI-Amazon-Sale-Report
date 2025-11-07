# Amazon Sales Dashboard – Power BI Project

## Project Overview
This project is a **Power BI-based interactive dashboard** designed to analyze and visualize Amazon sales data.  
The dashboard provides insights on product performance, fulfilment efficiency, regional sales trends, promotional effectiveness, and sales forecasting.  
It is aimed at helping stakeholders make **data-driven business decisions**.

---

## Problem Statement
Businesses often struggle with tracking and analyzing large volumes of sales data across multiple dimensions like product, region, fulfilment type, and promotions.  
Manual reporting is time-consuming, error-prone, and does not provide real-time actionable insights.  
Decision-makers need a **centralized, interactive dashboard** to understand performance, identify trends, and take informed actions quickly.

---

## Objectives
- **Centralize Sales Data:** Consolidate Amazon sales data from multiple sources into a single dashboard for easy access and analysis.  
- **Track Key Metrics:** Monitor global KPIs such as total sales, total orders, quantity sold, and average order value (AOV).  
- **Analyze Product Performance:** Identify top-selling categories, SKUs, and sizes to optimize inventory and marketing strategies.  
- **Monitor Fulfilment Efficiency:** Evaluate FBA vs FBM order processing, delivery efficiency, and operational dependency.  
- **Understand Regional Trends:** Analyze state-wise and city-wise sales distribution to target high-performing and underperforming regions.  
- **Evaluate Promotions:** Measure the effectiveness of promotional campaigns and understand their impact on sales growth.  
- **Forecast Sales Trends:** Predict future sales patterns using historical data to support strategic planning.  
- **Interactive Reporting:** Enable stakeholders to filter, slice, and drill-down data for detailed insights in real-time.

---

## 1. Data Cleaning & Transformation

### 1.1 KYD Data Cleaning Steps
The raw Amazon sales data was cleaned and transformed to ensure accuracy and consistency. Below are the applied steps:

| Sr. No. | Applied Steps |
|---------|---------------|
| 0 | Load CSV File |
| 1 | Remove Column `index` |
| 2 | Remove Column `Style` |
| 3 | Remove Column `ASIN` |
| 4 | Remove Column `ship-postal-code` |
| 5 | Remove Column `Unnamed: 22` |
| 6 | Remove Errors |
| 7 | Remove Blank Rows |
| 8 | Remove Duplicates |
| 9 | Remove Errors, Blank Rows, Duplicates after handling 0 in Qty |
| 10 | Add Column `Total Amount` |
| 11 | Remove Errors after handling 0 and null values in Total Amount |
| 12 | Add Column `Year` |
| 13 | Add Column `Month` |
| 14 | Add Column `Week` |
| 15 | Add Column `Order Type` |
| 16 | Add Column `Order Status Group` |
| 17 | Remove Column `Sales Channel` |
| 18 | Remove Column `Currency` |
| 19 | Remove Column `Country` |
| 20 | Add Column `Promotion Type` |



### 1.2 Data Cleaning: Rows & Columns Effect

The following table shows how the number of rows and columns changed after each cleaning/transformation step:

| Sr. No. | Rows Before | Rows After | Effect (Rows) | Columns Before | Columns After | Effect (Columns) |
|---------|------------|-----------|---------------|----------------|---------------|-----------------|
| 0 | 128975 | 128975 | 0 | 24 | 24 | 0 |
| 1 | 128975 | 128975 | 0 | 24 | 23 | 1 |
| 2 | 128975 | 128975 | 0 | 23 | 22 | 1 |
| 3 | 128975 | 128975 | 0 | 22 | 21 | 1 |
| 4 | 128975 | 128975 | 0 | 21 | 20 | 1 |
| 5 | 128975 | 128975 | 0 | 20 | 19 | 1 |
| 6 | 128975 | 128975 | 0 | 19 | 19 | 0 |
| 7 | 128975 | 128975 | 0 | 19 | 19 | 0 |
| 8 | 128975 | 128969 | 6 | 19 | 19 | 0 |
| 9 | 128969 | 116165 | 12804 | 19 | 19 | 0 |
| 10 | 116165 | 116165 | 0 | 19 | 20 | 1 |
| 11 | 116165 | 113698 | 2467 | 20 | 20 | 0 |
| 12 | 113698 | 113698 | 0 | 20 | 21 | 1 |
| 13 | 113698 | 113698 | 0 | 21 | 22 | 1 |
| 14 | 113698 | 113698 | 0 | 22 | 23 | 1 |
| 15 | 113698 | 113698 | 0 | 23 | 24 | 1 |
| 16 | 113698 | 113698 | 0 | 24 | 25 | 1 |
| 17 | 113698 | 113698 | 0 | 25 | 24 | 1 |
| 18 | 113698 | 113698 | 0 | 24 | 23 | 1 |
| 19 | 113698 | 113698 | 0 | 13 | 22 | 1 |
| 20 | 113698 | 113698 | 0 | 22 | 23 | 1 |

### 1.3 KYD Data Transformation
The following table shows the **columns before and after transformation**, including their purpose:

| Col No. | Column Name (Before) | Description / Purpose | Col No. | Column Name (After) | Description / Purpose |
|---------|--------------------|---------------------|---------|-------------------|---------------------|
| 1 | index | Row number (system generated) | 1 | Order ID | Unique order identification number |
| 2 | Order ID | Unique order identification number | 2 | Date | Final cleaned order date (proper date format) |
| 3 | Date | Order placed date (MM-DD-YY) | 3 | Year | Extracted year from the Date column |
| 4 | Status | Order current status | 4 | Month | Extracted month from Date column |
| 5 | Fulfilment | Who fulfilled the order | 5 | Week | Extracted week number of the year |
| 6 | Sales Channel | Platform used for sales | 6 | Status | Cleaned order status |
| 7 | ship-service-level | Shipping type | 7 | Order Status Group | Categorized order status |
| 8 | Style | Product style code | 8 | Fulfilment | Who fulfilled the order |
| 9 | SKU | Stock Keeping Unit | 9 | Shipping Type | Shipping method |
| 10 | Category | Product category | 10 | Order Type | Derived — “FBA” if Fulfilment = Amazon else “FBM” |
| 11 | Size | Product size | 11 | SKU | Stock Keeping Unit (unique product identifier) |
| 12 | ASIN | Amazon Standard ID | 12 | Category | Product category |
| 13 | Courier Status | Shipment progress status | 13 | Size | Product size |
| 14 | Qty | Quantity ordered | 14 | Courier Status | Shipment progress details |
| 15 | currency | Currency type | 15 | Qty | Quantity ordered per order ID |
| 16 | Amount | Total sale amount | 16 | Amount | Cleaned and converted total sale amount |
| 17 | ship-city | Shipping destination city | 17 | Total Amount | Derived as Qty × Amount |
| 18 | ship-state | Shipping destination state | 18 | City | Shipping destination city |
| 19 | ship-postal-code | Shipping postal code | 19 | State | Shipping destination state |
| 20 | ship-country | Shipping destination country | 20 | Promotion IDs | Cleaned promotion IDs or blank |
| 21 | promotion-ids | Promotion or coupon identifiers | 21 | B2B | Business-to-Business order indicator (Yes/No) |
| 22 | B2B | B2B indicator | 22 | Fulfilled By | Final fulfilment source (Easy Ship / Amazon / Merchant) |
| 23 | fulfilled-by | Fulfilment type | 23 | Promotion Type | Derived promotion type column |
| 24 | Unnamed: 22 | Extra blank column | - | - | Removed during cleaning |




---

## Dashboard Pages
1. **Home** – Logo and page navigation buttons  
2. **Overview** – High-level KPIs and overall sales analysis  
3. **Product** – Product performance and top-selling SKUs  
4. **Fulfilment** – FBA vs FBM performance and delivery efficiency  
5. **Region** – State and city-wise sales distribution  
6. **Promotion** – Promotional offer analysis and impact  
7. **Forecasting** – Monthly trends, seasonality, and future sales prediction

---

## 1. Home Page

**Screenshot:**  
<img width="1404" height="796" alt="Screenshot 2025-11-08 012636" src="https://github.com/user-attachments/assets/38f9a4d8-e333-4c08-a196-51e98efeebbc" />

**Purpose:**  
The Home page serves as the **entry point** to the dashboard.  
It primarily contains:  
- Dashboard logo  
- Navigation buttons to access other pages

---

### Global KPIs
These KPIs are **visible across all pages** at the top:  
- **Total Sales (₹):** Shows total revenue from all orders  
- **Total Orders:** Total number of unique orders placed  
- **Total Quantity Sold:** Total number of products sold  
- **Average Order Value (AOV):** Average revenue per order

### Global Filters / Slicers
These filters are **applied across all pages**:  
- Category  
- Date  
- City  
- Month  
- Status  
- Size  
- Order Status Group

---
## 2. Overview Page

**Screenshot:**  
<img width="1406" height="797" alt="Screenshot 2025-11-08 012733" src="https://github.com/user-attachments/assets/f87dad0b-52ea-4ea9-9111-d79376fa24fd" />

**Purpose:**  
The Overview page provides a **high-level summary of Amazon sales performance**.  
It allows stakeholders to quickly understand overall business trends, monitor sales performance, and identify growth opportunities.


### Page-Specific Visuals
The Overview page focuses on visualizing metrics that **summarize overall performance**:

- **Top 5 Category by Total Sales:**  
  Highlights the product categories generating the highest revenue.  
  *Purpose:* Helps stakeholders identify which product categories drive the most business and which are underperforming.

- **Fulfilment by Total Sales:**  
  Compares revenue contributed by Amazon (FBA) and Merchant (FBM) fulfilment.  
  *Purpose:* Helps understand operational dependency and the impact of fulfilment methods on total sales.

- **State Wise Total Sales:**  
  Shows total sales distributed across all states on a map.  
  *Purpose:* Visualizes regional performance, allowing stakeholders to spot high-performing and low-performing regions geographically.

- **Promotion Type by Total Sales:**  
  Compares revenue generated from orders with promotions vs without promotions.  
  *Purpose:* Evaluates the effectiveness of marketing campaigns and discounts in driving sales.

- **Monthly Sales Trend:**  
  Line chart showing total sales month-by-month.  
  *Purpose:* Tracks seasonality, growth trends, and identifies peaks or dips in revenue over time.


### Visuals / Charts on Overview Page 
| Sr. No. | Name | Visual Type | Columns Used | Purpose / Insight |
|---------|------|-------------|--------------|-----------------|
| 1 | Top 5 Category by Total Sales | Stacked Column Chart | Category, Total Amount | Identifies top-performing product categories and revenue contribution. |
| 2 | Fulfilment by Total Sales | Donut Chart | Fulfilment, Total Amount | Shows sales share between Amazon (FBA) and Merchant (FBM). |
| 3 | State Wise Total Sales | Filled Map | State, Total Amount | Highlights state-wise sales distribution to identify regional performance. |
| 4 | Promotion Type by Total Sales | Stacked Bar Chart | Promotion IDs, Total Amount | Compares revenue from promotional vs non-promotional orders. |
| 5 | Monthly Sales Trend | Line Chart | Month, Total Amount | Displays monthly sales trends and seasonality patterns. |


### Insights for Stakeholders
- Quickly identify **high-performing product categories** and those needing attention.  
- Understand the **impact of fulfilment types** (FBA vs FBM) on overall sales.  
- Detect **regional trends** and target high-performing or underperforming states for growth.  
- Assess **effectiveness of promotional campaigns** in boosting sales.  
- Monitor **seasonality and monthly revenue patterns** to support inventory, marketing, and operational planning.  

---

## 3. Product Page

**Screenshot:**  
<img width="1402" height="794" alt="Screenshot 2025-11-08 012814" src="https://github.com/user-attachments/assets/44a30531-ce9d-43ff-b416-504c5b91c1a2" />

**Purpose:**  
The Product page provides insights into **product-level performance**.  
It allows stakeholders to:  
- Identify top-selling **categories** and **SKUs**  
- Understand **product size performance**  
- Optimize **inventory planning**, **marketing campaigns**, and **sales strategies**  


### Page-Specific KPI's

- **Best-Selling Category:**  
  Shows which product category generated the highest total sales.  
  *Insight:* Helps stakeholders focus on the most profitable categories and make decisions about stock and promotions.

- **Top Performing Size:**  
  Highlights which product size sells the most units.  
  *Insight:* Guides production and inventory decisions by showing size preferences of customers.

- **Top SKU by Sales:**  
  Displays the SKU generating maximum revenue.  
  *Insight:* Helps in prioritizing marketing, inventory allocation, and promotions for top-performing products.

- **Average Category Revenue (₹):**  
  Calculates the average sales per category.  
  *Insight:* Enables comparison across categories to understand overall product performance and potential improvement areas.


### Visuals / Charts on Product Page

| Sr. No. | Name | Visual Type | Columns Used | Purpose / Insight |
|---------|------|-------------|--------------|-----------------|
| 1 | Top 3 SKU by Total Sales | Donut Chart | SKU, Total Amount | Identifies **top 3 revenue-generating SKUs**. Helps focus on products contributing the most to total sales. |
| 2 | Top 3 SKU by Total Qty | Donut Chart | SKU, Qty | Shows **top 3 selling SKUs by quantity**. Useful for inventory management and understanding demand trends. |
| 3 | Total Sales By Size | Stacked Bar Chart | Size, Total Amount | Reveals which **size variants generate the highest revenue**. Assists in optimizing size-wise production and stock levels. |
| 4 | Qty By Month & Category | Line Chart | Qty, Month, Category | Tracks **monthly demand trends per category**. Helps detect seasonality and identify periods of high demand for specific categories. |
| 5 | Total Sales By Category | Stacked Column Chart | Category, Total Amount | Measures **revenue contribution of each product category**. Supports strategic planning, marketing, and inventory decisions. |


**Insights for Stakeholders:**  
- Focus on top-performing SKUs and categories to maximize revenue.  
- Adjust inventory levels based on top-selling sizes and trends.  
- Plan marketing campaigns around high-performing products.  
- Analyze monthly trends to anticipate demand spikes or dips.  


---
## 4. Fulfilment Page

**Screenshot:**  
<img width="1404" height="797" alt="Screenshot 2025-11-08 012844" src="https://github.com/user-attachments/assets/98651e2a-f7b3-4c12-8860-ed1aa459340d" />

**Purpose:**  
The Fulfilment page provides insights into **order processing and delivery efficiency**.  
It helps stakeholders:  
- Evaluate **Amazon-fulfilled (FBA) vs Merchant-fulfilled (FBM)** performance  
- Monitor **delivery success rates and operational efficiency**  
- Identify areas to improve **logistics and fulfilment strategy**


### KPIs on Fulfilment Page

- **Total Orders (Fulfilment):**  
  Total number of orders processed.  
  *Insight:* Shows overall operational volume and helps track order handling efficiency.

- **Avg Delivery Value (₹):**  
  Compares the average order value for each fulfilment type.  
  *Insight:* Helps identify which fulfilment model brings higher revenue per order.

- **Delivered Orders %:**  
  Percentage of total delivered orders.  
  *Insight:* Tracks delivery efficiency and helps monitor fulfilment reliability.

- **FBA % Share:**  
  Contribution of Amazon-fulfilled orders in total sales.  
  *Insight:* Indicates dependence on Amazon’s fulfilment network.

- **FBM % Share:**  
  Contribution of Merchant-fulfilled orders in total sales.  
  *Insight:* Highlights the role of independent seller fulfilment in overall revenue.

- **FBA Sales (₹):**  
  Total revenue generated from Amazon-fulfilled orders.  
  *Insight:* Measures Amazon’s direct contribution to total sales.

- **FBM Sales (₹):**  
  Total revenue generated from Merchant-fulfilled orders.  
  *Insight:* Measures revenue contribution from seller-managed fulfilment.

### Visuals / Charts on Fulfilment Page

| Sr. No. | Name | Visual Type | Columns Used | Purpose / Insight |
|---------|------|-------------|--------------|-----------------|
| 1 | Qty by Fulfilment | Donut Chart | Qty, Fulfilment | Shows quantity distribution between FBA and FBM. Helps compare fulfilment efficiency. |
| 2 | Avg Delivery Value By Fulfilment | Stacked Bar Chart | Avg Delivery Value, Fulfilment | Compares average delivery value by fulfilment type to identify which model brings higher order value. |
| 3 | Delivered Orders % by Month & Year | Line Chart | Delivered Order %, Month, Year | Tracks delivery success trends over time. Helps monitor seasonal performance and logistics issues. |
| 4 | Qty by City & Fulfilment | Stacked Bar Chart | City, Qty, Fulfilment | Highlights quantity handled by each fulfilment type across cities. Supports operational and logistics planning. |
| 5 | FBA Share % | Donut Chart | Order Type, Total Amount | Shows percentage of total sales fulfilled via Amazon FBA. Useful to measure Amazon’s operational dominance. |
| 6 | FBM Share % | Donut Chart | Order Type, Total Amount | Shows percentage of total sales fulfilled via Merchant FBM. Helps evaluate merchant-driven performance. |


### Insights for Stakeholders
- Identify which fulfilment type (FBA or FBM) drives **more revenue and order volume**.  
- Monitor **delivery efficiency** over time to prevent delays or fulfilment bottlenecks.  
- Optimize logistics by analyzing **city-wise order quantities** and trends.  
- Understand the **balance between Amazon and Merchant fulfilment**, enabling informed operational decisions.  

---

## 5. Region Page

**Screenshot:**  
<img width="1405" height="799" alt="Screenshot 2025-11-08 012946" src="https://github.com/user-attachments/assets/3ccd2b44-ff08-4934-94e4-53d1b9b0588b" />

**Purpose:**  
The Region page provides insights into **state-wise and city-wise sales performance**.  
It helps stakeholders:  
- Identify **high-performing and underperforming regions**  
- Make **data-driven regional strategies**  
- Allocate resources and plan promotions based on **regional sales trends**


### KPIs on Region Page

- **Top State by Sales:**  
  Identifies the state generating the highest total sales.  
  *Insight:* Helps focus marketing and operational efforts on the most profitable regions.

- **Top City by Sales:**  
  Finds the city with the maximum revenue contribution.  
  *Insight:* Highlights key urban markets driving sales, aiding targeted campaigns.



### Visuals / Charts on Region Page

| Sr. No. | Name | Visual Type | Columns Used | Purpose / Insight |
|---------|------|-------------|--------------|-----------------|
| 1 | Sold Qty By State | Map | Qty, State | Visualizes total quantity sold across states. Helps stakeholders quickly identify high-volume regions. |
| 2 | Top 5 State by Total Sales | Stacked Bar Chart | State, Total Sales | Highlights the top 5 states generating the highest total sales. Supports resource allocation and strategy planning. |
| 3 | Top 5 City by Total Sales | Stacked Bar Chart | City, Total Sales | Shows top 5 cities contributing most to overall sales. Helps in city-level marketing and logistics decisions. |
| 4 | Bottom 5 State by Total Sales | Stacked Bar Chart | State, Total Sales | Displays the 5 lowest-performing states. Enables targeted improvement initiatives. |
| 5 | Regional Overview Table | Table | State, City, Qty, Total Amount, Fulfilment | Provides a detailed regional summary including sales, quantity, and fulfilment split. Supports deeper analysis of regional trends. |


### Insights for Stakeholders
- Identify regions contributing **most and least** to sales revenue.  
- Prioritize **promotions, inventory, and fulfilment** in high-performing states/cities.  
- Detect **underperforming areas** and plan corrective actions.  
- Use data for **logistics optimization** and regional market strategy.  

---

## 6. Promotion Page

**Screenshot:**  
<img width="1407" height="799" alt="Screenshot 2025-11-08 013015" src="https://github.com/user-attachments/assets/7951c19a-5b84-4b8d-bf8b-55c955d3ad0c" />

**Purpose:**  
The Promotion page provides insights into **promotional offer performance**.  
It allows stakeholders to:  
- Understand the share of sales generated organically versus via promotions.  
- Identify which promotions drive the highest quantity and revenue.  
- Evaluate the effectiveness of marketing campaigns in boosting sales.


### Page-Specific KPI's

- **No Promotion % Share:**  
  Shows the percentage of total sales that were made without any promotion.  
  *Insight:* Helps stakeholders understand how much revenue is generated organically, indicating brand strength and product demand without discounts.  

- **Promotion Applied % Share:**  
  Shows the percentage of total sales that occurred under promotions or discounts.  
  *Insight:* Measures the effectiveness and reach of promotional campaigns, enabling marketing teams to evaluate ROI of offers.



### Visuals / Charts on Promotion Page

| Sr. No. | Name | Visual Type | Columns Used | Purpose / Insight |
|---------|------|-------------|--------------|-----------------|
| 1 | Promotion Type % by Qty | Donut Chart | Promotion Type, Qty | **Displays quantity distribution between orders with promotions and without promotions.** Stakeholders can quickly see what portion of sales is driven by offers versus organic sales. |
| 2 | Sales by Month & Promotion Type | Line & Clustered Column Chart | Month, Promotion Type, Total Amount | **Compares monthly sales trends for promotional vs non-promotional orders.** Helps identify which months promotions had maximum impact and seasonal patterns in offer effectiveness. |
| 3 | Sales by Size & Qty | Line Chart | Total Amount, Size, Qty | **Shows variation in sales and quantities across product sizes during promotions.** Supports size-specific promotion planning and inventory allocation. |
| 4 | Top 5 Promotion IDs by Qty | Stacked Bar Chart | Promotion IDs, Qty | **Highlights the top 5 promotion campaigns driving highest order quantities.** Enables marketing teams to evaluate the most effective promotions for future campaigns. |
| 5 | Total Sales By Promotion Type | Donut Chart | Total Amount, Promotion Type | **Compares revenue generated under each promotion type.** Helps stakeholders see which type of promotion contributed most to sales and plan marketing strategies accordingly. |


### Filters / Slicers on Promotion Page

| Sr. No. | Filter / Slicer Name | Used Column |
|---------|-------------------|-------------|
| 1 | Business 2 Business | B2B |  
  *Insight:* Allows filtering sales and promotions specifically for B2B orders to evaluate how offers perform in the business segment. |
| 2 | Fulfilment | Fulfilment |  
  *Insight:* Enables analysis of promotions by fulfilment type (Amazon FBA vs Merchant FBM), helping operations and marketing teams understand impact per fulfilment channel.


### Insights for Stakeholders
- Understand **organic vs promotional sales** and overall campaign effectiveness.  
- Identify **top-performing promotions** and their impact on quantity and revenue.  
- Plan **size-specific or segment-specific promotions** using quantity and revenue data.  
- Evaluate performance by **B2B segment and fulfilment type** for targeted marketing strategies.  

---

## 7. Forecasting Page

**Screenshot:**  
<img width="1407" height="797" alt="Screenshot 2025-11-08 013041" src="https://github.com/user-attachments/assets/ac066690-de9b-4cce-b6d5-b80c1f9f8b0d" />


**Purpose:**  
The Forecasting page provides insights into **monthly sales trends, seasonality, and future sales predictions**.  
It allows stakeholders to:  
- Analyze historical sales patterns.  
- Identify peak and low-demand months.  
- Plan inventory, marketing, and operational strategies.  
- Make data-driven forecasts for upcoming months.


### Page-Specific KPI's

- **Avg Monthly Sales (₹):**  
  Calculates the average sales per month.  
  *Insight:* Helps stakeholders understand seasonal trends and expected revenue, enabling better resource allocation.

- **Highest Sales Month:**  
  Identifies the month with the maximum total sales.  
  *Insight:* Enables planning for high-demand months, such as scaling stock, logistics, or marketing campaigns.


### Visuals / Charts on Forecasting Page

| Sr. No. | Name | Visual Type | Columns Used | Purpose / Insight |
|---------|------|-------------|--------------|-----------------|
| 1 | Order Over Status | Line Chart | Order Status Group, Qty | **Tracks the movement of orders by status over time.** Helps stakeholders understand fulfillment and cancellation trends. |
| 2 | Qty Trend Over Time | Line Chart | Month, Qty | **Shows month-wise changes in ordered quantity.** Useful to detect seasonality or spikes in demand. |
| 3 | Sales Trend Over Time | Line Chart | Month, Total Amount | **Displays overall monthly sales growth trends.** Supports business planning and trend analysis. |
| 4 | Category Wise Monthly Trend | Area Chart | Month, Total Amount, Category | **Highlights monthly performance of product categories.** Reveals seasonal demand patterns per category for inventory planning. |
| 5 | Fulfilment Type Trend | Stacked Column Chart | Month, Fulfilment, Total Amount | **Compares sales by FBA and FBM fulfilment per month.** Helps assess operational efficiency and channel performance. |
| 6 | Business To Business Trend | Stacked Column Chart | B2B, Total Amount | **Shows revenue contribution from B2B vs B2C orders.** Supports segment-specific strategy and sales planning. |
| 7 | Sales by Shipping Type & Month | Donut Chart | Month, Shipping Type, Total Amount | **Displays monthly sales distribution by shipping type.** Helps optimize delivery methods and assess customer preferences. |


### Insights for Stakeholders
- Understand **historical sales patterns** and identify high-demand periods.  
- Detect **category-specific seasonal trends** to plan production and inventory.  
- Evaluate **fulfilment efficiency and channel performance** over time.  
- Optimize **B2B vs B2C strategies** based on revenue contribution.  
- Plan **marketing and logistics** for upcoming months using predicted trends.
