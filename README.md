Sales Analysis - Griffith Foods

Project Overview

This project analyzes sales data for Griffith Foods to identify trends, top customers, product performance, and seasonal sales variations. The analysis was performed using Tableau, SQL, and Excel, providing key insights into business performance and sales distribution.

🎯 Problem Statement

Griffith Foods aims to improve sales performance by identifying:

Top customers contributing to revenue.

Sales trends by product line to optimize inventory and marketing strategies.

Monthly sales variations to plan better seasonal strategies and stock management.

🔍 Objectives

Identify the Top 10 Customers by total sales.

Analyze Sales by Product Line to find the most profitable product categories.

Track Sales by Month to uncover seasonal demand patterns.

📊 Data Overview

The dataset consists of order-level transaction details, including:

Sales Details: ORDERNUMBER, SALES, ORDERDATE, ORDERSTATUS

Product Information: PRODUCTLINE, MSRP, PRODUCTCODE

Customer Details: CUSTOMERNAME, CONTACT INFORMATION, COUNTRY, TERRITORY

Time Dimensions: QTR_ID, MONTH_ID, YEAR_ID

🔹 Data Cleaning & Transformation Process

To ensure data quality and consistency before analysis, we performed:

Identifying missing values

Handling duplicates

Standardizing data formats

1️⃣ Data Overview

Column Name

Description

ORDERNUMBER

Unique identifier for each order

SALES

Total sales amount per order

ORDERDATE

Date when the order was placed

STATUS

Order status (e.g., Shipped, Canceled)

QTR_ID

Quarter in which the order was placed

MONTH_ID

Month in which the order was placed

YEAR_ID

Year in which the order was placed

PRODUCTLINE

Category of the product (e.g., Trains, Ships, Planes)

MSRP

Manufacturer’s Suggested Retail Price

PRODUCTCODE

Unique product identifier

CUSTOMERNAME

Name of the customer who placed the order

DEALSIZE

Size of the deal (Small, Medium, Large)

TOTAL SALES

Summarized total sales for analysis

2️⃣ Data Cleaning & Transformation Process

A. Identifying Missing Values

-- SQL QUERY HERE

✅ Purpose: Identifies missing values in crucial columns.
✅ Action Taken:

For numerical columns, missing values were replaced with the median/mean.

For categorical values, missing entries were marked as Unknown.

B. Detecting Duplicate Entries

-- SQL QUERY HERE

✅ Purpose: Checks for duplicate orders.
✅ Action Taken: If duplicates exist, they were investigated for potential removal.

C. Removing Duplicates

-- SQL QUERY HERE

✅ Purpose: Deletes duplicate rows while keeping the first occurrence.

D. Final Verification

-- SQL QUERY HERE

✅ Purpose: Retrieves the final cleaned dataset for analysis.

3️⃣ Data Transformation for Analysis

After cleaning the data, transformations were performed to enhance usability:

Sales Aggregation by Month & Product Line to identify peak periods.

Customer Segmentation to retain high-value customers.

Enhancing Data Consistency by standardizing date formats.

4️⃣ Data Export

After cleaning, the dataset was exported to Excel and SQL databases for reporting and visualization.

Excel: Used for interactive dashboards.

SQL: Used for business intelligence tools (Tableau, Power BI).

📈 Key Visualizations and Insights

1️⃣ Top 10 Customers (By Total Sales)

📌 Finding:

The highest revenue was generated from customers purchasing Classic Cars ($2.96M), Vintage Cars ($1.64M), and Motorcycles ($971K).

The top 3 customers accounted for ~50% of total revenue.

📌 Recommendation:

Introduce loyalty programs to retain high-value customers.

Consider cross-selling and up-selling related product lines.

2️⃣ Sales by Product Line

📌 Finding:

Classic Cars generated the highest revenue ($2.96M), followed by Vintage Cars ($1.64M).

Trains had the lowest sales ($203K), indicating either low demand or poor marketing.

📌 Recommendation:

Increase marketing efforts for low-performing categories.

Optimize stock levels for high-demand products.

Bundle popular products with low-performing ones to boost sales.

3️⃣ Sales by Month (Seasonality Analysis)

📌 Finding:

November had the highest sales ($2.1M), followed by October ($1.12M).

Summer months (June & July) had the lowest sales (~$450K–$500K).

📌 Recommendation:

Run promotions & discounts in summer months to boost sales.

Increase marketing spend from September to November.

Improve inventory management to ensure enough stock during peak sales months.

📌 Tools Used

Data Analysis: SQL, Excel

Data Visualization: Tableau, Power BI

Dashboard Design: Tableau

📂 Repository Structure

/Sales-Analysis-Griffith-Foods/
│── dataset/       # Raw and cleaned data
│── notebooks/     # SQL queries & scripts
│── dashboards/    # Tableau visualization files
│── README.md      # Project documentation
│── sales_analysis.pdf  # Summary of findings

🔗 Live Dashboard: Tableau Public Link

📢 Conclusion

This analysis provided valuable insights into customer purchasing patterns, product performance, and seasonal trends. By leveraging these insights, Griffith Foods can optimize marketing, inventory, and pricing strategies to maximize profitability.

