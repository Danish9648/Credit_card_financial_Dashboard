# Credit_card_financial_Dashboard
Credit Card Trancaction and Customer Details Power BI Dashboard

Project Objective: To develop a comprehensive credit card weekly dashboard that provides real-time insights into key performance metrics and trends, enabling stakeholders to monitor and analyze credit card operations effectively.

Dataset: Credit Card Financial Dataset

Steps: 

Step 1: Imported Data- Used two CSV files (credit card details and customer details) to import data into Power BI.

Step 2: Transformed data- Used required DAX queries. 

(i)
AgeGroup = SWITCH(
TRUE(),
'public cust_detail'[customer_age] < 30, "20-30",
'public cust_detail'[customer_age] >= 30 && 'public cust_detail'[customer_age] < 40, "30-40",
'public cust_detail'[customer_age] >= 40 && 'public cust_detail'[customer_age] < 50, "40-50",
'public cust_detail'[customer_age] >= 50 && 'public cust_detail'[customer_age] < 60, "50-60",
'public cust_detail'[customer_age] >= 60, "60+",
"unknown")

(ii)
IncomeGroup = SWITCH(
TRUE(),
'public cust_detail'[income] < 35000, "Low",
'public cust_detail'[income] >= 35000 && 'public cust_detail'[income] <70000, "Med",
'public cust_detail'[income] >= 70000, "High",
"unknown")

(iii)
week_num2 = WEEKNUM('public cc_detail'[week_start_date])

(iv)
Revenue = 'public cc_detail'[annual_fees] + 'public cc_detail'[total_trans_amt] + 'public cc_detail'[interest_earned]

(v)
Current_week_Reveneue = CALCULATE(
SUM('public cc_detail'[Revenue]),
FILTER(
ALL('public cc_detail'),
'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2])))

(vi)
Previous_week_Reveneue = CALCULATE(
SUM('public cc_detail'[Revenue]),
FILTER(
ALL('public cc_detail'),
'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2])-1))

Step 3: Implementation of Dashboard on differnt key metrics.

Step 4: Fetched the indights.

Step 5: Deployed the project on github.

Insights:

Overview YTD:
• Revenue increased by 28.8%

• Overall revenue is 57M

• Total interest is 8M

• Total transaction amount is 46M

• Male customers are contributing more in revenue 31M, female 26M

• Blue & Silver credit card are contributing to 93% of overall
transactions

• TX, NY & CA is contributing to 68%

• Overall Activation rate is 57.5%

• Overall Delinquent rate is 6.06%


