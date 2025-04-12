# Coffee Sales Analysis

## Project Overview

This project aimed to evaluate and improve the sales performance of Coffee Shop by analyzing historical sales data. The primary objectives were to identify sales trends, assess the effectiveness of sales strategies, and discover key factors influencing sales outcomes.

##  Research Questions 

- Which types of coffee have the highest sales volume?

- Which types of coffee generate the highest profit margins?
  
- During which time periods does the company experience peak sales?

## Data Sources

Data from sales transactions were collected and cleaned for analysis. The original data "Coffee Sales Data.csv" file contains variables such as date (3/1/2024), datetime (3/1/2024 10:15:51 AM), cash type (card/cash), card (the number of the card used to purchase), money (how much the customer paid when ordering a type of coffee), coffee name (the specific coffee the customer purchased). 

## Tools

- Excel for data assessment [Download here](https:/microsoft.com)
- PowerBI for data cleaning and creating report [Download here](https:/PowerBI.com)
- SQL for descriptive analytics [Download here](https:/SQL.com)

## Data Preparation
The raw data has been imported from Microsoft Excel into Microsoft Power BI for analysis. Preliminary assessment in Excel indicates the presence of inconsistencies that need to be addressed to ensure the data is suitable for accurate and reliable analysis.

- ### Features Engineering

In PowerBI, we created a new feature called Time by splitting the original column datetime (3/1/2024 10:15:51 AM) into Column (Date) → 3/1/2024 and Column (Time) → 10:15:51 AM. The Column (Time) → 10:15:51 AM is also spitted into Column (Time) → 10:15:51 and Column (Time Period) → AM/PM. This will enable us to identify the time period that the company experience peak sales.

- ### Data Cleaning

In PowerBI, Data profiling technique has been implemented to analyze the data to better understand its structure, quality, and content. 9% of the variable "card" are empty. However, this variable will not contribute to our analysis, so we removed it from the data.

## Exploratory Data Analysis

We used SQL to perfrom some descriptive summaries. Here are some of the code written.

- ### View all records
```sql
SELECT * FROM[dbo].[Coffee Sales Data];
```

- ### See distinct coffee name
```sql
SELECT DISTINCT coffee_name FROM [dbo].[Coffee Sales Data] ;
```

- ### Check data range
```sql
SELECT MIN(date), MAX(date) FROM [dbo].[Coffee Sales Data];
```

- ### Total sales
```sql
SELECT SUM(money) AS total_sales FROM[dbo].[Coffee Sales Data] ;
```

- ### Sales by coffee name
```sql
SELECT coffee_name, SUM(money) 
FROM [dbo].[Coffee Sales Data]
GROUP BY coffee_name;
```

- ### Top 5 best-selling coffee
```sql
SELECT coffee_name, SUM(money) AS revenue 
FROM [dbo].[Coffee Sales Data]
GROUP BY coffee_name
ORDER BY revenue DESC
LIMIT 5;
```

## Results and Findings

## Recommendations

## Limitations
- The presence of missing values in the data, particularly in the 'card' column, highlights potential issues in the data collection process. These gaps may stem from human-related errors, such as incorrect or incomplete data entry, or from software limitations during data handling or transfer.

- Insufficient feature availability required the generation of additional features from existing variables to extract meaningful insights from the data.

