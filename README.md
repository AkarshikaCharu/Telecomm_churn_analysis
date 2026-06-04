Telecomm_churn_analysis
Telecom Business Intelligence: High-Value Customer Churn Analysis
This repository contains a data analytics and business intelligence solution designed to analyze and predict churn behavior among High-Value Customers (HVC)for a telecom corporation. 
Using operational data across four consecutive months (June to September), this project isolates top-tier revenue generators, diagnoses why they leave, and highlights customers currently "At-Risk" of churning.

Executive Summary
A Python-driven analysis was executed on a dataset containing customer metrics for 30,011 High-Value Customers. The framework yields the following data-driven insights:
High-Value Churn Rate:8.64% of the company's top 30% revenue-generating users have completely churned by month 9 (September).
The "Usage Drop" Indicator: Churned customers show a distinct pattern where their Minutes of Usage (MOU) dropped off almost entirely in month 8, long before absolute churn occurred in month 9.
Proactive Retaining Alert: The pipeline identified **3,978 currently active customers** who are heavily "At-Risk" due to a usage crash of 50% or more.

Core Business Logic & Methodology
The project applies strict telecom business definitions to segment and evaluate data over a 4-month timeline:
1. High-Value Customer (HVC) Definition
Instead of analyzing the entire user base, the script filters for the top 30% of customers based on their average recharge amount in the first two action months (June (Month 6) and July (Month 7)):
Average Recharge=(Total Recharge Amt_6+Total Recharge_Amt_7)/2

2. Churn Derivation
A customer is flagged as Churned (1) if they show zero volume/usage in Month 9 (September) across all key services:
Total Usage_9 = Outgoing MOU_9 + Incoming MOU_9 + 2G MB_9 + 3G MB_9

3. Usage Drop Ratio (Predictive Indicator)
To evaluate the rate of service decline prior to churn, the script calculates a Minutes of Usage (MOU) drop ratio between Month 7 (July) and Month 8 (August):
MOU Drop Ratio = (Total OG MOU_8 -Total OG MOU_7)/Total OG MOU_7+1

At-Risk Definition:Any user who is not yet churned Churn = 0 but experiences age 50%  dropin outgoing usage (MOU Drop Ratio < -0.5) is flagged with an immediate strategic retention alert.

Requirements & Setup
Prerequisites
Make sure you have Python 3 installed along with the required data science stack:
Pandas(Data manipulation)
NumPy(Mathematical modeling)
Matplotlib(Data visualization)

### Installation

1. Clone this repository or download the source code files.
2. Install the library dependencies using pip:
bash
pip install pandas numpy matplotlib
3. Place your raw telecom data named as `telecom_churn_data.csv` into the root folder.

Key Outputs & Visualizations
The execution of the script generates two major diagnostic components:

1. Terminal Business Intelligence Report
--- Telecom Business Intelligence Report ---
High-Value Customers Analyzed: 30011
Churn Rate among High-Value: 8.64%
Avg MOU Drop for Churners: 0.95
Avg MOU Drop for Loyalists: 4.80
ALERT: 3978 customers are currently 'At-Risk' (50%+ usage drop).

2. Generated Plot Artifacts

churn_dist.png`: A distribution bar plot explicitly breaking down the counts of Loyal (0) vs. Churned (1) clients among the high-value segment to show class imbalance.
"arpu_trend_plot.png`: A line plot outlining the **Average Revenue Per User (ARPU)** trajectory from June (6) to August (8) to track changes in value generation.

Actionable Recommendations
Target the 3,978 "At-Risk" Customers:Deploy personalized re-engagement campaigns (e.g., tailored data packages or discount offers) immediately to this specific segment before 
they reach month 9 absolute churn status.
Establish Month 8 Gates:Implement automated alarms using the Usage Drop Ratio metric to catch customer deterioration 30 days before full service abandonment.
