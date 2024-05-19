Credit Card Financial Analysis Dashboard :-

Project Objective :-
To develop a comprehensive credit  card weekly dashboard that  provides real-time insights into key  performance metrics and trends,  enabling stakeholders to monitor  and analyze credit card operations 
effectively.

Import data to SQL database :-
1. Prepare csv file 
2. Create tables in SQL
3. import csv file into SQL
4. Data from SQL to Power BI tool
5. Data processing & DAX
6. Dashboard & insights
7. Export & share project

Project Insights- Week 52 (24st Dec)

Week of the Week change: 

• Revenue decreased by -9.4%, 

• Total Transaction Amt Decreased by 13.41% & 15.38%.

• Customer count increased by -15.89% Overview YTD:

• Overall revenue is 9.82M

• Total interest is 7.8M

• Total transaction amount is 45M

• Male customers are contributing more in revenue 25M, female 20M

• Blue & Silver credit card are contributing to 94.10 % of overall transactions

• TX, NY & CA is contributing to 68%

• Overall Activation rate is 57.47%

• Overall Delinquent rate is 6.07%


DAX Queries:-

here I am assuming, Revenue = interest_earned + Annual_fees - cust_Aquisition_cost

AgeGroup = SWITCH(
 TRUE(),
 'public cust_detail'[customer_age] < 30, "20-30",
 'public cust_detail'[customer_age] >= 30 && 'public cust_detail'[customer_age] < 40, "30-40",
 'public cust_detail'[customer_age] >= 40 && 'public cust_detail'[customer_age] < 50, "40-50",
 'public cust_detail'[customer_age] >= 50 && 'public cust_detail'[customer_age] < 60, "50-60",
 'public cust_detail'[customer_age] >= 60, "60+",
 "unknown"
 )
 
IncomeGroup = SWITCH(
 TRUE(),
 'public cust_detail'[income] < 35000, "Low",
 'public cust_detail'[income] >= 35000 && 'public cust_detail'[income] <70000, "Med",
 'public cust_detail'[income] >= 70000, "High",
 "unknown"
)

week_num2 = WEEKNUM('public cc_detail'[week_start_date])

Current_week_Reveneue = CALCULATE(
 SUM('public cc_detail'[Revenue]),
 FILTER(
 ALL('public cc_detail'),
 'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2]))) 
Previous_week_Reveneue = CALCULATE(
 SUM('public cc_detail'[Revenue]),
 FILTER(
 ALL('public cc_detail'),
 'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2])-1))




