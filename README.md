# LITA-Capstone-project

### Project Title : Sales Performance Analysis For a Retail Store 

### Project Overview
---
This sales analysis provides valuable insights for a retail store over a specified timeframe. By examining various parameters within the data, I gained a comprehensive understanding that facilitated informed decision-making. This process allowed me to derive narratives from the insights obtained, enriching my understanding of sales performance.

### Data Sources 
---
The primary source of data here is LITA Capstone Dataset(sales data) which was provided by my facilitator 

### Tools Used 
---
-Microsoft Excel  
   1. Data cleaning
   2. Analysis
   3. Visualization
      
-SQL- Structured Query Language
   1. Querying of data
      
-Power BI
   1. Data analysis
   2. Visualization

### Data Cleaning and Preparation
---
Cleaning of the data was the first phase to enable me have a clean data to work on so as to get the accurate result.
  1. Data loading and review
  2. Removing of Duplicate data
  3. Data formatting
### Exploratory Data Analysis 
---
This invloves analyzing the data to enable better understanding of the data set, they include;
  1. Total sales by product
  2. Total sales by region
  3. Average sales per product
  4. Average sales per region
  5. Highest selling product
  6. Top 5 customer
  7. Percentage of total sales by each region
  8. Product with no sales 

### Data Analysis
---
This includes some of the codes or queries i used to analyze the data 
When analyzing on Microsoft Excel below forumar was used
   - for total sales =$F2*$G2
   - for average sales by product =AVERAGEIFS(H1:H9923,C1:C9923,C1)
   - for average sales by region= =AVERAGEIFS(H1:H9923,D1:D9923,C1)

When Analyzing for SQL below formular was used 

SELECT * FROM[dbo].[SALESDATA]

----total sales for each product category---

select product,
sum(quantity * unitprice) as total_sales
from [dbo].[SALESDATA]
group by Product

---number of sales transactions in each region---

select region,
sum (quantity * unitprice) as total_sales_transactions
from [dbo].[SALESDATA]
group by Region

----highest-selling product by total sales value.---

select top 1 product,
sum(quantity*unitprice) as total_sales
from[dbo].[SALESDATA]
group by product
order by total_sales
desc

---total revenue per product.---

select product,
sum (quantity*unitprice) as total_revenue
from[dbo].[SALESDATA]
Group by Product

---monthly sales totals for the current year---

SELECT MONTH(ORDERDATE) AS MONTH,
SUM(quantity*UnitPrice) AS TOTAL_SALES
FROM [dbo].[SALESDATA]
WHERE YEAR(ORDERDATE)=YEAR(GETDATE())
GROUP BY MONTH(ORDERDATE)
ORDER BY MONTH(ORDERDATE)

---top 5 customers by total purchase amount---

SELECT TOP 5 SUM (quantity*unitprice) AS TOTAL_SALES, CUSTOMER_ID
FROM[dbo].[SALESDATA]
GROUP BY Customer_Id
ORDER BY 1 DESC

---percentage of total sales contributed by each region---

SELECT region,SUM(quantity*unitprice) AS total_sales,
(SUM(quantity*unitprice) / (SELECT SUM(quantity*unitprice) FROM[dbo].[SALESDATA] ) * 100) AS percentage_of_total_sales
FROM [dbo].[SALESDATA]
GROUP BY region;

---products with no sales in the last quarter---

SELECT distinct PRODUCT, orderid, quantity
FROM [dbo].[SALESDATA]
WHERE PRODUCT is null
(SELECT DISTINCT PRODUCT
FROM [dbo].[SALESDATA]
WHERE ORDERDATE BETWEEN '2024-07-01' AND '2024-09-30')
