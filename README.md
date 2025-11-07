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

### 1.2 KYD Data Transformation
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


### 1.3 Data Cleaning: Rows & Columns Effect

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
The Home page serves as the entry point to the dashboard. It primarily contains the dashboard logo and navigation buttons to access other pages.

---

## 2. Overview Page

**Screenshot:**  
<img width="1406" height="797" alt="Screenshot 2025-11-08 012733" src="https://github.com/user-attachments/assets/f87dad0b-52ea-4ea9-9111-d79376fa24fd" />
 

**Purpose:**  
The Overview page provides a **high-level summary of Amazon sales performance**. It allows stakeholders to quickly understand overall business trends and key metrics.

**Global KPIs:**  
These KPIs are displayed at the top of the page and are visible across all pages:  
- **Total Sales (₹):** Shows total revenue from all orders.  
- **Total Orders:** Total number of unique orders placed.  
- **Total Quantity Sold:** Total number of products sold.  
- **Average Order Value (AOV):** Average revenue per order.

**Visuals / Charts on Overview Page:**  
| Sr. No. | Name | Visual Type | Columns Used | Purpose / Insight |
|---------|------|-------------|--------------|-----------------|
| 1 | Top 5 Category by Total Sales | Stacked Column Chart | Category, Total Amount | Shows which product categories generate the highest revenue. |
| 2 | Fulfilment by Total Sales | Donut Chart | Fulfilment, Total Amount | Compares contribution of Amazon (FBA) vs Merchant (FBM) fulfilment to total sales. |
| 3 | State Wise Total Sales | Filled Map | State, Total Amount | Displays total sales distribution across states. |
| 4 | Promotion Type by Total Sales | Stacked Bar Chart | Promotion IDs, Total Amount | Compares sales generated from promotional vs non-promotional orders. |
| 5 | Monthly Sales Trend | Line Chart | Month, Total Amount | Tracks monthly revenue patterns and seasonality trends. |

**Global Filters / Slicers:**  
- Category  
- Date  
- City  
- Month  
- Status  
- Size  
- Order Status Group

---

## 3. Product Page

**Screenshot:**  
<img width="1402" height="794" alt="Screenshot 2025-11-08 012814" src="https://github.com/user-attachments/assets/44a30531-ce9d-43ff-b416-504c5b91c1a2" />


**Purpose:**  
The Product page provides insights into **product-level performance**. It helps stakeholders identify top-selling categories, SKUs, and sizes to optimize inventory, marketing, and sales strategies.

**KPIs on Product Page:**  
- **Best-Selling Category:** Identifies the product category with the highest total sales.  
- **Top Performing Size:** Highlights which product size sells the most.  
- **Top SKU by Sales:** Shows the SKU generating maximum revenue.  
- **Average Category Revenue (₹):** Finds the average sales per category for comparison.  

**Visuals / Charts on Product Page:**  
| Sr. No. | Name | Visual Type | Columns Used | Purpose / Insight |
|---------|------|-------------|--------------|-----------------|
| 1 | Top 3 SKU by Total Sales | Donut Chart | SKU, Total Amount | Identifies the best revenue-generating SKUs. |
| 2 | Top 3 SKU by Total Qty | Donut Chart | SKU, Qty | Shows which products are selling the most units. |
| 3 | Total Sales By Size | Stacked Bar Chart | Size, Total Amount | Reveals which size variants contribute more sales. |
| 4 | Qty By Month & Category | Line Chart | Qty, Month, Category | Tracks monthly demand trends across categories. |
| 5 | Total Sales By Category | Stacked Column Chart | Category, Total Amount | Measures category-wise revenue contribution. |

---

## 4. Fulfilment Page

**Screenshot:**  
<img width="1404" height="797" alt="Screenshot 2025-11-08 012844" src="https://github.com/user-attachments/assets/98651e2a-f7b3-4c12-8860-ed1aa459340d" />


**Purpose:**  
The Fulfilment page provides insights into **order processing and delivery efficiency**. It helps stakeholders evaluate FBA (Amazon-fulfilled) vs FBM (Merchant-fulfilled) performance and monitor delivery success rates.

**KPIs on Fulfilment Page:**  
- **Total Orders (Fulfilment):** Total number of orders processed.  
- **Avg Delivery Value (₹):** Compares average order value for each fulfilment type.  
- **Delivered Orders %:** Percentage of total delivered orders, indicating delivery efficiency.  
- **FBA % Share:** Contribution of Amazon-fulfilled orders in total sales.  
- **FBM % Share:** Contribution of Merchant-fulfilled orders in total sales.  
- **FBA Sales (₹):** Total revenue generated from FBA orders.  
- **FBM Sales (₹):** Total revenue generated from FBM orders.  

**Visuals / Charts on Fulfilment Page:**  
| Sr. No. | Name | Visual Type | Columns Used | Purpose / Insight |
|---------|------|-------------|--------------|-----------------|
| 1 | Qty by Fulfilment | Donut Chart | Qty, Fulfilment | Shows quantity distribution between FBA and FBM. |
| 2 | Avg Delivery Value By Fulfilment | Stacked Bar Chart | Avg Delivery Value, Fulfilment | Compares average delivery value by fulfilment type. |
| 3 | Delivered Orders % by Month & Year | Line Chart | Delivered Order %, Month, Year | Tracks delivery success trends over time. |
| 4 | Qty by City & Fulfilment | Stacked Bar Chart | City, Qty, Fulfilment | Highlights quantity handled by each fulfilment type across cities. |
| 5 | FBA Share % | Donut Chart | Order Type, Total Amount | Shows percentage of total sales fulfilled via Amazon FBA. |
| 6 | FBM Share % | Donut Chart | Order Type, Total Amount | Shows percentage of total sales fulfilled via Merchant FBM. |

