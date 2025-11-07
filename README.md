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
