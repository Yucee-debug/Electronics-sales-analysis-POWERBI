## Electronics Sales Analysis & Power BI Dashboard

An end-to-end electronics sales analysis project developed in Microsoft Power BI to evaluate revenue, profitability, customer activity, and product performance through interactive business intelligence reporting.


### Project Objective

The objective of this project was to transform raw electronics sales data into an interactive Power BI dashboard that enables users to monitor key performance indicators, evaluate profitability, identify product and customer patterns, and support data-driven business decisions.


### Business Questions

The analysis was designed to answer the following questions:

1. Which brand generated the highest profit?
2. Which product color recorded the highest purchase volume?
3. What was the total revenue for the available year?
4. Which month recorded the lowest customer reach?
5. Which customer income level generated the highest profit?

   

## Table of Contents

- [Introduction](#1-introduction)
- [About the Dataset](#2-about-the-dataset)
- [Data Cleaning and Transformation](#3-data-cleaning-and-transformation)
- [Analysis](#4-analysis)
- [Key Findings](#5-key-findings)
- [Analysis Questions and Insights](#6-analysis-questions-and-insights)
- [Dashboard Preview](#7-dashboard-preview)
- [Tools and Techniques](#8-tools-and-techniques)
- [DAX Measures](#9-dax-measures)
- [Data Model](#10-data-model)
- [Conclusion](#11-conclusion)



## 1. Introduction
   
This project analyzes electronics sales data to evaluate overall sales performance, profitability, customer activity, and product performance. The analysis was developed in Microsoft Power BI to transform the raw sales data into an interactive dashboard that supports monitoring, measurement, and evaluation of key business performance indicators.


## Project Workflow

The project followed an end-to-end data analysis workflow:

1. **Data Profiling**: Reviewed the structure, fields, data types, completeness, and relationships within the dataset.
2. **Data Cleaning and Transformation** Prepared the source data using Power Query by checking data quality, correcting data types, standardizing fields, and preparing the tables for analysis.
3. **Data Modelling**: Established relationships between the Sales, Products, and Customers tables.
4. **DAX Calculations**: Created measures for revenue, cost, profit, profit margin, units sold, and unique customers.
5. **Exploratory Analysis**: Examined sales, profitability, customer activity, product characteristics, and income-level performance.
6. **Dashboard Development**: Built interactive Power BI visualizations and KPI cards.
7. **Insight Generation**: Interpreted the results to identify key performance patterns and findings.
8. **Documentation**: Documented the analytical process and results in GitHub


## Dashboard Overview

The Power BI dashboard provides a consolidated view of electronics business performance using key performance indicators (KPIs) and interactive visualizations. It enables users to monitor total revenue, total cost, total profit, and total customers while examining profitability by brand, purchase volume by color, revenue by year, monthly customer reach, and profit by income level.

The dashboard also includes interactive **Brand** and **Product Name** slicers, allowing users to filter the dashboard and examine sales and profitability performance for specific brands and products.



 ## 2. About the Dataset

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



## 4. Analysis

The analysis focused on measuring overall sales performance, profitability, customer activity, and product performance using calculated measures and interactive Power BI visualizations.

### Overall Business Performance

The overall business performance was evaluated using four key performance indicators: Total Revenue, Total Cost, Total Profit, and Total Customers.
Revenue was calculated by multiplying the SalesAmount by Quantity for each transaction and aggregating the results.

Total Cost was calculated by multiplying Unit Cost by Quantity.

Total Profit was calculated as Total Revenue minus Total Cost.

Total Customers was measured using the unique CustomerID values.

### Profitability by Brand

Profit was analyzed across product brands to identify differences in profitability and determine which brands contributed the most to overall profit.

### Product Demand by Color

Units sold were analyzed by product color to identify differences in purchase volume and determine which colors were associated with higher product demand.

### Revenue by Year

Revenue was analyzed by year to examine overall sales performance across the available sales period and identify changes in revenue over time.

### Monthly Customer Reach

Customer activity was analyzed by month to identify periods with higher or lower customer reach and examine the distribution of customer activity throughout the available sales period.

### Profitability by Customer Income Level

Profit was analyzed across customer income levels to determine how profitability was distributed among different customer segments.

### Interactive Analysis

Brand and Product name slicers were incorporated into the dashboard to allow users to dynamically filter the analysis. This makes it possible to examine revenue, cost, profit, customer activity, and product performance for selected regions and product categories.




## 5. Key Findings

The analysis produced four primary KPIs for measuring overall business performance: Total Revenue, Total Cost, Total Profit, and Total Customers. A total of 15,657 units were sold across 5,200 sales transactions.

### Total Revenue

Total Revenue was 3,106,350. This represents the total sales value generated from all recorded transactions after accounting for the quantity sold in each transaction.

### Total Cost

Total Cost was 2,174,445. This represents the total cost associated with the 15,657 units sold during the analysis period.

### Total Profit

Total Profit was 931,905. Profit was calculated by subtracting Total Cost from Total Revenue.

Profit = Total Revenue − Total Cost

Profit = 3,106,350 − 2,174,445 = 931,905

### Profit Margin

The overall profit margin was approximately 30%. This means that approximately 30% of the total revenue remained as profit after accounting for the recorded product costs.

Profit Margin = (Total Profit ÷ Total Revenue) × 100

Profit Margin = (931,905 ÷ 3,106,350) × 100 = 30%

### Total Customers

The analysis identified 250 unique customers in the Customers table. This KPI represents the number of distinct customers available in the dataset.

### Units Sold

A total of 15,657 units were sold across 5,200 recorded sales transactions. This KPI provides an overall measure of sales volume.

### KPI Summary

| KPI | Result | What It Measures |
|---|---:|---|
| **Total Revenue** | **3,106,350** | Total sales revenue generated |
| **Total Cost** | **2,174,445** | Total cost associated with units sold |
| **Total Profit** | **931,905** | Revenue remaining after recorded costs |
| **Profit Margin** | **30%** | Profit as a percentage of revenue |
| **Total Customers** | **250** | Number of unique customers |
| **Units Sold** | **15,657** | Total number of product units sold |


### Dashboard Findings

The dashboard provides a consolidated view of the business's sales and profitability performance. The KPI results show total revenue of 3,106,350 against total cost of 2,174,445, resulting in total profit of 931,905 and an overall profit margin of 30%.

The dashboard also shows that 15,657 units were sold across 5,200 sales transactions, while the customer dataset contains 250 unique customers.




## 6. Analysis Questions and Insights

### Question 1: Which brand generated the highest profit?

**Finding:** Apple generated the highest profit at 196,890, while Dell generated the lowest profit at 125,850.

**Insight:** Apple was the most profitable brand in the dataset, generating 71,040 more profit than Dell. This indicates that Apple products made the largest contribution to overall brand-level profitability.

### Question 2: Which product color had the highest purchase volume?

**Finding:** White had the highest purchase volume with 6,120 units sold, followed by Gray with 5,230 units and Black with 4,307 units.

**Insight:** White products recorded the highest sales volume, accounting for approximately 39.1% of the 15,657 units sold. Black recorded the lowest volume at approximately 27.5%.

### Question 3: What was the total revenue by year?

**Finding:** The dataset contains sales records for 2023, generating total revenue of 3,106,350.

**Insight:** Since the available sales data covers only 2023, the dataset does not provide multiple years for a year-over-year growth comparison. The 2023 revenue therefore represents the total revenue for the available period rather than evidence of annual growth or decline.

### Question 4: Which month had the lowest customer reach?

**Finding:** January, February, and March each recorded 250 unique customers.

**Insight:** There was no lowest-performing month based on customer reach because all three months recorded the same number of unique customers. Customer reach remained consistent across the available three-month period.

### Question 5: Which customer income level generated the highest profit?

**Finding:** The Medium income-level segment generated the highest profit at 346,920, followed by the High income-level segment at 302,205 and the Low income-level segment at 282,780.

**Insight:** The Medium income-level segment contributed the largest share of profit among the three income groups, generating approximately 37.2% of the total profit.

### Analysis Summary

| Analysis Question | Result | Key Insight |
|---|---|---|
| Which brand generated the highest profit? | Apple — 196,890 | Apple was the most profitable brand. |
| Which color had the highest purchase volume? | White — 6,120 units | White products had the highest sales volume. |
| What was the yearly revenue? | 2023 — 3,106,350 | 2023 represents the available sales period; no year-over-year comparison is possible. |
| Which month had the lowest customer reach? | No lowest month | January, February, and March each recorded 250 customers. |
| Which income level generated the highest profit? | Medium — 346,920 | Medium-income customers contributed the highest profit. |



## 7. Dashboard Preview

The Power BI dashboard provides an interactive overview of electronics sales performance, profitability, customer activity, and product performance.

### Electronics Overview

![Electronics Overview Dashboard](ELECTRONICS%20OVERVIEW.png)

### Electronics Sales Analysis Dashboard

![Electronics Sales Analysis Dashboard](ELECTRONICS%20SALES%20ANALYSIS%20DASHBOARD.png)



## 8. Tools and Techniques

### Microsoft Excel

Microsoft Excel was used as the source environment for the electronics sales dataset. The workbook contained the Products, Customers, and Sales tables used for the Power BI analysis.

### Power Query

Power Query in Power BI was used to prepare the dataset before analysis. The cleaning process included checking for missing values and duplicates, standardizing categorical values, trimming unnecessary spaces, converting date fields to the appropriate Date data type, and validating key fields used to connect the tables.

### Power BI Data Modelling

Power BI was used to create the analytical data model by connecting the Sales table to the Products and Customers tables through ProductID and CustomerID. This model allowed sales transactions to be analyzed using product and customer attributes.

### DAX

DAX (Data Analysis Expressions) was used to create measures for the dashboard KPIs and analysis. The calculations included Total Revenue, Total Cost, Total Profit, Total Customers, Units Sold, and Profit Margin.

### Power BI Visualizations

Power BI visualizations were used to present the analysis in an interactive dashboard. KPI cards were used to display overall performance measures, while charts were used to compare profitability by brand, units sold by color, revenue by year, monthly customer activity, and profit by income level.

### GitHub

GitHub was used to document and present the completed analytics project. The repository contains the project overview, dataset description, data preparation process, analytical approach, key findings, insights, and Power BI dashboard preview.



## 9. DAX Measures

### Total Revenue

Total Revenue =SUMX(Sales,Sales[SalesAmount] * Sales[Quantity])

### What this means

Think of one sales row:

**SalesAmount = 500**

**Quantity = 3**

Power BI calculates:

**500 × 3 = 1,500**

Result:

**3,106,350**

### Total Cost

Total Cost =SUMX(Sale,Sales[Unit Cost] * Sales[Quantity])

Result:

**2,174,445**

### Total Profit

Total Profit =[Total Revenue] - [Total Cost]
Calculation:

**3,106,350 − 2,174,445 = 931,905**
Result:

**931,905**

### Units Sold

Units Sold =SUM(Sales[Quantity])

Result:

**15,657 units**

### Total Customers

Total Customers =DISTINCTCOUNT(Customers[CustomerID])

### Why `DISTINCTCOUNT`?

Suppose Customer 101 purchased five times.

A normal count could count the five records.

But we want:

**Customer 101 = 1 customer**

Therefore:

`DISTINCTCOUNT(CustomerID)`

is appropriate.

### Profit Margin

Profit Margin =DIVIDE([Total Profit],[Total Revenue],0)

Calculation:

**931,905 ÷ 3,106,350 = 0.30**

Formatted as percentage:

**30%**

| Measure | Purpose |
|---|---|
| Total Revenue | Calculates total sales revenue based on sales amount and quantity. |
| Total Cost | Calculates total cost based on unit cost and quantity. |
| Total Profit | Calculates revenue remaining after total cost. |
| Units Sold | Calculates total product quantity sold. |
| Total Customers | Counts unique customers. |
| Profit Margin | Calculates profit as a percentage of revenue. |



## 10. Data Model

The Power BI data model was designed around the Sales table as the central transaction table. The Products and Customers tables provide descriptive information used to analyze sales transactions from different business perspectives.

### Model Structure

The model consists of:

- **Sales** — central transaction/fact table
- **Products** — product dimension table
- **Customers** — customer dimension table

### Sales Table

The Sales table acts as the central fact table because it contains the individual sales transactions and measurable business values such as Quantity, SalesAmount, and Unit Cost.
The table contains the transaction identifiers SaleID, ProductID, and CustomerID, which allow each transaction to be associated with a product and customer.

### Products Table

The Products table acts as a dimension table containing descriptive information about the products. ProductID serves as the key used to connect product information to sales transactions.
The table provides attributes such as ProductName, Category, Brand, Color, and Weight, which allow sales and profitability to be analyzed by product characteristics.

### Customers Table

The Customers table acts as a dimension table containing customer-related information. CustomerID serves as the key used to connect customers to their sales transactions.
The table provides attributes such as Region, Age, Gender, IncomeLevel, and SignupDate, allowing customer-related sales and profitability analysis.

### Relationships

The Sales table is connected to the Products table through ProductID and to the Customers table through CustomerID.

The relationships follow a one-to-many structure:

- Customers[CustomerID] → Sales[CustomerID]
- Products[ProductID] → Sales[ProductID]

This structure allows filters and attributes from the Customers and Products tables to be applied to the related sales transactions.

### Model Overview

Customers
CustomerID
     │
     │ 1 : *
     ▼
   Sales
CustomerID
ProductID
     ▲
     │ 1 : *
     │
Products
ProductID

### Why the Model Was Used

The model separates transaction data from descriptive customer and product information. This makes it possible to analyze sales transactions using attributes from the Products and Customers tables while maintaining a structured analytical model.
For example, the model allows total profit to be analyzed by Brand from the Products table and by IncomeLevel from the Customers table.



## 11. Conclusion

The electronics sales analysis provided an overview of sales performance, profitability, customer activity, and product performance for the available data period. The business generated total revenue of 3,106,350 from 15,657 units sold, with total costs of 2,174,445 resulting in total profit of 931,905 and an overall profit margin of 30%.
At the brand level, Apple recorded the highest profit at 196,890, while White products recorded the highest purchase volume with 6,120 units sold. The Medium income-level customer segment generated the highest profit at 346,9
Customer reach remained consistent across January, February, and March, with each month recording 250 unique customers. Since the available sales data covers 2023 only, a year-over-year revenue growth comparison could not be established.
The Power BI dashboard consolidates these findings into an interactive reporting tool, allowing users to monitor key performance indicators and explore results using Region and Category filters.

