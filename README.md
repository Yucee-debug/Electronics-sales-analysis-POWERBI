# Electronics Sales Analysis & Power BI Dashboard

An end-to-end electronics sales analysis project developed in Microsoft Power BI to evaluate revenue, costs, profitability, sales volume, customer activity, and product performance.

## Project Objective

The objective of this project was to transform the provided electronics sales dataset into an interactive Power BI dashboard that measures overall business performance and answers specific sales and profitability questions.

The analysis focuses on calculating core KPIs, comparing brand profitability, identifying the product color with the highest purchase volume, examining revenue for the available sales year, comparing monthly customer activity, and evaluating profit across customer income levels.

## Business Questions

The analysis was designed to answer the following questions:

1. Which brand generated the highest profit?
2. Which product color recorded the highest purchase volume?
3. What was the total revenue for the available sales year?
4. Which month recorded the lowest customer reach?
5. Which customer income level generated the highest profit?

## Table of Contents

- [Introduction](#1-introduction)
- [About the Dataset](#2-about-the-dataset)
- [Data Cleaning and Transformation](#3-data-cleaning-and-transformation)
- [Data Model](#4-data-model)
- [Analysis](#5-analysis)
- [Key Findings](#6-key-findings)
- [Analysis Questions and Insights](#7-analysis-questions-and-insights)
- [Dashboard Preview](#8-dashboard-preview)
- [DAX Measures](#9-dax-measures)
- [Tools and Techniques](#10-tools-and-techniques)
- [Conclusion](#11-conclusion)



## 1. Introduction

### Electronics Business Overview

This project analyzes sales performance for an electronics business using transaction-level sales data together with product and customer information.

The analysis was developed to monitor the business from three main perspectives: **financial performance, product performance, and customer performance**. This provides a structured way to evaluate how much revenue the business generated, how much it spent on the products sold, how much profit was retained, which products and brands contributed to performance, and how customer activity varied across the available sales period.

The analysis covers sales transactions recorded from **January to March 2023**, with the available Sales data ending on **March 10, 2023**.

### Business Overview Dashboard

The first Power BI dashboard page, **Business Overview**, provides a management-level view of the business performance.

The dashboard tracks five headline measures:

- **Total Revenue** — £3.11M
- **Total Profit** — £931.91K
- **Total Cost** — £2.17M
- **Total Sales** — 5,200 sales transactions
- **Total Customers** — 250 unique customers

The page also provides a monthly financial breakdown of **Total Profit, Total Revenue, and Total Cost** by region, allowing performance to be reviewed across March, January, and February.

The product performance visual ranks the products by profit, with **Headphones recording the highest displayed profit at approximately £168K**, followed by Monitor at approximately £166K.

Interactive **Product Name, Category, and Brand** slicers allow users to narrow the dashboard to specific product, category, or brand selections.

### Business Analysis Dashboard

The second Power BI dashboard page, **Business Analysis**, focuses on identifying patterns and differences within the sales, customer, product, and profitability data.

The page examines:

- Purchase volume by product color
- Monthly customer activity
- Revenue for the available sales year
- Profitability by brand
- Profitability by customer income level

The dashboard also includes the same **Product Name, Category, and Brand** filtering controls, allowing users to investigate these measures at a more focused product or brand level.

Together, the two dashboard pages provide an overview-to-detail reporting structure: the **Business Overview** page focuses on monitoring overall financial and product performance, while the **Business Analysis** page supports comparison and interpretation of the underlying performance patterns.

The purpose of the dashboard is therefore not only to display sales figures, but to provide a structured view of business performance that supports monitoring, comparison, evaluation, and data-driven decision-making.




## 2. About the Dataset

The analysis is based on an Excel workbook containing product, customer, and sales information. Three tables were used for the Power BI analysis: **Products, Customers, and Sales**. A fourth sheet, **Sheet1**, contains the original task instruction and was not used as an analytical table.

### Dataset Structure

| Table | Records | Purpose |
|---|---:|---|
| **Products** | 250 | Provides product attributes used to analyze product, category, brand, and color performance. |
| **Customers** | 250 | Provides customer attributes used to analyze customer activity, region, gender, age, and income level. |
| **Sales** | 5,200 | Contains the transaction records used to calculate revenue, cost, profit, sales volume, and customer activity. |

### Products Table

The Products table contains **250 product records** and six fields:

| Field | Description |
|---|---|
| `ProductID` | Unique identifier for each product. |
| `ProductName` | Name of the product. |
| `Category` | Product category. |
| `Brand` | Product brand. |
| `Color` | Product color. |
| `Weight` | Product weight. |

The table contains **7 product names, 2 categories, 6 brands, and 3 colors**.

### Customers Table

The Customers table contains **250 customer records** and seven fields:

| Field | Description |
|---|---|
| `CustomerID` | Unique identifier for each customer. |
| `CustomerName` | Customer name. |
| `Region` | Customer's geographical region. |
| `Age` | Customer age. |
| `Gender` | Customer gender. |
| `IncomeLevel` | Customer income-level segment. |
| `SignupDate` | Customer registration date. |

The customer records cover four regions after standardizing the region values: **North, East, South, and West**.

The income-level groups are **Low, Medium, and High**.

### Sales Table

The Sales table contains **5,200 transaction records** and seven fields:

| Field | Description |
|---|---|
| `SaleID` | Unique identifier for each sales transaction. |
| `ProductID` | Identifies the product involved in the transaction. |
| `CustomerID` | Identifies the customer associated with the transaction. |
| `Quantity` | Number of units recorded in the transaction. |
| `SaleDate` | Date of the sales transaction. |
| `SalesAmount` | Sales amount recorded for the transaction. |
| `Unit Cost` | Cost per unit associated with the transaction. |

The Sales table contains transactions recorded on **January 1, February 15, and March 10, 2023**, representing the three monthly periods available in the supplied dataset.

Across the 5,200 transactions, the recorded quantity totals **15,657 units**.

### Data Relationships

The three analytical tables are connected through their identifier fields:

```text
Products[ProductID]  1 ───────── *  Sales[ProductID]

Customers[CustomerID]  1 ─────── *  Sales[CustomerID]
```



## 3. Data Cleaning and Transformation

The raw workbook was reviewed table by table in Power Query before the analysis was performed. The cleaning process focused on data quality issues that could affect filtering, grouping, calculations, and relationships between the tables.

### Products Table

The Products table contained 250 records with no missing values or duplicate records.

The following checks were performed:

- `ProductID` was checked for uniqueness and completeness.
- `ProductName`, `Category`, `Brand`, and `Color` were reviewed for inconsistent text values.
- `Weight` was checked to confirm that the numeric values were valid.
- No missing values or duplicate records required removal from the Products table.

The Products table was therefore retained as the product dimension used to analyze sales by product, category, brand, and color.

### Customers Table

The Customers table contained 250 records with no missing values or duplicate records.

Two text-standardization issues were identified:

**1. Region**

Some Region values contained leading and trailing spaces, creating a separate ` north ` value from `North`.

The Region column was cleaned by applying **Trim** in Power Query so that the values could be grouped correctly.

**2. Gender**

The Gender column contained both `Female` and `female`, which represented the same category.

The values were standardized to a consistent format so that female customers were treated as one category.

After cleaning, Region contained four consistent values:

- North
- East
- South
- West

Gender contained two consistent values:

- Male
- Female

### Sales Table

The Sales table contained 5,200 transaction records with no missing values or duplicate records.

The following checks were performed:

- `SaleID` was checked for uniqueness.
- `ProductID` and `CustomerID` were checked against the Products and Customers tables.
- `Quantity`, `SalesAmount`, and `Unit Cost` were checked as numeric fields.
- Quantity values were positive.
- SalesAmount and Unit Cost contained no missing or negative values.
- `SaleDate` contained the same dates represented in two different text formats.

The `SaleDate` column contained:

- `2023-01-01`
- `2023/02/15`
- `2023-03-10`

The date column was converted to a proper **Date** data type so that the transactions could be grouped correctly by month and year in Power BI.

### Transformation Summary

The main Power Query transformations were:

| Table | Transformation | Reason |
|---|---|---|
| Products | Checked missing values and duplicates | Confirm product records were complete and unique. |
| Customers | Trimmed Region values | Removed leading/trailing spaces that created inconsistent region categories. |
| Customers | Standardized Gender values | Combined `Female` and `female` into one category. |
| Sales | Converted SaleDate to Date | Enabled accurate month and year analysis. |
| Sales | Checked numeric columns | Confirmed Quantity, SalesAmount, and Unit Cost were suitable for calculations. |
| All analytical tables | Checked key fields | Ensured ProductID, CustomerID, and SaleID could support the data model. |

No rows were removed from the three analytical tables because the identified issues could be corrected through transformation without discarding valid transaction, product, or customer records.



## 4. Analysis

The analysis was performed in Power BI using the cleaned Products, Customers, and Sales tables. The analysis focused on the financial performance of the business, product performance, customer activity, and profitability across customer and product segments.

### 4.1 Financial Performance

The core financial measures were calculated from the Sales table.

| KPI | Result |
|---|---:|
| Total Revenue | £3,106,350 |
| Total Cost | £2,174,445 |
| Total Profit | £931,905 |
| Total Sales Transactions | 5,200 |
| Total Customers | 250 |
| Total Units Sold | 15,657 |

Total profit was calculated as the difference between Total Revenue and Total Cost.

The resulting profit margin was approximately **30%**, indicating that approximately £0.30 of every £1 of recorded revenue remained as profit after the recorded product costs.

### 4.2 Profit by Brand

Profit was grouped by Brand to identify which electronics brand contributed the most profit.

| Brand | Profit |
|---|---:|
| Apple | £196,890 |
| Lenovo | £160,140 |
| Samsung | £159,510 |
| HP | £147,990 |
| Asus | £141,525 |
| Dell | £125,850 |

Apple recorded the highest profit among the six brands, while Dell recorded the lowest.

### 4.3 Purchase Volume by Color

Quantity was grouped by Color to determine which product color recorded the highest purchase volume.

| Color | Units Sold |
|---|---:|
| White | 6,120 |
| Gray | 5,230 |
| Black | 4,307 |

White recorded the highest purchase volume with **6,120 units**, followed by Gray and Black.

### 4.4 Revenue by Year

Revenue was grouped by year using the SaleDate field.

The available Sales records contain **2023 transactions only**, producing total revenue of:

**£3,106,350**

Because only one year is represented in the dataset, the analysis does not support a year-over-year revenue comparison.

### 4.5 Monthly Customer Activity

Customer activity was analyzed by month using the unique CustomerID count.

| Month | Unique Customers |
|---|---:|
| January | 250 |
| February | 250 |
| March | 250 |

Each available month recorded **250 unique customers**.

Therefore, there was no single lowest-performing month based on unique customer reach. January, February, and March were tied at 250 customers.

### 4.6 Profit by Income Level

Profit was grouped by customer IncomeLevel to determine which income segment contributed the most profit.

| Income Level | Profit |
|---|---:|
| Medium | £346,920 |
| High | £302,205 |
| Low | £282,780 |

The Medium income-level segment generated the highest profit at **£346,920**, followed by High and Low.

### 4.7 Product Profitability

Product-level profit was also examined to identify the products contributing the most profit.

| Product | Profit |
|---|---:|
| Headphones | £167,565 |
| Monitor | £166,365 |
| Tablet | £154,605 |
| Keyboard | £118,620 |
| Mouse | £114,375 |
| Laptop | £107,340 |
| Phone | £103,035 |

Headphones generated the highest product-level profit at **£167,565**, closely followed by Monitor at **£166,365**.

## 5. Key Findings

The analysis produced five headline KPIs for monitoring the overall performance represented in the dataset, supported by product, brand, customer, and profitability analysis.

### KPI Summary

| KPI | Result | What It Shows |
|---|---:|---|
| **Total Revenue** | £3,106,350 | Total revenue generated from the recorded sales transactions. |
| **Total Profit** | £931,905 | Profit remaining after deducting the recorded product costs from revenue. |
| **Total Cost** | £2,174,445 | Total product cost associated with the recorded quantities sold. |
| **Total Sales** | 5,200 | Total number of sales transactions recorded in the Sales table. |
| **Total Customers** | 250 | Number of unique customers represented in the customer data. |

### Financial Performance

The business generated **£3.11M in revenue** from the available sales records, with **£2.17M in recorded costs**, resulting in **£931.91K in profit**.

The relationship between revenue, cost, and profit gives an overall profit margin of approximately **30%**. This provides a baseline measure of the profitability of the sales recorded in the dataset.

### Sales and Customer Activity

The dataset contains **5,200 sales transactions** representing **15,657 units sold** and **250 unique customers**.

The distinction between Total Sales and Total Customers is important: Total Sales represents the number of transaction records, while Total Customers represents unique customers rather than the number of transactions made by those customers.

Customer activity was consistent across the three available monthly periods, with **250 unique customers recorded in January, February, and March**.

### Product Performance

The product profitability analysis shows that **Headphones generated the highest product-level profit at £167,565**, followed closely by **Monitor at £166,365**.

At the other end of the ranking, **Phone generated £103,035**, making it the lowest-profit product among the seven products displayed.

### Brand Profitability

**Apple generated the highest brand-level profit at £196,890**, followed by Lenovo at £160,140 and Samsung at £159,510.

**Dell recorded the lowest brand-level profit at £125,850** among the six brands analyzed.

This identifies Apple as the strongest brand contributor to profit within the available sales records.

### Product Color Performance

**White recorded the highest purchase volume with 6,120 units**, followed by Gray with 5,230 units and Black with 4,307 units.

White therefore accounted for approximately **39.1% of the 15,657 units sold**.

This finding describes sales volume rather than profitability; the highest-volume color is not automatically the most profitable color.

### Customer Income-Level Profitability

The **Medium income-level segment generated the highest profit at £346,920**, followed by High at £302,205 and Low at £282,780.

Medium-income customers contributed approximately **37.2% of the total £931,905 profit** represented in the analysis.

### Overall Finding

The analysis shows that the business generated a positive profit position within the available sales records, with Apple leading brand profitability, Headphones leading product profitability, White leading purchase volume, and the Medium income-level segment contributing the highest profit among the customer income groups analyzed.



## 6. Analysis Questions and Insights

The analysis was designed to answer five business questions using the cleaned sales, product, and customer data.

### 1. Which brand generated the highest profit?

**Result:** Apple generated the highest profit at **£196,890**.

**Insight:** Apple was the strongest profit-contributing brand among the six brands analyzed. Its profit was higher than Lenovo (£160,140), Samsung (£159,510), HP (£147,990), Asus (£141,525), and Dell (£125,850).

From a monitoring perspective, Apple should remain a key brand to track because changes in its sales volume, revenue, or cost could have a noticeable effect on overall profitability.

---

### 2. Which product color recorded the highest purchase volume?

**Result:** White recorded the highest purchase volume at **6,120 units**.

White represented approximately **39.1%** of the total **15,657 units sold**, compared with 5,230 units for Gray and 4,307 units for Black.

**Insight:** White products accounted for the largest share of recorded unit volume. This identifies White as the strongest color category by sales volume in the available data.

However, high volume should not be interpreted as high profitability without examining the associated revenue and cost.

---

### 3. What was the total revenue for the available sales year?

**Result:** The Sales data generated **£3,106,350 in revenue during 2023**.

**Insight:** The dataset represents only part of 2023, with transaction dates available for January, February, and March. Therefore, £3,106,350 should be treated as the revenue recorded in the supplied dataset rather than a full-year 2023 revenue figure.

The available data also does not support a year-over-year revenue comparison because no second year is present.

---

### 4. Which month recorded the lowest customer reach?

**Result:** There was **no single lowest month**.

| Month | Unique Customers |
|---|---:|
| January | 250 |
| February | 250 |
| March | 250 |

**Insight:** Customer reach was identical across the three available monthly periods. Each month recorded 250 unique customers, so the data does not identify a month with lower customer reach.

This should be reported as a three-way tie rather than selecting one month as the lowest-performing month.

---

### 5. Which customer income level generated the highest profit?

**Result:** The **Medium income-level segment generated the highest profit at £346,920**.

| Income Level | Profit |
|---|---:|
| Medium | £346,920 |
| High | £302,205 |
| Low | £282,780 |

Medium-income customers contributed approximately **37.2% of the total £931,905 profit**.

**Insight:** The Medium income-level segment was the largest contributor to profit among the three income groups. This makes the segment important for continued performance monitoring.

The analysis identifies the difference in profit contribution but does not establish the underlying cause, such as differences in purchasing frequency, product selection, quantity purchased, or transaction value.





## 7. Dashboard Preview

The Power BI report was structured into two dashboard pages to separate **performance monitoring** from **performance analysis**. The first page establishes the overall financial position of the electronics business, while the second page investigates the product, brand, color, customer, and income-level patterns behind that performance.

### Business Overview

![Business Overview Dashboard](business%20overview.png)

The **Business Overview** page was designed as the primary monitoring page for the electronics business.

The five KPI cards provide an immediate measurement of the overall position of the business:

- **Total Revenue — £3.11M**
- **Total Profit — £931.91K**
- **Total Cost — £2.17M**
- **Total Sales — 5,200**
- **Total Customers — 250**

These measures establish the financial and transaction baseline before moving into the underlying performance breakdowns.

The **Revenue, Cost and Profit by Region and Month** visual allows financial performance to be compared across the available monthly periods and four regions. This makes it possible to identify differences in regional contribution while also observing how revenue, cost, and profit changed across the available periods.

The **Profit by Product** visual ranks the seven products according to their contribution to profit. This supports product-level performance monitoring and makes it easier to identify the products contributing most and least to the overall profit result.

The page also includes **Product Name, Category, and Brand** slicers. These controls allow the user to move from the overall business position to a more focused view of selected products, categories, or brands.

### Business Analysis

![Business Analysis Dashboard](business%20analysis.png)

The **Business Analysis** page was designed to investigate the composition of the business results rather than only report the overall totals.

The **Purchase Volume by Color** visual compares the number of units sold across the three product colors, providing a view of product demand by color.

The **Customer Activity by Month** visual compares the number of unique customers recorded across the available monthly periods. This was used to determine whether any month recorded lower customer reach.

The **Revenue by Year** visual establishes the revenue recorded for the available sales year. Since the Sales data contains 2023 records only, the visual provides a revenue baseline rather than a year-over-year growth comparison.

The **Profit by Brand** visual compares the profit contribution of the six brands in the dataset, allowing the strongest and weakest brand-level contributors to be identified.

The **Profit by Income Level** visual examines how profit is distributed across the Low, Medium, and High customer income-level groups. This provides a customer-segment view of profitability rather than assuming that total customer count alone represents business value.

The **Product Name, Category, and Brand** slicers are available on this page as well, allowing the user to narrow the analysis and examine how the selected product, category, or brand affects the displayed results.

### Dashboard Design Approach

The two-page structure was intentionally used to support a monitoring-to-analysis workflow:

**Business Overview → establish the overall performance position**

**Business Analysis → investigate the factors contributing to that position**

This structure allows a user to begin with the headline KPIs and then use the supporting visuals and slicers to investigate product, regional, brand, customer, and profitability patterns within the available data.





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



## ## 9. DAX Measures

The dashboard uses six DAX measures to calculate the financial, sales-volume, customer, and profitability metrics displayed in the KPI cards and analytical visuals.

### 9.1 Total Revenue

```DAX
Total Revenue =
SUMX(
    Sales,
    Sales[SalesAmount] * Sales[Quantity]
)
```

This measure calculates revenue at the transaction level by multiplying the recorded `SalesAmount` by the `Quantity` for each Sales record and then adding the resulting values.

**Dashboard result:** 3,106,350

---

### 9.2 Total Cost

```DAX
Total Cost =
SUMX(
    Sales,
    Sales[Unit Cost] * Sales[Quantity]
)
```

This measure calculates the total cost associated with the units recorded in the Sales table. For each transaction, `Unit Cost` is multiplied by `Quantity`, and the resulting costs are summed.

**Dashboard result:** 2,174,445

---

### 9.3 Total Profit

```DAX
Total Profit =
[Total Revenue] - [Total Cost]
```

This measure derives profit from the two previously created measures rather than recalculating the transaction-level values.

**Calculation:**

3,106,350 − 2,174,445 = **931,905**

**Dashboard result:** 931,905

---

### 9.4 Units Sold

```DAX
Units Sold =
SUM(Sales[Quantity])
```

This measure sums the `Quantity` field in the Sales table to determine the total number of product units represented by the recorded transactions.

**Dashboard result:** 15,657 units

---

### 9.5 Total Customers

```DAX
Total Customers =
DISTINCTCOUNT(Customers[CustomerID])
```

This measure counts each customer only once using the unique `CustomerID`.

`DISTINCTCOUNT` is important here because the same customer can be associated with multiple records in the Sales table. Counting Sales rows would measure transactions, not customers.

**Dashboard result:** 250 customers

---

### 9.6 Profit Margin

```DAX
Profit Margin =
DIVIDE(
    [Total Profit],
    [Total Revenue],
    0
)
```

This measure expresses profit as a proportion of revenue.

**Calculation:**

931,905 ÷ 3,106,350 = **0.30**

Formatted as a percentage:

**30%**

---

### Measure Summary

| Measure             | DAX Purpose                                                 | Dashboard Result |
| ------------------- | ----------------------------------------------------------- | ---------------: |
| **Total Revenue**   | Calculates transaction revenue from SalesAmount × Quantity. |        3,106,350 |
| **Total Cost**      | Calculates transaction cost from Unit Cost × Quantity.      |        2,174,445 |
| **Total Profit**    | Subtracts Total Cost from Total Revenue.                    |          931,905 |
| **Units Sold**      | Sums the Quantity field.                                    |           15,657 |
| **Total Customers** | Counts unique CustomerID values.                            |              250 |
| **Profit Margin**   | Divides Total Profit by Total Revenue.                      |              30% |

### How the Measures Work With the Dashboard

These measures are not fixed values. They are evaluated within the current filter context in Power BI.

For example, when a user selects a specific **Brand** or **Product Name** using the dashboard slicers, the relevant Sales records are filtered through the Products-to-Sales relationship. The measures then recalculate using the filtered records.

This allows the KPI cards and connected visuals to update when the user interacts with the dashboard.



## 10. Data Model

The Power BI model uses the Sales table as the central transaction table, with Products and Customers providing the descriptive attributes needed to analyze those transactions.

### Model Structure

| Table | Role | Key Field | Analytical Purpose |
|---|---|---|---|
| **Sales** | Fact table | SaleID | Stores transaction-level quantities, dates, sales amounts, and costs. |
| **Products** | Dimension table | ProductID | Provides product, category, brand, color, and weight attributes. |
| **Customers** | Dimension table | CustomerID | Provides customer, region, age, gender, income level, and signup-date attributes. |

### Relationships

The model contains two relationships:

```text
Products[ProductID]  1 ───────── *  Sales[ProductID]

Customers[CustomerID]  1 ─────── *  Sales[CustomerID]

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

