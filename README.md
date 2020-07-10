# Bank Customer Segmentation (Clustering)

# Problem Statement
## Context
Some banking institutions use marketing campaigns to make clients subscribe to their services. One of those services is the term deposit, which restricts withdrawing the deposit until the term ends. This deposit allows a higher flexibility in budget management because it doesn't affect the "liquidity coverage ratio" (the amount of money that the bank has to be able to pay instantly). In this project marketing segmentation will be done.

## Goal
The goal is to divide all clients into distinct market segments by answering the following questions:
* By which distinct features each segment can be characterized?
* What type of customers marketing team should focus on for their next marketing campaign?

# Data Exploration
## Data Source
I used "Bank Marketing" dataset from Kaggle provided by user Henrique Yamahata. [https://www.kaggle.com/henriqueyamahata/bank-marketing?select=bank-additional-full.csv]

## Data description
Attributes can be divided into the following groups:

### Client data:
* Age (numeric)
* Job : type of job (categorical: 'admin.', 'blue-collar', 'entrepreneur', 'housemaid', 'management', 'retired', 'self-employed', 'services', 'student', 'technician', 'unemployed', 'unknown')
* Marital : marital status (categorical: 'divorced', 'married', 'single', 'unknown' ; note: 'divorced' means divorced or widowed)
* Education (categorical: 'basic.4y', 'basic.6y', 'basic.9y', 'high.school', 'illiterate', 'professional.course', 'university.degree', 'unknown')
* Default: has credit in default? (categorical: 'no', 'yes', 'unknown')
* Housing: has housing loan? (categorical: 'no', 'yes', 'unknown')
* Loan: has personal loan? (categorical: 'no', 'yes', 'unknown')

### Current campaign
* Contact: last contact communication type (categorical: 'cellular','telephone')
* Month: last contact month of year (categorical: 'jan', 'feb', 'mar',…, 'nov', 'dec')
* Dayofweek: last contact day of the week (categorical: 'mon','tue','wed','thu','fri')
* Duration: last contact duration, in seconds (numeric). Important note: this attribute highly affects the output target (e.g., if duration=0 then y='no').
* Campaign: number of contacts performed during this campaign and for this client (numeric, includes last contact)

### Previous campaign 
* Pdays: number of days that passed by after the client was last contacted from a previous campaign (numeric; 999 means client was not previously contacted)
* Previous: number of contacts performed before this campaign and for this client (numeric)
* Poutcome: outcome of the previous marketing campaign (categorical:'failure','nonexistent','success')

### Social and economic context attributes
* Emp.var.rate: employment variation rate - quarterly indicator (numeric)
* Cons.price.idx: consumer price index - monthly indicator (numeric)
* Cons.conf.idx: consumer confidence index - monthly indicator(numeric)
* Euribor3m: euribor 3 month rate - daily indicator (numeric)
* Nr.employed: number of employees - quarterly indicator (numeric)

### Output variable
* y - has the client subscribed a term deposit? (binary: 'yes', 'no')

# Model building
Since I there is a considerable number of useful categorical data, I used Kmodes clustering method.

## Number of clusters
![Elbow Method](https://github.com/aza-atabayev/bank-marketing-clustering/blob/master/images/elbow.png?raw=true)

## Result
![Elbow Method](https://github.com/aza-atabayev/bank-marketing-clustering/blob/master/images/newplot.png?raw=true)

# Conclusion
## Insights
* The best way to segment customers is based on their marital status. This clustering results in 3 segments of single, married and divorced with 9443, 17492 and 3553 customers respectively.
* Married clients are more willing to accept bank's marketing campaigns and have higher percentage of "loyal" customers based on the last 2 campaigns.
* Married clients constitute the biggest cluster.

## Produced value (recommended actions)
* Since married clients is the biggest cluster, has higher marketing campaign efficiency and loyalty, marketing team should target them as the most valuable segment of bank customers.
* In order to evaluate efficiency of the future marketing campaign that targets married customers, we should check whether mentioning cluster in the data improves predictions. If it does, then marketing team did a good job in focusing customers based on their marital status.
