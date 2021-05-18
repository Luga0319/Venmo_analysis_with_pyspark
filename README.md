## Venmo Analysis with Pyspark 
Venmo is one of top transaction app which is very convinent for transactions between friends. People would leave some text or emojis while transfering money. 
Tons of texts and emojis made it difficult to analyze what is happening in the Venmo community. Thus, it's important if we could use word & emoji dictionary to classify
the comments left by users so that we could perform some analysis. Another interesting topic is to analyze the users' social network by analyzing the transactions among them 
which would help us predict the level of user's activity and strength of relationship with his/her friends.

### 1. Problem Statement 
Predicting the number of transactions in next year based on the text & emojis within transactions and the social network profiles

### 2. Data Description
#### a. A snappy parquet dataset including millions of public transaction records. (Didn't publish due to pricate issue) 
#### b. A word classification dictionary 
#### c. A emoji classification dictionary 

### 3. Methodology
The code is compiled on the Google Cloud Platform Virtual Machine 

---------

#### Text & Emoji Analysis

1. Tokenized each transaction comment (text & emoji) and label each transaction record with a category extracted from dictionary 
2. Built a dynamic transaction profile, displaying the percentage of each category take in the user's total transaction history. i.e. 

|  User_id      |  month  |  People   |  Food   |    Activity    |  Event  |
| ------------- |:-------:|:---------:| -------:| :-------------:| -------:|
| 1             |     1   | null      | 0.26    |     0.32       |  0.42   |
| 16            |     1   | 0.35      | 0.5     |     0.10       |  0.05   |
| 26            |     2   |  0.15     | 0.25    |     0.20       |  0.40   |

---------

**Social Network Analysis**
1. Analyze the user's social network based on the transaction records with other users ---- find out his/her friends and friends' friends
2. Calculate clustering coefficents based on their social network [reference](https://en.wikipedia.org/wiki/Clustering_coefficient "wikipage")
3. Calculate the page rank of each user

---------

**Predictive Analysis with MLlib**

1. Create dependent variableY,i.e. the total number of transactions at lifetimepoint 12
2. Create the recency and frequency variables based on CRM theory
3. Used **Linear Regression Model** and **Random Forest** to predict 
4. Plot the MSE for each lifetime point
![](https://github.com/Luga0319/Venmo_analysis_with_pyspark/blob/main/MSE.png "MSE plot")

