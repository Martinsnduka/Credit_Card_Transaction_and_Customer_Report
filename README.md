# Credit Card Weekly Dashboard (Power BI)

An interactive Power BI report that tracks credit card revenue, interest earned, transactions and customer behavior on a weekly basis, so stakeholders can monitor performance and spot trends quickly.

## Business Problem

Develop a comprehensive credit card weekly dashboard that provides real time insights into key performance metrics and trends, enabling stakeholders to monitor and analyze credit card operations effectively.

## Project Overview

The report is split into two pages:

1. **Credit Card Customer Report**: who the customers are and where revenue comes from (gender, age, income, job, education, marital status, state).
2. **Credit Card Transactions Report**: how the cards perform (card category, expenditure type, quarterly revenue and transaction count).

A third view, the **Week over Week (WoW) Revenue table**, tracks how revenue moves from one week to the next.

## Dashboard Preview

<img width="899" height="497" alt="image" src="https://github.com/user-attachments/assets/e34f2e18-3036-4883-98a5-ab59b8d36f5d" />

<img width="899" height="500" alt="image" src="https://github.com/user-attachments/assets/1afb7809-31c0-46d6-90eb-f40836332361" />

<img width="605" height="478" alt="image" src="https://github.com/user-attachments/assets/ae3b82dc-1a5c-45a7-bc88-fbff7cb822bf" />


## Key Metrics

* **Total Revenue:** 10.79M
* **Interest Earned:** 7.84M
* **Total Transaction Amount:** 44.52M
* **Transaction Count:** about 10K
* **Total Income:** 576M
* **Customer Satisfaction Score (CSS):** 3.19

## Key Insights

* **Blue cards drive the business.** Blue generates about 9.18M of the 10.79M revenue, which is roughly 85% of the total. Silver, Gold and Platinum together make up the remaining 15%.
* **Interest is the main income source.** Interest earned (7.84M) accounts for about 73% of total revenue.
* **Revenue is split evenly by gender.** Male customers contribute 5.46M and female customers 5.34M.
* **Bills lead spending.** Bills (2.8M) rank first by expenditure type, followed by Entertainment (1.9M) and Fuel (1.8M).
* ** High-income customers contribute the most revenue** among the income groups, and the 40 to 49 age group is the strongest age segment.
* **Top states by revenue:** TX, CA, NY, FL, and NJ.
* **Weekly revenue is stable.** It stays in a range of roughly 189K to 240K per week, with the highest week at about 240K.
* ** Week-over-week swings are moderate.** Most weekly changes sit between about minus 13% and plus 11%.

## Tools and Skills Used

* Power BI Desktop
* DAX (measures and time intelligence)
* Power Query (data cleaning and transformation)
* Data modeling and dashboard design

## Data Model

The dataset has two main parts:

* **Customer data:** gender, age group, income, job, education, marital status, state
* **Transaction data:** card category, expenditure type, transaction amount, interest earned, revenue, week start date

## Sample DAX Measures

```DAX
Total Revenue = SUM('credit_card'[Revenue])

Interest Earned = SUM('credit_card'[Interest_Earned])

Total Transaction Amount = SUM('credit_card'[Total_Trans_Amt])

Current_Week_Revenue =
CALCULATE(
    [Total Revenue],
    FILTER(
        ALL('credit_card'),
        'credit_card'[Week_Numb2] = MAX('credit_card'[Week_Numb2])
    )
)

Previous_Week_Revenue =
CALCULATE(
    [Total Revenue],
    FILTER(
        ALL('credit_card'),
        'credit_card'[Week_Numb2] = MAX('credit_card'[Week_Numb2]) - 1
    )
)

WoW Revenue % =
DIVIDE(
    [Current_Week_Revenue] - [Previous_Week_Revenue],
    [Previous_Week_Revenue]
)
```

## Dashboard Features

* Slicers for quarter, week start date, and gender
* KPI cards for revenue, interest, income and customer satisfaction
* Revenue breakdown by card category, expenditure type, state, age, income, job and education
* Quarterly revenue and transaction count combo chart
* Weekly revenue trend line by gender
* Week-over-week revenue table with percentage change

## How to Use

1. Clone or download this repository.
2. Open `Credit_card_Transaction.pbix` in Power BI Desktop.
3. Use the slicers to filter by quarter, week, or gender.
4. Click any visual to cross-filter the rest of the report.

## Repository Structure

```
├── Credit_card_Transaction.pbix
├── images/
│   ├── customer_report.png
│   ├── transactions_report.png
│   └── wow_revenue.png
└── README.md
```

## Recommendations

* Grow Silver, Gold, and Platinum card uptake, since Blue carries most of the revenue.
* Target high-income and 40 to 49 customers with offers, as they bring in the most revenue.
* Review the weeks with large negative WoW changes to find the cause, such as seasonality or campaigns.
* Look into the customer satisfaction score of 3.19 and set a plan to improve it.

## Author

**Martins Nduka**
Aspiring Data Analyst | Excel, SQL, Python, Power BI
* Email: [ndukamartins2019@gmail.com]
