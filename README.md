# Sales-Data-Project
## Table of Content
- [Project Overview](#project-overview)
- [Business Purpose](#business-purpose)
- [Project Objectives](#project-objectives)
- [Tools and Technologies](#tools-and-technologies)
- [Data Quality Issues](#data-quality-issues)
- [Data Cleaning](#data-cleaning)
- [Data Model](#data-model)
- [SQL queries](#sql-queries)
- [DAX measures](#dax-measures)
- [Dashboard Features](#dashboard-features)
- [Business Questions](#business-questions)
- [Results](#results)
- [Recommendations](#recommendations)

### Project Overview
This data analysis aims to provide accurate and clean data, reveal trends, and converts the complex data into understandable charts and reports. This data was cleaned and transformed using Excel and Power Query and analyzed using SQL and DAX before being used to create interactive Power BI report.

### Business Purpose
The purpose of this project was to clean the data and create a report whihc helps business leaders answer the questions about sales performance, product demand and customer behaviour.  

### Project Objectives
The main objective of this project were to:
- Clean and transform raw sales data using Excel and Power Query.
- Analyze sales data using SQL and DAX measures.
- Built a interactive Power BI dashboard.
- Analyze monthly sales.
- Compare performance across region.
- Identify top customers and products.
- Provide useful insights for decision-making.

### Tools and Technologies
- Microsoft Excel
- SQLite
- Power Query
- Power BI
- DAX
- Data Modeling
- Data Visualization

### Data Quality Issues

This Sales dataset contained the following issues:

- Duplicate records
- Duplicate Oder IDs
- Mixed Date formats
- Inconsistent customers names and regions names
- Extra Spaces in text columns
- Missing sales representive, total sales and discount values
- Negative quantitities
- Incorrect data types

### Data Cleaning

  The following data cleaning steps were completed in Excel and Power Query.
  - Remove duplicate records
  - Trimmed unnecessary spaces from text column
  - Strandarized cusotmers name and regions name
  - Replaces missing Sales Representative values with unassigned
  - Replace missing sales and discount values with 0
  - Corrected mixed date formats
  - Reviewed and corrected the negative values in total sales column
  - Assigned a corrected data type in each column
  - Loaded the clean data into Power BI.
 
### Data Model 
The separate Date table was created and connected to the Sales table using Order Date as a common column. This step made it possible to perform the monthly, quarterly and yearly based sales analysis.

### SQL Queries
The following SQL queries has been used for data analysis:

##### Total Revenue
```sql
SELECT SUM(Total_Sales) AS TotalRevenue From Sales;
```

##### Sales by Region
```sql
SELECT Region,SUM(Total_Sales) AS Revenue FROM Sales
Group BY Region
Order BY Revenue DESC;
```

##### Top 5 Customers
```sql
SELECT Customer_Name, SUM(Total_Sales) AS Revenue FROM Sales
GROUP BY Customer_Name
ORDER BY Revenue DESC
LIMIT 10;
```

##### Best Selling Products
``` sql
SELECT Product_Name, SUM(Quantity) AS TotalQuantitySold FROM Sales
Group BY Product_Name
ORDER BY TotalQuantitySold Desc;
```
##### Monthly Sales Trend
```sql
SELECT MONTH(OrderDate) AS Month, SUM(Total_Sales) As Revenue FROM Sales
GROUP BY MONTH(OrderDate)
ORDER BY Month;
```

### DAX Measures 
The following DAX measures has been used for sales analysis in Power BI:

##### Total Revenue 
```dax
Total Revenue = SUM(Sales[Total Sales])
```
##### Total Orders
```dax
Total Orders = DISTINCTCOUNT(Sales[Order ID])
```
##### Total Customers
```dax
Total Customers = DISTINCTCOUNT(Sales[Customer ID])
```

##### Quantity Sold
```dax
Quantity Sold = SUM(Sales[Quantity])
```
##### Average Order Value 
```dax
Average Order Value = DIVIDE([Total Revenue],[Total Orders])
```
##### Average Discount
```dax
Average Discount = AVERAGE(Sales[Discount])
```
##### Last Purchase Date
```dax
Last Purchase Date = MAX(Sales[Order Date])
```
### Dashboard Features
The Sales Power BI dashboard includes:

- Total Revenue KPI card
- Total Orders KPI card
- Total Customers KPI card
- Average Order Value KPI card
- Quantity Sold KPI card
- Monthly sales trend
- Regional sales performance
- Revenue by product category
- Top performing products
- Top customers
- Interactive slicer
- Drill-through page

### Business Questions
- What is company total sales revenue?
- How many orders have been placed?
- How are sales changing over time?
- Which month generate more revenue?
- Which region performs best?
- What is the most selling product?
- What is the underperforming product?
- Who are the highest value customers?

### Results
- East region generated the highest total revenue.
- Monitor produced the highest level of sales.
- Sales reached their highest level durng first quarter of the year.
- Our top 3 customers who contributed a significant portion of total revenue are David Wilson, Liam Anderson and Emma Thomsom.

### Recommendations
- Increase the inventory for Monitors.
- Develop promotions for underperforming products like keyboard and printers.
- Reward the top customer with rewards.
- Focus marketing in East region which is the top performing region. 

