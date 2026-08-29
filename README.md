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


## 3. Data Cleaning and Transformation

Before analysis, the Products, Customers, and Sales tables were reviewed in Power Query to identify missing values, duplicate records, inconsistent formatting, incorrect data types, and potential relationship issues.

### Missing Values

The Products, Customers, and Sales tables were checked for missing values. No missing values were identified in the analytical fields, so no records required removal because of null values.

### Duplicate Records

Duplicate records were checked across the three analytical tables. No duplicate rows were identified in the Products, Customers, or Sales tables.

The key identifier columns were also checked. ProductID, CustomerID, and SaleID contained unique values within their respective tables.

### Standardizing Categorical Values

Categorical fields were standardized to ensure that values representing the same category were not treated as separate categories. Region values were trimmed and standardized for consistent capitalization, while Gender values were standardized so that different capitalization did not create duplicate categories.

### Relationship and Key Validation

The key fields used to connect the tables were validated. ProductID values in the Sales table matched the Products table, while CustomerID values in Sales matched the Customers table. No unmatched key values were identified.


### Data Transformation

The cleaned data was prepared for analysis by standardizing categorical values, removing unnecessary spaces, converting date fields to the Date data type, and ensuring numerical fields used appropriate data types.

The cleaned Products, Customers, and Sales tables were then loaded into Power BI for data modelling and analysis.
The dataset supports analysis of revenue, cost, profit, customer activity, product performance, brand profitability, purchase volume, and customer segmentation.
