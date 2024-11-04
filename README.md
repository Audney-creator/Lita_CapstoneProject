# Lita_CapstoneProject
This is where i documented my Second project given to me by The Incubator Hub 

## Project Title: Capstone Project 
## Sales Data
## Project Overview
---
In this project, i was tasked with analyzing the sales performance of a retail store. 
To explore sales data to uncover key insights such as top-selling products, regional 
performance, and monthly sales trends. The goal was to produce an interactive Power BI 
dashboard that highlights these findings.

## Technologies Used
---
- Microsoft Excel;
  - data loading and inspection
  - handling duplicates
  - For initial data exploration and calculations
  - data cleaning and formatting
  - data visualizations

- SQL: For querying data to derive key insights

- Power BI: For creating an interactive dashboard to visualize the findings

## Project Objectives
---
- 1. Excel:

     - Conducted exploratory analysis on the sales dataset.

     - Summarized total sales by product, region, and month using pivot tables.

     - Calculated metrics such as average sales per product and total revenue by region.

     - Generated reports using charts, to highlight trends and insight.

- 2. SQL:

    * Loaded the dataset into a SQL Server environment to extract the following insights:

    - Retrieved total sales for each product category.

    - Determined the number of sales transactions by region.

    - Identified the highest-selling product by total sales value.

    - Calculated total revenue per product.

    - Generated monthly sales totals for the current year.

    - Found the top 5 customers by total purchase amount.

    - Calculated the percentage of total sales contributed by each region.

    - Identified products with no sales in the last quarter.

- 3. Power BI:

    - Created an interactive dashboard that visualizes insights from Excel and SQL analysis.

    - Included an overall sales overview, top-performing products, and regional breakdowns.
 
 ## Data

The dataset used in this project was structured and contained fields such as 
- Order ID,
- Customer ID,
- Product,
- Region,
- Order date,
- Quantity,
- and Unit price.
During the initial analysis, there appeared to be repeated records; i had my doubts about it seeing as the customer id were unique, but confirmed that there were truly duplicates on SQL, by calling out a some particular customer id and products, the query used in confirming this;

---sql
SELECT * FROM SALESDATA
WHERE CUSTOMER_ID = 'CUS1278'
AND PRODUCT = 'SHIRT'

## Analysis Process
1. Excel
Exploration: Conducted an exploratory analysis to understand the data structure and identify any patterns or anomalies.
Pivot Tables: Created pivot tables to summarize sales by product, region, and month.
Metrics Calculation: Calculated average sales per product and total revenue by region to gauge sales performance.
Reporting: Developed additional reports for deeper insights into specific sales metrics.
2. SQL
Data Loading: Imported the dataset into SQL Server for further analysis.
Querying:
Sample Query: Retrieve total sales for each product category
sql
Copy code
SELECT product_category, SUM(sales_amount) AS total_sales
FROM sales_data
GROUP BY product_category;
Ran SQL queries to answer the questions outlined in the objectives, including calculating monthly sales totals, identifying top products, and determining the regional distribution of sales.
3. Power BI
Dashboard Creation: Designed an interactive dashboard to display the key insights discovered through the Excel and SQL analysis.
Features:
Sales overview by category, top products, and regional performance.
Monthly trend analysis to observe sales fluctuations over time.
Interactive filters to allow users to view data by specific regions or products.
Key Insights
From the analysis, the following insights were identified:

Certain products consistently outperformed others across regions.
Regional sales showed variability, indicating areas for targeted marketing.
Monthly sales trends highlighted peak sales periods, which could guide inventory planning.






