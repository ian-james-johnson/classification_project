# classification_project
The first project for machine learning at Codeup
Telco Classification Project
Project Planning
Plan -> Acquire -> Prepare -> Explore -> Model & Evaluate -> Deliver 

Telco is a telecommunications company that has a problem: too many customers are churning. The goal of this project is to develop machine learning classification models that can help determine the reasons for high customer churn rates. These models will be developed using Python.
Business Goals 
Find drivers of customer churn 
Develop a machine learning classification model that will predict customer churn

Executive Summary
The primary drivers of churn are contract type, payment type, and internet type 
Autopay helps to mitigate churn 
The utility options (online security, online backup, tech support) are less common among the customers, but customers who do have them are less likely to churn 
The entertainment option (streaming movies/tv) did have statistically significant impact on churn
Why are our customers churning? 

Do the basics of the customer account influence churn (internet type, contract, payment method)? 
Do utility options (security, backup, tech support) influence churn? 
Do entertainment options (streaming movies/tv) inflence churn? 

Hypothesis 
H0: Autopay does not affect churn rate 
Ha: Autopay does affect churn rate
Prepare Data 
Plan -> Acquire -> Prepare -> Explore -> Model & Evaluate -> Deliver
Preparation Takeaways 
Encoded all categorical variables 
Removed id features that were used as table keys in SQL 
Converted total_charges to numeric data type, and filled nulls with the median value 
Created new column to show if payment was automatic or not
Explore Data 
Plan -> Acquire -> Prepare -> Explore -> Model & Evaluate -> Deliver 
Questions to be discovered: 
Do the basics of the customer account like autopay influence churn? 
Do utility options (security, backup, tech support) influence churn? 
Do entertainment options (streaming movies/tv) inflence churn? 

Hypothesis 
H0: Autopay does not affect churn rate 
Ha: Autopay does affect churn rate

Takeaways from univariate exploration 
In regards to the previous questions: 
Most customers have autopay 
Most customers with internet do not have the utilities (online security/backup, tech support) 
Most customers with internet do have streaming movies/tv 

Other observations: 
Gender is approximately half and half 
Most customers (83%) are not senior citizens 
Approximately half of customers have partners 
Most customers (69%) do not have dependents 
Most customers (90%) do have phone service 
In terms of customers having internet: none > DSL > fiber optic
However, most customers with internet do have device protection 
The most common contract length is 2 years, but 1 year is only slightly higher than month-to-month 
Most customers have paperless billing 
Credit card (autopay) is the most common payment type, the other types are similar to each other 
Tenure looks like an upside-down bell curve, with peaks on either tail 
Monthly charges looks like a bell curve, but right skewed and with a large peak on the right tail (lowest cost)
Total charges peaks at the lowest cost, then has several large drops, then the number of customers with higher charges continually shrinks

Takeaways from the bivariate exploration: 
In regards to the previous questions: 
Autopay had a statistically significant effect on churn 
The utility and entertainment options also had statistically significant effect on churn 

Other observations: 
Phone service and gender where the only features without statistical significance in chi2 tests 


The lowest p values for categorical features were: 
contract_type p=10**-146 
online_security p=10**-106 
tech_support p=10**-105 
internet_service_type p=10**-87 
payment_type p=10**-76 
online_backup. p=10**-71

Takeaways from overall exploration 

- gender and phone_service had little impact on churn, and can be safely dropped from models 

I want to limit the amount of categorical variables because there are too many 
I believe that the following categorical variables should be used: 
- contract_type 
- payment_type 
- internet_service_type 
- online_security 
- online_backup 
- tech_support 

- Part of the reason that I chose these features is that they have p values less than 10^-70 
- A low p value does not necessarily mean affecting a large number of customers, but it does show a strong relationship, and is a starting point 
- Most customers did not have these utilities, but those that did were less likely to churn 

- I believe that the quantitative variables should be tenure and monthly_charges 
- I am dropping total_charges because it is mostly a function of tenure and monthly_charges 
- In addition, I don't think that total_charges is a good feature for the specific questions that I am asking now 
- total_charges could be useful for predicting how much to invest in retaining customers while retaining a profit, but I don't think that it drives customer decisions 

The purpose of this strategy of removing features is to remove noise so that I can focus on the signal

Takeaways for decision tree model 
The full and abreviated models did not outperform baseline 2
Baseline 2 has good accuracy and is not overfit on the decision tree

Takeaways for KNN model 
The KNN model shows signs of over-fitting 
The KNN model slightly underperforms the tree model on validation

Takeaways for logistic regression model 
The logistic regression model slightly increased in accuracy during validation 
The slight increase in accuracy may be a statistical fluctuation 
I am selecting this model for the test phase because it does have the highest accuracy

Takeaways from test phase 
Accuracy of model does not drop with test data as compared to train and validate data 
This shows that the model has a good fit to the data and can be expected to make reliable predictions with new data

Deliver 
Plan -> Acquire -> Prepare -> Explore -> Model & Evaluate -> Deliver 
Autopay had a statiscally significant impact on on churn rates in chi2 tests. 
Payment method was an important part of baseline 2, which was an improvement over the first baseline. 

The utility options had statistically significant impact on churn rate, but did not seem to influence the decision tree models. 
This could be because of noise, a large number of customers did not have internet. This resulted in 'no internet' values for many records in the utility columns. 
Perhaps this could addressed by dropping all customers who do not have phone service.



