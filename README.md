# **Loan Status Prediction App**
********************************************

# Project Overview
* I developed a model that predicts whether banks will give credit based on the characteristics of customers applying for credit and their past responsibilities (credit rating, etc.)

# Libraries Used and Python Version
* **Python**:3.10.9
* pandas , missingno , sklearn , pickle

# Information About The Data Set 
* The columns in the dataset are as follows:

    * **ID** : A unique identification number for each customer.
    * **Customer ID** : A unique customer ID number for each customer.
    * **Current Loan Amount** : The customer's current loan amount.
    * **Term** : The loan term is usually expressed as a monthly payment schedule.
    * **Credit Score** : A customer's credit score is a numerical value based on credit history, payment status of loan debts, and other factors.
    * **Annual Income** : The customer's annual income.
    * **Years in current job** : How many years the customer has worked at their current job?
    * **Home Ownership** : The client's home ownership status, for example, for rent, homeownership, or mortgage holder.
    * **Purpose** : The purpose of getting a loan, for example, to buy a car, renovate a house, or consolidate debts.
    * **Monthly Debt** : The customer's monthly debt payment amount.
    * **Years of Credit History** : The number of years the customer has a credit history.
    * **Months since last delinquent** : How many months ago the last payment delayed was.
    * **A Number of Open Accounts** : The number of customers' open credit accounts.
    * **A number of Credit Problems** : Number of customers' credit problems, such as payment delays or debt collection.
    * **Current Credit Balance** : Customer's current credit balance.
    * **Maximum Open Credit** : The maximum credit limit for the customer's open credit accounts.
    * **Bankruptcies** : Number of bankruptcies of the customer.
    * **Tax Liens** : The number of customers' tax liabilities.

* As you can see, there is no information in the dataset about whether they give credit to customers, so I will use the k means algorithm for my forecasting model.


# Cleaning The Data Set 
* First , I deleted the "ID" and "CustomerID" columns that I thought were unnecessary
* I examined the percentages of null values in the dataset.

![alt text](https://github.com/gamzeaslan/Loan_Status_Prediction/blob/main/null.png "null percent")

* As you can see from the picture above, the null value in the " Months since last delinquent " column is 54%. So I'm removing this column from my dataset

* I visualize this situation using missingno to find out if there is a coincidence among the remaining variables that contain null values.


![alt text](https://github.com/gamzeaslan/Loan_Status_Prediction/blob/main/msno.png "msno.matrix")
* As you can see from the table above, I noticed that the null values in "CreditScore" and "AnnualIncome" are the same, but since I don't fully understand the relationship between them, I will follow the standard fill and delete operation.
* I filled in null values in numeric columns using KNNImputer
* Afterward, I performed the following few operations to bring the dataset to the appropriate form for the model:
    * I removed the “years , year , < , +” signs in the Years in current job column
    * I used get_dummies for categorical variables
    * I converted variables that are actually numeric but of type object in the dataset to int

# Model Selection
* As I said above, I cannot use classification algorithms in this data set when there is no information about whether banks give credit to customers or not. I used k means algorithm for this model
* Finally, I measured the success of the model using silhouette_score(-1,1).silhouette_score value is 0.98
