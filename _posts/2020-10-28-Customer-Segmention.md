---
layout: post
title: "Customer Segmentation using K-means clustering and PCA"
date: 2020-10-28
---

<h2><strong> Goal of this project </strong></h2>
<p>The goal of this project is to develop a customer segmentation to define marketing strategy. The
sample Dataset summarizes the usage behavior of about 9000 active credit card holders during the last 6 months. The file is at a customer level with 18 behavioral variables.</p>

<ul><li>Data includes transactions frequency, amount, tenure etc</li>
    <li>Leverage K-means clustering and PCA to do the segmentation</li></ul>

<h2><strong> Analysis</strong></h2>
<ul><li><strong>First Customers cluster (Transactors): </strong>Those are customers who pay least amount of interest charges and careful with their money, Cluster with lowest balance (105 dollars) and cash advance (308 dollars), Percentage of full payment = 23%</li>
<li><strong>Second customers cluster (revolvers) </strong> who use credit card as a loan (most lucrative sector): highest balance (5000 dollars) and cash advance (~5000 dollars), low purchase frequency, high cash advance frequency (0.5), high cash advance transactions (16) and low percentage of full payment (3%)</li>
<li><strong>Third customer cluster (VIP/Prime):</strong> high credit limit dollars 16K and highest percentage of full payment, target for increase credit limit and increase spending habits</li>
<li><strong>Fourth customer cluster (low tenure):</strong> these are customers with low tenure (7 years), low balance</li></ul>

<h2> K-means clustering visuals </h2>

![K-means clustering](/assets/Clustering/Kmeans-BALANCE.jpg)
![K-means clustering](/assets/Clustering/Kmeans-CASH_ADVANCE.jpg)
![K-means clustering](/assets/Clustering/Kmeans-TENURE.jpg)
![K-means clustering](/assets/Clustering/Kmeans-PAYMENTS.jpg)
![K-means clustering](/assets/Clustering/Kmeans-PURCHASES_FREQUENCY.jpg)

<h2> First two principal components visuals </h2>

![First two Principal Components](/assets/Clustering/PCA.jpg)

<h2><strong>License of the source data </strong></h2>
<p>Creative Commons Public Domain Dedication
This license is one of the open Creative Commons licenses and is like a public domain dedication. It allows you, as a dataset owner, to use a license mechanism to surrender your rights in a dataset when you might not otherwise be able to dedicate your dataset to the public domain under applicable law.</p>
<a href="https://creativecommons.org/publicdomain/zero/1.0/">cc0: Public Domain</a> 

<h2><strong>Data Source :</strong></h2>
 <a href="https://www.kaggle.com/arjunbhasin2013/ccdata">Kaggle credit card dataset for clustering</a>
 
<h2><strong>Data Dictionary for Credit Card dataset</strong></h2>

| COLUMNS | DESCRIPTION | 
| :------------- | :----------  | 
| CUSTID  | Identification of Credit Card holder (Categorical) |
| BALANCE | Balance amount left in their account to make purchases |  
| BALANCE FREQUENCY | How frequently the Balance is updated, score between 0 and 1 (1 = frequently updated, 0 = not frequently updated) |
| PURCHASES | Amount of purchases made from account |
| ONE OFF PURCHASES | Maximum purchase amount done in one-go |
| INSTALLMENT PURCHASES | Amount of purchase done in installment |
| CASH ADVANCE | Cash in advance given by the user |
| PURCHASES FREQUENCY | How frequently the Purchases are being made, score between 0 and 1 (1 = frequently purchased, 0 = not frequently purchased) |
| ONEOFF PURCHASES FREQUENCY | How frequently Purchases are happening in one-go (1 = frequently purchased, 0 = not frequently purchased) |
| PURCHASES INSTALLMENT FREQUENCY | How frequently purchases in installments are being done (1 = frequently done, 0 = not frequently done) |
| CASH ADVANCE FREQUENCY | How frequently the cash in advance being paid |
| CASH ADVANCE TRX | Number of Transactions made with "Cash in Advanced" |
|PURCHASES TRX |Number of purchase transactions made |
|CREDIT LIMIT |Limit of Credit Card for user |
|PAYMENTS |Amount of Payment done by user |
|MINIMUM_PAYMENTS | Minimum amount of payments made by user |
|PRC FULL PAYMENT |Percent of full payment paid by user |
|TENURE |Tenure of credit card service for user |

<h2><strong>Links to artifacts</strong></h2>
<p><a href="/assets/Clustering/Credit_Card_Customer_Segmentation.ipynb">Code link</a></p>

