---
title:  "Credit Scoring Tutorial - Medium TBD"
date:   2019-10-06 15:00:00
categories:  
tags: [Credit, Credit Scoring, Tutorial, Side-Project]
outside_link: "N"
link: ""
---
# Credit Scoring - Project, Data Wrangling (Tutorial):
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
- 