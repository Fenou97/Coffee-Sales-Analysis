# Coffee Sales Analysis

## Table of contents

- [Project Overview](#project-overview)
- [Research Questions](#research-questions)
- [Data Sources](#data-sources)
- [Tools](#tools)
- [Data Preparation](#data-preparation)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Results and Findings](#results-and-findings)
- [Recommendations](#recommendations)
- [Limitations](#limitations)

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

![Data Assessement 2](https://github.com/user-attachments/assets/aaab5194-46ed-4880-8c52-0f83df4aa318)

- ### Features Engineering

In PowerBI, we created a new feature called Time by splitting the original column datetime (3/1/2024 10:15:51 AM) into Column (Date) → 3/1/2024 and Column (Time) → 10:15:51 AM. The Column (Time) → 10:15:51 AM is also spitted into Column (Time) → 10:15:51 and Column (Time Period) → AM/PM. This will enable us to identify the time period that the company experience peak sales.

![Features Engineering 2](https://github.com/user-attachments/assets/1d4d4055-fa5c-4393-a17e-c441dd8a2747)

- ### Data Cleaning

In PowerBI, Data profiling technique has been implemented to analyze the data to better understand its structure, quality, and content. 9% of the variable "card" are empty. However, this variable will not contribute to our analysis, so we removed it from the data.

![Data Profiling 2](https://github.com/user-attachments/assets/8400f9ed-a94e-49e1-b726-243a2c15bf5b)


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
- ### Coffee Popularity and Revenue

![Finding 1](https://github.com/user-attachments/assets/2b1b0e5a-7461-41f4-9253-7332e8df6930)

**Top sellers (by quantity)**: Americano with Milk, Latte, Cappuccino, Americano

**Least sold**: Espresso and Cocoa.

**Americano with Milk leads in units sold, suggesting it's a customer favorite in terms of frequency**.

**Top revenue generators**: Latte, Americano with Milk, Cappuccino

**Lowest revenue**: Espresso and Cocoa 

**Although Americano with Milk has the highest count, Latte generated the most revenue likely due to a higher unit price**.

- ### Coffee purchase

![Finding 2](https://github.com/user-attachments/assets/42acb3db-60c0-45a3-9877-72ee5f810fb7)

AM purchases dominate with a count close to 900.

PM purchases are significantly lower, estimated around 100.

**Coffee is overwhelmingly purchased in the morning (AM) compared to the afternoon or evening (PM). This supports a common behavior pattern where people tend to consume more coffee earlier in the day, likely to boost alertness and energy levels at the start of their day**.

Card payments are used predominantly, also near 900.

Cash payments are quite minimal, roughly around 100.

**Most customers prefer using cards (credit/debit) to pay for coffee, indicating a shift toward cashless transactions. This could reflect convenience, modern payment preferences, or a demographic comfortable with digital transactions**.

### - Sales and Revenues Trends

![Finding 3](https://github.com/user-attachments/assets/1e1439b2-ad09-4981-a51e-8a6c1af94e94)

The month of May had the highest sales volume, with over 260 units and also generated the most money, around $9,000.

Both the number of coffee sales and revenue sharply declined in July. Sales volume fell to under 100 and revenue dropped to about $2,500.

March, April, and June all had relatively stable figures. Sales volume ranged between 190–230 units and revenue was between $6,800–$7,800.

## Recommendations

- While Latte may be the most profitable per unit and should be promoted more, Americano with Milk has strong volume and we can consider bundling or loyalty promos. Upselling higher-margin drinks (e.g., Lattes, Cappuccinos) could boost revenue. However, Cocoa and Espresso may need marketing revamps or removal if not profitable.

- The majority of coffee purchases occur in the morning and are paid for using a card. This could inform business decisions such as staffing more in the morning hours to handle peak demand, offering loyalty programs or promotions targeting morning buyers, ensuring efficient card payment systems to accommodate customer preferences.

- Capitalize on peak months (e.g., May) by promoting best-selling products from May during other months, replicating successful campaigns, discounts, or events that were run in May, and analyzing customer behavior in May to understand what drove the spike.

- Investigate and address July drop by conducting a root cause analysis to see if there were any supply chain or staffing issues or a downtime.


## Limitations
- The presence of missing values in the data, particularly in the 'card' column, highlights potential issues in the data collection process. These gaps may stem from human-related errors, such as incorrect or incomplete data entry, or from software limitations during data handling or transfer.

- Insufficient feature availability required the generation of additional features from existing variables to extract meaningful insights from the data.

