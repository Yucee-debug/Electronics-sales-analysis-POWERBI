Electronics Sales Analysis & Power BI Dashboard

1. Introduction
   
This project analyzes electronics sales data to evaluate overall sales performance, profitability, customer activity, and product performance. The analysis was developed in Microsoft Power BI to transform the raw sales data into an interactive dashboard that supports monitoring, measurement, and evaluation of key business performance indicators.

Dashboard Overview

The Power BI dashboard provides a consolidated view of the electronics business performance using key performance indicators (KPIs) and interactive visualizations. It enables users to monitor total revenue, total cost, total profit, and total customers while examining profitability by brand, purchase volume by color, revenue by year, monthly customer reach, and profit by income level.

The dashboard also includes interactive Brand and Category slicers, allowing users to filter the analysis and examine performance for specific customer brand and product categories.

 2. About the Dataset

The dataset is an Excel workbook containing product, customer, and sales transaction information for an electronics business. The data was used to evaluate sales performance, profitability, customer activity, and product-related performance in Power BI.

### Dataset Structure

The workbook contains three sheets:

| Sheet | Records | Fields | Description |
|---|---:|---:|---|
| Products | 250 | 6 | Contains product details and product attributes. |
| Customers | 250 | 7 | Contains customer demographic and registration information. |
| Sales | 5,200 | 7 | Contains individual sales transaction records. |


### Products Table

The Products table contains 250 product records and includes ProductID, ProductName, Category, Brand, Color, and Weight.

### Customers Table

The Customers table contains 250 customer records and includes CustomerID, CustomerName, Region, Age, Gender, IncomeLevel, and SignupDate.

### Sales Table

The Sales table contains 5,200 sales transactions and includes SaleID, ProductID, CustomerID, Quantity, SaleDate, SalesAmount, and Unit Cost.

### Table Relationships

The Sales table serves as the central transaction table. It connects to the Products table through ProductID and to the Customers table through CustomerID. These relationships allow product attributes and customer attributes to be analyzed alongside sales transactions.

The dataset supports analysis of revenue, cost, profit, customer activity, product performance, brand profitability, purchase volume, and customer segmentation.

The dataset supports analysis of revenue, cost, profit, customer activity, product performance, brand profitability, purchase volume, and customer segmentation.
