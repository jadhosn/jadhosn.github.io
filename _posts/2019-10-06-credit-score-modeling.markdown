---
title:  "Peer-to-peer credit risk modeling"
date:   2019-10-06 15:00:00
categories:  
tags: [Project]
outside_link: "N"
link: ""
tools: [Python, Jupyter]
---
In this tutorial, I am going to walk you through how to set up your data for credit modeling. The conent of the article is based on multiple online resources, and some experience that I have acquired during my day-to-day learnings. 

## Data Sources:
1. Using Lending Club data, there's this link on kaggle that seems to supply good data. I might want to look further into it [link](https://www.kaggle.com/wordsforthewise/lending-club)
2. [link](https://www.lendingclub.com/info/download-data.action) she downloaded the data up to 2018

[Peer-2-peer loan prediction - Medium Article](https://medium.com/@jiaminhan/peer-to-peer-loan-default-prediction-using-lending-club-data-3f75886cb1e)
- Source used Lending Club
- Introduction about Lending club (connecting investors and borrowers directly)
- The default rate of in peer-to-peer loans is higher than traditional loans (but how does it compare with deep sub-prime lending?)
- Making a data-driven assessment of the loan risk 
- EDA: correlation study in regards of the outcome, remove features that are forward looking.
- She ended up with 28 features, followed by typing them, bookending the values, one-hot enconding and feature creation 
for some attributes that she thought might be interesting
- She added a couple attributes (length of employment, home ownership, loan purpose)
- FICO average, length of credit history, current employment history, region of residence in the US (maybe even last 4 zips?)
- How to define a defaulted status 
- What are the different types of models that we want to fit? This is a classification problem 
    - GBT
    - SVM
    - RF
    - Logit
    - NB
    - KNN
    - DT
- What are the metrics that we want to compare the different models? AUC, F1 metric? 
- How to treat the imbalanced distribution (undersampled dataset with equal number of good and bad loans)
- Feature Importance: 
    - Average FICO
    - CO times within 12 months
    - Total Credit Revolving balance
    - Debt to income ratio 
    - Total number of credit lines 
    - Interest rate
    - Loan description length 
    - Time of delinquency in 2 years 
    - Number of derogatory records 
    - Loan application year 
- List the tools you used (Jupyter, pandas, numpy, matplotlib, seaborn, scikit-learn, statsmodels)
- Use the remaining features to analyze the model's performance 
- Invesitgate dimensionality reduction to avoid correlation? 
- What is CatBoost?


## Introduction: 
This is an effort to add more clarity to credit modeling. In terms of resources,
there are multiple resources. I am a fan of a detailed step-by-step [tutorial](https://www.worldprogramming.com/us/blog/credit_scoring_development_pt1) from CreditKarma

### What is a credit score? 
Lenders (whether auto loans, credit cards, housing etc.) are looking to assess the risk of default for each customer so the lender can decide who to offer a credit line. 

Companies that are no longer the generic credit score depend on credit bureau data sources, as well as the advancement in machine learning and available alternative data. 

We are used to higher your score, you are more credit worthy 

Credit scoring is assessing the likelihood of a customer defaulting on a credit obligation (delinquent)

### Different types of scores: 
There are different stages of the customer's journey into a loan, or a credit line: 
#### A - Application Score:

Before originating a loan

#### B - Behavorial Score:

#### C - Collection Score:

### Modeling Techniques: 
Following the Credit Scorecard model (logistic regression) and we like it because it's output can be used directly as probabilities. It's intuitive and easy to explain. 

1. Design, develop and accurate and stable credit risk model 
2. Make sure that other data scientists can replicate and follow my steps and obtain the similar results 

3. How do we tell a 'bad' customer from a 'good' customer? What's the ideal performance window to look at? 60, 90 or 180 days past due?
--> the answer should depend on the business needs in the case but all these different windows can be investigated 

4. Definitely worth putting these questions in an EDA format: 
Question 4: What are the main characteristics that tell "bad" from "good" customers?
Answer 4: This is part of my theoretical framework, specifically identification of independent variables. I will carry out data exploration to establish the relationships between customers’ characteristics and the outcome variable. For example, "customers that have regular income are less likely to default" or "older customers are less likely to default". In scientific terminology, each characteristic, such as income or age, represents a hypothesis that is tested for significance using a statistical method such as logistic regression. Based on statistical analysis, I can decide whether to retain such variables in the model.

5. When you are developing an end-to-end machine learning pipeline, there are certain constraints that one must keep in mind: 
Having a multidisciplinary nature, data mining projects require consideration from different perspectives, including:

Business – for assessing potential business benefits
Data science – for creating a theoretical model
Software development – for developing a viable software solution

6. What are those? 
Examples of two popular methodologies are Agile-scrum and CRISP-DM (Cross Industry Standard Process for Data Mining)

I am using an agile-scrum methodology 

7. What are the key elements at play here:
- dependent variable (loan status)
- predictors (customer attributes, employment, income, bank and card behavior)