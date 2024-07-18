# RBC_BankAnalysis
# Customer Churn Prediction for Bank


### Dashboard Link : https://app.powerbi.com/Redirect?action=OpenApp&appId=0120bb79-a3f1-4708-9c8c-69fcdabbe844&ctid=712d7553-2038-4dae-ac24-abc98ae7cb00







## Problem Statement

This project aims to analyze and predict customer churn for a bank. Customer churn is a critical metric for banks as retaining existing customers is often more cost-effective than acquiring new ones. Understanding the factors that influence customer churn can help in developing strategies to improve customer retention.

The banking industry faces a significant challenge in retaining customers, often referred to as customer churn. Customer churn not only affects the bank's revenue but also its reputation and growth potential. The bank seeks to identify key factors contributing to customer churn and develop effective strategies to retain customers. The objective is to leverage data analytics to understand the patterns and predictors of churn, thereby enabling the bank to implement targeted interventions to reduce churn rates and enhance customer loyalty.

Analysis will not only help you understand the factors influencing customer churn but also demonstrate your ability to handle and analyze complex datasets. 





## Tables and Columns 
- As we have imported files in csv format all the files were cleaned and ready for transforming and if in case small transformations and cleaning is done in inbuilt ETL of power BI 
- A dummy table was created to store all DAX measure we implimented for out report 

### Table and Column  
    DateMaster = CALENDAR(FIRSTDATE(Bank_Churn[Bank DOJ]),LASTDATE(Bank_Churn[Bank DOJ]))

    year = YEAR(DateMaster[Date])

    Month = MONTH(DateMaster[Date])

    Month name = FORMAT(DateMaster[Date],"MMM")

    Credit type = SWITCH(TRUE(),Bank_Churn[CreditScore]>=800 && Bank_Churn[CreditScore]<=850 ,"Excellent" ,
    Bank_Churn[CreditScore]>=740 && Bank_Churn[CreditScore]<=799 , "Very good" ,
    Bank_Churn[CreditScore]>=670 && Bank_Churn[CreditScore]<=739 , "good" ,
    Bank_Churn[CreditScore]>=580 && Bank_Churn[CreditScore]<=669 ,"Fair" ,
    Bank_Churn[CreditScore]>=300 && Bank_Churn[CreditScore]<=579 ,"poor"
    )



 ### DAX expressions or measures

    Active Customer = CALCULATE(COUNT(Bank_Churn[CustomerId]),ActiveCustomer[ActiveCategory]="Active Member")

    Toatal Customer = COUNT(Bank_Churn[CustomerId])

    Inactive Customer = [Total Customer] - [Active Customer]

    Credit card holder = CALCULATE(COUNT(Bank_Churn[CustomerId]),CreditCard[Category]="cedit card holder")

    Non credit card holder = CALCULATE(COUNT(Bank_Churn[CustomerId]),CreditCard[Category]="non credit card holder")

    Exit Customer = CALCULATE([Total Customer],ExitCustomer[ExitCategory]="Exit")

    previous month exit custome = CALCULATE([Exit Customer],PREVIOUSMONTH(DateMaster[Date]))





### Data Dictionary
- RowNumber: corresponds to the record (row) number and has no effect on the output.
- CustomerId: contains random values and has no effect on customer leaving the bank.
- Surname: the surname of a customer has no impact on their decision to leave the bank.
- CreditScore: can have an effect on customer churn, since a customer with a higher credit score is less likely to leave the bank.
    
    Credit score:
    - Excellent: 800–850
    - Very Good: 740–799
    - Good: 670–739
    - Fair: 580–669
    - Poor: 300–579

- Geography: a customer’s location can affect their decision to leave the bank.
- Gender: it’s interesting to explore whether gender plays a role in a customer leaving the bank.
- Age: this is certainly relevant, since older customers are less likely to leave their bank than younger ones.
- Tenure: refers to the number of years that the customer has been a client of the bank. Normally, older clients are more loyal and less likely to leave a bank.
- Balance: also a very good indicator of customer churn, as people with a higher balance in their accounts are less likely to leave the bank compared to those with lower balances.
- NumOfProducts: refers to the number of products that a customer has purchased through the bank. 
- HasCrCard: denotes whether or not a customer has a credit card. This column is also relevant, since people with a credit card are less likely to leave the bank.
    - 1 represents credit card holder
    - 0 represents non credit card holder
- IsActiveMember: active customers are less likely to leave the bank.
   - 1 represents Active Member
   - 0 represents Inactive Member
- Estimated Salary: as with balance, people with lower salaries are more likely to leave the bank compared to those with higher salaries.
- Exited: whether or not the customer left the bank.
   - 0 represents Retain 
    - 1 represents Exit
- Bank DOJ: date when the Customer associated/joined  with the bank.



### Data Gathering:

Please use the following data assets to pull the data related to Bank customer and associated details.

- ActiveCustomer 
-  Bank_Churn
- CreditCard
- CustomerInfo
- ExitCustomer
- Gender
- Geography

### Churn Analysis
Analyse the data and bring out few insights on the customer Churn.
It is advantageous for banks to know what leads a client towards the decision to leave the company.
Churn prevention allows companies to develop loyalty programs and retention campaigns to keep as many customers as possible.








# Snapshot of Data Model (contains facts and dimension table )


![Screenshot (12)](https://github.com/user-attachments/assets/5c53ab68-4127-423e-8a3a-ec2cb8d4cce8)



# Snapshot of Customer Analysis Summary

![Screenshot (14)](https://github.com/user-attachments/assets/74b509c5-033e-47c9-bbb7-367c1d479a9a)



# Snapshot of Customer Churn percentage
![Screenshot (15)](https://github.com/user-attachments/assets/848b8d75-56ac-4eb4-a9e0-223bbb23cad0)


# Snapshot of Workspace
![Screenshot (16)](https://github.com/user-attachments/assets/5a89a5a2-9e1e-4a65-adeb-cbb9df0a5d72)

  # Snapshot of Published app      
![Screenshot (17)](https://github.com/user-attachments/assets/7e0ee49d-031d-4792-ba86-46812d09d107)


## Insights
A single page report was created on Power BI Desktop & it was then published to Power BI Service.

Following inferences can be drawn from the dashboard;


### Total number of customer : 10000
### Total number of Active customer : 5151
### Total number of Inactive customer : 4849
### Total number of Credit card holder : 7055
### Total number of non Credit card holder : 2945
### Exit customer: 2037
### Retain customer : 7963

- Customers with good credit score are likely to less to exit the bank
- Customers with bad credit score are likely to less to exit the bank
- Pulished the app in organizational level
