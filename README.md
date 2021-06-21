# Bank Customer Churn Prediction
The bank decided to collect data from 6 months period to evaluate the problem after noticing increase in the number of customers leaving the bank. This data set contains of 10,000 customers were selected randomly among three countries – France, Germany and Spain. The dataset is well-labelled to explain all its columns and the target variable is a binary variable reflecting the fact whether the customer left the bank (closed account) or continues to be a customer. The dataset was obtained from the website of [Kaggle]. 

## Table Content
* [Problem Statement](#problem-statement)
* [Technologies](#technologies)
* [Features](#features)
* [Summary of Dataset](#summary-of-dataset)
* [Predictive Model Workflow](#predictive-model-workflow)
* [Conclusion](#conclusion)
* [Room for Improvement](#room-for-improvement)

## Problem Statement
The project objective is to develop churn prediction model that how likely its current customers will be leaving the bank in near future.

The problem here is a classification problem to classify a customer whether he or she will exit or not based on his or her credit score, region, gender, age, tenure, balance, estimated salary and etc. We will be dealing with binary classification by using 3 algorithms like logistic regression, decision trees and SVM to predict the test and select the best model that able to provide the better accuracy.

## Technologies
Project is created with: 
* Python

## Features
The feature of the dataset have as per below: 
1.	RowNumber: corresponds to the record (row) number
2.	CustomerId: The customer ID created by the bank
3.	Surname: The customer surname
4.	CreditScore: The customer credit score`
5.	Geography: The country of the customer (Germany/France/Spain)
6.	Gender: The gender of the customer (Female/Male)
7.	Age: The age of the customer
8.	Tenure: The customer's number of years in the bank
9.	Balance: The customer's account balance
10.	NumOfProducts: The number of bank products that the customer uses
11.	HasCrCard: Does the customer has a credit card? (0=No,1=Yes)
12.	IsActiveMember: Does the customer has an active membership (0=No,1=Yes)
13.	EstimatedSalary: The estimated salary of the customer
14.	Exited: Churned or not? (0=No,1=Yes)

## Summary of dataset 
- All features look normal and there is no extreme values for any feature. 
- Most people are from France and there are more males (5457) than females. There are no sparse classes. 
- In our data sample there are more males than females. 
- Majority of customers are from France, about 50%. Customers from Germany and Spain around 25% each. 
- Credit Score: Observed that average and median values are overlap and normal distribution.
- Age: Maximum age is 92 however average and median for Age seems close to each to others besides. 
- Tenure: Average and median values almost the same. 
- Balance: Average balance is higher than median value. 
- EstimatedSalary: Outlier status is not observed. Average and median values are considered the same. 
- Here most interest things to notice is 3617 customer of this bank has 0 balance and out of 3617, 3017 didn't exited from the bank.

## Predictive Model Workflow
- Data Pre-processing before model training.
    i. Handle missing values, remove variables and check for outlier
    ii. Encode categorical feature and scale numerical feature 
- Model Training - It is an imbalance dataset hence we use stratify to split for traning and testing in order to split the dataset equally. 
    - Use [Lazy Predict](https://pypi.org/project/lazypredict/#description) library to compare across all the models available and find top 3 baseline models to test and do hyperparameter tuning. However, metric results for all the model looks identical. Hence we use metric - logloss for comparison from the top 8 models chosen from the results of lazy prediction.
- Gridsearch CV used for hyperparamter tuning for the 3 top models after comparing the metric results - logloss. 
    - Random Forest Classifier 
    - LGBM Classifier
    - AdaBoost Classifier
- Model Validation - use confusion metric to validate how good is the model and compare among the 3 models after trained. 

## Conclusion
AdaBoost Classifier have the best performance which have the highest ROC score and the best true positive and false negative rate compare to others. 

Based on the feature importance, we know that Age, Estimated Salary and the balance of the money customers deposited into the bank will affect the customer to exit the bank or not.
    - Target on the customers who have frequent withdrawal from the bank or monthly regular deposit not reflected for a period, i.e. Salary. 
    - To have some client recovery services to keep the customers and get direct feedback from customers.
The bank may also focused on those customers that are in the age range to be churn that have shown in the chart and offering better incentives to them in order to minimize churn and keep more customers. 


## Room for improvement
- use SHAP to have better understanding for the feature importance in training model. 
- train the feature separately and understand the important of feature. 


This project was done as part of DS105 project requirement of Applied Data Science with Machine Learning in MAGES of Institute of Excellence - 2021. 


[Kaggle]:https://www.kaggle.com/santoshd3/bank-customers
