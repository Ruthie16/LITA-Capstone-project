# LITA-Capstone-project

### Project Title : Sales Performance Analysis For a Retail Store 

[Project Overview](#project-overview)

[Data Sources](#data-sources)

[Tools Used](#tools-used)

[Data Cleaning and Preparation](#data-cleaning-and-preparation)

[Exploratory Data Analysis](#exploratory-data-analysis)

[Data Analysis](#data-analysis)

[Data Visualization](#data-visualization)




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

### Data Visualization 
![BI 1](https://github.com/user-attachments/assets/6687e27c-fd5f-4a38-8764-48d97886a721)
![SQLS 9](https://github.com/user-attachments/assets/69168c92-286b-4818-8153-d6d412cc15db)
![SQLS 8](https://github.com/user-attachments/assets/4eab4d7a-416f-4b82-9eb3-c9a03e1e03d1)
![SQLS 7](https://github.com/user-attachments/assets/787fb77f-457f-4f2c-bf00-8c5cff9036de)
![SQLS 6](https://github.com/user-attachments/assets/dcfaed37-2a6d-4a2b-9bcd-88d0265d34a2)
![SQLS 5](https://github.com/user-attachments/assets/4b48f5c7-018a-4351-b595-7b8d590b2555)
![SQLS 4](https://github.com/user-attachments/assets/743ba7d9-7e7d-49f5-84d9-1c16de991bea)
![SQLS 3](https://github.com/user-attachments/assets/a478179e-fac2-4a99-928f-5fc584ef320c)
![SQLS 2](https://github.com/user-attachments/assets/5e2fd484-0cc3-4083-836c-55ecc5d0f383)
![SQLS 1](https://github.com/user-attachments/assets/cb28322f-cd72-4bb5-9dc0-74149e22c65b)
![ex 5](https://github.com/user-attachments/assets/a2ae43f0-990a-4f52-9ce5-ccc8ebaaf51a)
![ex 4](https://github.com/user-attachments/assets/fb58b418-be5e-4bd2-8210-89c4535e4aeb)
![ex 2](https://github.com/user-attachments/assets/b7473f58-34de-49b8-9472-b63228cb8a4f)
![ex 1](https://github.com/user-attachments/assets/d61890f7-798b-4a79-95f5-f274fa95226e)
![BI 3](https://github.com/user-attachments/assets/d56fef27-1d30-4347-b6e0-85e4dae1dc5d)
![BI 2](https://github.com/user-attachments/assets/a8b38160-162e-46cf-bb39-f180e01e8041)
![bi 5](https://github.com/user-attachments/assets/51aea93c-c1c4-4f81-828a-70beb4be5420)