---

## 5. Region Page

**Screenshot:**  
<img width="1405" height="799" alt="Screenshot 2025-11-08 012946" src="https://github.com/user-attachments/assets/3ccd2b44-ff08-4934-94e4-53d1b9b0588b" />


**Purpose:**  
The Region page provides insights into **state-wise and city-wise sales performance**. It helps stakeholders identify high-performing and underperforming regions to make informed regional strategies.

**KPIs on Region Page:**  
- **Top State by Sales:** Identifies the state generating the highest total sales.  
- **Top City by Sales:** Finds the city with the maximum revenue contribution.  

**Visuals / Charts on Region Page:**  
| Sr. No. | Name | Visual Type | Columns Used | Purpose / Insight |
|---------|------|-------------|--------------|-----------------|
| 1 | Sold Qty By State | Map | Qty, State | Visualizes total quantity sold across states. |
| 2 | Top 5 State by Total Sales | Stacked Bar Chart | State, Total Sales | Highlights the top 5 states generating the highest total sales. |
| 3 | Top 5 City by Total Sales | Stacked Bar Chart | City, Total Sales | Shows top 5 cities contributing most to overall sales. |
| 4 | Bottom 5 State by Total Sales | Stacked Bar Chart | State, Total Sales | Displays the 5 lowest-performing states. |
| 5 | Regional Overview Table | Table | State, City, Qty, Total Amount, Fulfilment | Provides detailed regional summary including sales, quantity, and fulfilment split. |


---

## 6. Promotion Page

**Screenshot:**  
<img width="1407" height="799" alt="Screenshot 2025-11-08 013015" src="https://github.com/user-attachments/assets/7951c19a-5b84-4b8d-bf8b-55c955d3ad0c" />

**Purpose:**  
The Promotion page provides insights into **promotional offer performance**. It helps stakeholders analyze how different promotions impact sales and understand revenue generated organically versus via offers.

**KPIs on Promotion Page:**  
- **No Promotion % Share:** Percentage of total sales without any promotion.  
- **Promotion Applied % Share:** Percentage of total sales under promotional offers.  

**Visuals / Charts on Promotion Page:**  
| Sr. No. | Name | Visual Type | Columns Used | Purpose / Insight |
|---------|------|-------------|--------------|-----------------|
| 1 | Promotion Type % by Qty | Donut Chart | Promotion Type, Qty | Shows quantity distribution between “Promotion Applied” and “No Promotion”. |
| 2 | Sales by Month & Promotion Type | Line & Clustered Column Chart | Month, Promotion Type, Total Amount | Compares monthly sales between promotion types. |
| 3 | Sales by Size & Qty | Line Chart | Total Amount, Size, Qty | Displays sales and quantity variation across product sizes during promotions. |
| 4 | Top 5 Promotion IDs by Qty | Stacked Bar Chart | Promotion IDs, Qty | Highlights the top 5 promotion IDs that drove the highest quantity of orders. |
| 5 | Total Sales By Promotion Type | Donut Chart | Total Amount, Promotion Type | Compares total sales generated under each promotion type. |

**Filters / Slicers on Promotion Page:**  
| Sr. No. | Filter / Slicer Name | Used Column |
|---------|-------------------|-------------|
| 1 | Business 2 Business | B2B |
| 2 | Fulfilment | Fulfilment |


---

## 7. Forecasting Page

**Screenshot:**  
![Uploading Screenshot 2025-11-08 013041.png…]()


**Purpose:**  
The Forecasting page provides insights into **monthly sales trends, seasonality, and future sales predictions**.  
It helps stakeholders plan inventory, marketing, and business strategies based on historical data and predicted trends.

**KPIs on Forecasting Page:**  
- **Avg Monthly Sales (₹):** Shows average sales per month to understand seasonality.  
- **Highest Sales Month:** Identifies the month with the highest total sales.  

**Visuals / Charts on Forecasting Page:**  
| Sr. No. | Name | Visual Type | Columns Used | Purpose / Insight |
|---------|------|-------------|--------------|-----------------|
| 1 | Order Over Status | Line Chart | Order Status Group, Qty | Tracks order movement by status group over time. |
| 2 | Qty Trend Over Time | Line Chart | Month, Qty | Shows how total ordered quantity changes month by month. |
| 3 | Sales Trend Over Time | Line Chart | Month, Total Amount | Displays overall monthly sales growth trends. |
| 4 | Category Wise Monthly Trend | Area Chart | Month, Total Amount, Category | Highlights monthly performance of different product categories. |
| 5 | Fulfilment Type Trend | Stacked Column Chart | Month, Fulfilment, Total Amount | Compares monthly sales between FBA and FBM fulfilment. |
| 6 | Business To Business Trend | Stacked Column Chart | B2B, Total Amount | Shows revenue contribution from B2B vs B2C orders. |
| 7 | Sales by Shipping Type & Month | Donut Chart | Month, Shipping Type, Total Amount | Displays distribution of sales by shipping types per month. |
