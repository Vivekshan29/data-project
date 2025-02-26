Sales Analysis - Griffith Foods
 Project Overview
This project analyzes sales data for Griffith Foods to identify trends, top customers, product performance, and seasonal sales variations. The analysis was performed using Tableau, SQL, and Excel, and provides key insights into business performance and sales distribution.

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

Sales Details: Order Number, Sales, Order Date, Order Status
Product Information: Product Line, MSRP, Product Code
Customer Details: Customer Name, Contact Information, Country, Territory
Time Dimensions: Quarter ID, Month ID, Year ID
Data Overview, Cleaning & Transformation Process
In this dataset, we aim to ensure data quality and consistency before conducting analysis. The steps taken focus on identifying missing values, handling duplicates, and ensuring data integrity.

1. Data Overview
The dataset consists of sales transactions with key details such as order numbers, customer details, product categories, pricing, and sales performance. Below are the main columns and their significance:

Column Name	Description
ORDERNUMBER	Unique identifier for each order
SALES	Total sales amount per order
ORDERDATE	Date when the order was placed
STATUS	Order status (e.g., Shipped, Canceled)
QTR_ID	Quarter in which the order was placed
MONTH_ID	Month in which the order was placed
YEAR_ID	Year in which the order was placed
PRODUCTLINE	Category of the product (e.g., Trains, Ships, Planes)
MSRP	Manufacturer’s Suggested Retail Price
PRODUCTCODE	Unique product identifier
CUSTOMERNAME	Name of the customer who placed the order
PHONE	Contact number of the customer
ADDRESSLINE1/ADDRESSLINE2	Customer's address details
CITY, STATE, POSTALCODE, COUNTRY, TERRITORY	Geographic details of the customer
CONTACTLASTNAME, CONTACTFIRSTNAME	Name of the customer contact person
DEALSIZE	Size of the deal (Small, Medium, Large)
Total Sales	Summarized total sales for analysis
2. Data Cleaning & Transformation Process
A. Identifying Missing Values
sql
Copy
Edit
SELECT COUNT(*) AS Missing_Values
FROM cleaned_sales_data
WHERE QUANTITYORDERED IS NULL
   OR PRICEEACH IS NULL
   OR CUSTOMERNAME IS NULL;
✅ Purpose: This query helps identify missing values in crucial columns (QUANTITYORDERED, PRICEEACH, CUSTOMERNAME).
✅ Action Taken: If missing values exist:

For numerical columns like QUANTITYORDERED and PRICEEACH, missing values might be filled with the median or mean.
For categorical values like CUSTOMERNAME, missing entries may be replaced using alternative customer details or marked as "Unknown."
B. Detecting Duplicate Entries
sql
Copy
Edit
SELECT ORDERNUMBER, COUNT(*)
FROM cleaned_sales_data
GROUP BY ORDERNUMBER
HAVING COUNT(*) > 1;
✅ Purpose: This query checks for duplicate orders by counting occurrences of ORDERNUMBER.
✅ Action Taken: If duplicates exist, they need to be investigated—duplicates may arise from data entry errors or system issues.

C. Viewing Duplicate Entries
sql
Copy
Edit
SELECT * 
FROM cleaned_sales_data
WHERE ORDERNUMBER IN (
    SELECT ORDERNUMBER 
    FROM cleaned_sales_data
    GROUP BY ORDERNUMBER
    HAVING COUNT(*) > 1)
ORDER BY ORDERNUMBER;
✅ Purpose: This query retrieves all duplicate rows for further inspection.
✅ Action Taken: It allows us to check whether duplicate records are legitimate (e.g., different quantities for the same order) or if they need removal.

D. Removing Duplicates
sql
Copy
Edit
DELETE FROM cleaned_sales_data
WHERE ROWID NOT IN (
    SELECT MIN(ROWID) 
    FROM cleaned_sales_data
    GROUP BY ORDERNUMBER, QUANTITYORDERED, PRICEEACH
);
✅ Purpose: This deletes duplicate rows while keeping the first occurrence based on ORDERNUMBER, QUANTITYORDERED, and PRICEEACH.
✅ Action Taken: Ensures no duplicate sales transactions, which prevents inflated sales calculations.

E. Final Verification
sql
Copy
Edit
SELECT * FROM cleaned_sales_data;
✅ Purpose: After cleaning, this retrieves the final dataset to confirm that the necessary changes have been made.

3. Data Transformation for Analysis
After cleaning the data, transformations are performed to enhance its usability:

Sales Aggregation by Month & Product Line

Monthly sales trends help identify peak periods.
Top-performing product categories highlight key revenue sources.
Customer Segmentation

Identifying top 10 customers helps in customer retention strategies.
Enhancing Data Consistency

Standardizing date formats.
Removing unwanted characters/spaces from text fields.
4. Data Export
After cleaning, the dataset is exported to Excel and SQL databases for reporting and visualization.

Excel: Used for interactive dashboards.
SQL: Used for advanced queries and business intelligence tools (Tableau, Power BI).

📈 Key Visualizations and Insights
1️⃣ Top 10 Customers (By Total Sales)
📌 Finding:

The highest revenue was generated from customers purchasing Classic Cars ($2.96M), Vintage Cars ($1.64M), and Motorcycles ($971K).
The top 3 customers alone accounted for ~50% of total revenue, indicating a reliance on a few key buyers.
📌 Recommendation:

Loyalty programs or exclusive discounts can be introduced to retain high-value customers.
Consider cross-selling and up-selling related product lines to increase revenue from these customers.
2️⃣ Sales by Product Line
📌 Finding:

Classic Cars generated the highest revenue ($2.96M), followed by Vintage Cars ($1.64M).
Trains had the lowest sales ($203K), indicating either low demand or poor marketing.
📌 Recommendation:

Increase marketing efforts for low-performing categories (e.g., Trains).
Optimize stock levels for high-demand products like Classic and Vintage Cars.
Bundle popular products with low-performing categories to boost sales.
3️⃣ Sales by Month (Seasonality Analysis)
📌 Finding:

November had the highest sales ($2.1M), followed by October ($1.12M), suggesting peak holiday demand.
Summer months (June & July) had the lowest sales (~$450K–$500K), indicating a seasonal dip.
📌 Recommendation:

Run promotions & discounts in summer months to boost sales.
Increase marketing spend from September to November to capitalize on peak demand.
Improve inventory management to ensure enough stock during the high-sales months.
📌 Tools Used
Data Analysis: SQL, Excel
Data Visualization: Tableau, Power BI
Dashboard Design: Tableau
📂 Repository Structure
bash
Copy
Edit
/Sales-Analysis-Griffith-Foods/
│── dataset/                      # Raw and cleaned data
│── notebooks/                     # SQL queries & scripts
│── dashboards/                     # Tableau visualization files
│── README.md                       # Project documentation
│── sales_analysis.pdf               # Summary of findings
🔗 Live Dashboard
🔗 Tableau Public Link

📢 Conclusion
This analysis provided valuable insights into customer purchasing patterns, product performance, and seasonal trends. By leveraging these insights, Griffith Foods can optimize marketing, inventory, and pricing strategies to maximize profitability.

