# pandas-profiling

Bank Credit Card Customer Churn Prediction and Analysis

**Introduction**

Customer churn is a major concern for big businesses. Losing a customer is awfully expensive for any business. The full cost of churn includes both lost revenue and marketing costs involved in replacing them with new ones. Identifying unhappy customers early on will help business win those customers with incentives, free trials promotions, and advertising.
This project uses Machine Learning to identify those who will churn so action can be taken well in advance to retain those customers. Also, it investigates the factors that affect customer churning 

**Data Wrangling**

The data consists of bank customers who own credit card. It has about 10,000 customers and 23 features describing each user. It includes Client number, Attrition Flag, Customer Age, Gender, Dependent count, Education Level, Marital Status, Income Category, Card Category, Months on book, Total Relationship Count, Months Inactive 12 mon, Contacts Count 12 mon, Credit Limit, Total Revolving Bal, Avg Open to Buy, Total Amt Chng Q4 Q1, Total Trans Amt, Total Trans Ct, Total Ct Chng Q4 Q1     and Avg Utilization Ratio.

This data is obtained from Kaggle at the link https://www.kaggle.com/sakshigoyal7/credit-card-customers
Here is the description of few metrics in the data which are not trivial.
<br />Revolving Balance: Portion of credit card spending that goes unpaid at the end of a billing cycle
<br />Average Open to Buy: The difference between the credit limit assigned to cardholder account and the present balance on the account
<br />Utilization Ratio: How much customer owes divided by credit limit expressed in percentage
<br />Relationship Count: Number of products held by the customer
<br />Amounts change Q4_Q1: Change in transaction amount in Q4 over Q1
<br />Months on book:  Number of months the customer stayed with the bank

**Exploratory Data Analysis**

The churned customers are very few in the dataset. 83.93% of customers remain with the bank and attired customers make only 16.07%, so this is highly skewed. 
<br /> <br />Each customer is uniquely identified by Client Number. Customer Age ranges from 25 to 70, with most of them between 40 and 55. They are sorted into categories. 
Outliers are noticed on these columns Customer_Age, Months_on_book, Months_Inactive_12_mon, Contacts_Count_12_mon, Credit_Limit, Avg_Open_To_Buy, Total_Trans_Amt, Total_Trans_Ct, and Total_Ct_Chng_Q4_Q1. There is a strong relation between gender and income category.
Heat Map indicating correlation of numerical attributes 

<img src="https://github.com/padmaparam/Screenshots/blob/main/CustomerChurn/HeatMap.png" style=" width:100px ; height:100px " />



