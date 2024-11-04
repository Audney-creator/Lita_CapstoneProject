# Lita_CapstoneProject
This is where i documented my Second project given to me by The Incubator Hub 

## Project Title: Capstone Project 
## Sales Data

[Project Overview](#project-overview)

[Technologies Used](#technologies-used)

[Project Objectives](#project-objectives)

[Data](data)

[Analysis process](#analysis-process)

- [Excel](#excel)

- [SQL](#sql)

- [Power BI](#power-bi)

[Key Insights](#key-insights)

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
---
The dataset used in this project was structured and contained fields such as 
|Order ID|Customer ID|Product|Region|Order date|Quantity|Unit price|
|--------|-----------|-------|------|----------|--------|----------|


During the initial analysis, there appeared to be repeated records; i had my doubts about it seeing as the customer id were unique, but confirmed that there were truly duplicates on SQL, by calling out a some particular customer id and products, the query used in confirming this;

```sql
SELECT * FROM SALESDATA
WHERE CUSTOMER_ID = 'CUS1278'
AND PRODUCT = 'SHIRT'

```
## Analysis process 
---
**-1. Excel**
---
- Exploration: Conducted an exploratory analysis such as;
  - Finding revenue ,
  - Average sales per products,
  - Total revenue by region,
  - Grand total revenue, Total number of products,
  - Total revenue per products,
  - Total quantity per product sold,
  - Total quantity of product sold, to understand the data structure and identify any patterns or anomalies.
  
- Pivot Tables: Created pivot tables to summarize sales by product, region, and month.
  
- Metrics Calculation: Calculated average sales per product and total revenue by region to gauge sales performance.
  
- Reporting: Developed additional reports for deeper insights into specific sales metrics.

  ![Screenshot (31)](https://github.com/user-attachments/assets/d5c4f182-5816-4591-bb8f-e63fe6343f5a)

  ![Screenshot (32)](https://github.com/user-attachments/assets/5a6ec578-b994-434b-b27c-c22a649052a2)


![Screenshot (33)](https://github.com/user-attachments/assets/68d0e73b-6439-4e1b-b87b-71a677913638)











**-2. SQL**
---
- Data Loading: Imported the dataset into SQL Server for further analysis.
- Querying:
  -Queries: Retrieve total sales for each product category
```sql
CREATE database SALES_REPORT

SELECT *FROM[dbo].[salesdata]

------TOTALSALES FOR EACH PRODUCT CATEGORY------
SELECT Product,SUM(Revenue) AS TOTALSALES FROM SALESDATA
GROUP BY Product 

-----NUMBER OF SALES TRANSACTION IN EACH REGION---
SELECT REGION,COUNT(QUANTITY) AS NUMBER_OF_TRANSACTIONS FROM SALESDATA
GROUP BY REGION

-----HIGHEST SELLING PRODUCTS BY TOTALSALES VALUE
SELECT TOP 1 PRODUCT,SUM(REVENUE) AS TOTALSALES FROM SALESDATA
GROUP BY PRODUCT

-----TOTAL REVENUE PER PRODUCT
SELECT PRODUCT,SUM(REVENUE) AS TOTALREVENUE FROM SALESDATA
GROUP BY PRODUCT

-----MONTHLY SALESTOTAL FOR THE CURRENT YEAR
SELECT FORMAT(ORDERDATE, '2024-MM') AS MONTH,SUM(REVENUE) AS MONTHLYSALESTOTAL FROM SALESDATA
WHERE YEAR(ORDERDATE) = 2023
GROUP BY FORMAT(ORDERDATE, '2024-MM')
ORDER BY MONTH 

----TOP 5 CUSTOMERS BY TOTAL PURCHASE AMOUNT-----
SELECT TOP 5 CUSTOMER_ID,SUM(REVENUE) AS TOTALPURCHASEAMOUNT FROM SALESDATA
GROUP BY CUSTOMER_ID
ORDER BY TOTALPURCHASEAMOUNT DESC

-----PERCENTAGE OF THE TOTALSALES BY EACH REGION----
SELECT REGION,
SUM(REVENUE) AS REGIONALSALES,
(SUM(REVENUE) * 100.0) / (SELECT SUM(REVENUE) FROM SALESDATA) AS PERCENTAGEOFTOTALSALES FROM SALESDATA
GROUP BY REGION

----PRODUCTS WITH NO SALES IN THE LAST QUARTER---
SELECT PRODUCT FROM SALESDATA
WHERE PRODUCT NOT IN (
SELECT PRODUCT FROM SALESDATA 
WHERE ORDERDATE >=
DATEADD( QUARTER,-1, GETDATE())
)

```

**-3. Power BI**
---
- Dashboard Creation: Designed an interactive dashboard to display the key insights discovered through the Excel and SQL analysis.
- Features:
   - Sales overview by category, top products, and regional performance.
    - Monthly trend analysis to observe sales fluctuations over time.
    - Interactive filters to allow users to view data by specific regions or products.

     ![Screenshot (28)](https://github.com/user-attachments/assets/a7a5a167-521b-45ac-9a92-690b47d50c46)
 
 
  

## Key Insights
---
From the analysis, the following insights were identified:

Certain products consistently outperformed others across regions.
Regional sales showed variability, indicating areas for targeted marketing.
Monthly sales trends highlighted peak sales periods, which could guide inventory planning.






