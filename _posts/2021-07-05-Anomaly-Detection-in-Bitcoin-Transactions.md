---
layout: post
title: "Anomaly Detection in Bitcoin Transactions"
date: 2021-07-05
---

<h3>Abstract</h3> 
<p>Bitcoin has become a preferred method for transferring money for illicit economicactivity such as ransomware payments and money laundering. Robust detection of these illicit transactions in the Bitcoin blockchain is crucial for anti-money laundering operations.  Major challenges for illicit transaction detection includethe lack of transaction labels, the massive size of the bitcoin network, and the fact the bad actors work to mask their activity and avoid detection.   Previous researchers have proposed anomaly detection(unsupervised methods), supervised learning, and active learning to classify illicit transactions. Supervised learning is necessary to classify illicit transactions as illicit transactions do not correlate with anomalies in the dataset. Unsupervised learning methods are useful when there’s scarcity of labels.  Active learning is a useful modification of supervised learning for illicit transaction classification as real world bitcoin datasets have very few licit/illicitlabels. We compare the performance of these methods using the Elliptic dataset.</p>

<h3>Data Source</h3>
<p>We use the Elliptic Data Set which contains 200K Bitcoin transactions, a subset of which are tagged as belonging to either licit or illicit categories. This dataset is a time series graph where Bitcoin transactions are nodes in the network and directed payment flows are edges. Along with licit or illicit tags, the nodes are also tagged with 166 additional node features. 94 of the features are local information about the transaction, such as the time step, transaction fee, and output volume. 72 features are aggregated features which are aggregated information from the nodes one-hop backward and forward. The data is divided evenly into 49 time steps. In each time step, the transactions are connected as a single component. There is an important event occurs at time step 43 which is a sudden closure of a dark market. This causes the number of illicit data to decrease significantly after the shut down.</p>

<p>We use this dataset to evaluate the effectiveness of anomaly detection methods to classify illicit transactions, reproduce supervised learning classification method employed in previous studies, including AL, and evaluate the performance of a modification to the AL method that uses the network graph to aid in selecting datapoints.</p>

<h3>Repository structure</h3>

```
├── README.md
├── LICENSE
├── writeup.pdf
├── data
├── images
├── notebooks
```
<h3>How to run the notebook</h3>

* Install Anaconda
* Using a terminal or cmd, navigate to the src folder.
* Launch jupyter by running: jupyter notebook
* Select the notebook of interest. (Start at data_cleaning.ipynb for the full process or analysis.ipynb for the final report.)

<h3>Resources used</h3>

This analysis was prepared using Python 3.8 running in a Jupyter Notebook environment.  
Documentation for Python can be found here: https://docs.python.org/3.8/  
Documentation for Jupyter Notebook can be found here: http://jupyter-notebook.readthedocs.io/en/latest/  

The following Python packages were used and their documentation can be found at the accompanying links:

* [pandas](https://pandas.pydata.org/)
* [numpy](https://numpy.org/)
* [IPython](https://ipython.org/)
* [matplotlib](https://matplotlib.org/)
* [seaborn](https://seaborn.pydata.org/)

<h3>Detailed report</h3>
<a href='https://github.com/lakshmi2688/Illicit-transactions-detection-in-Bitcoin-system/blob/main/Illicit_transactions_detection_in_the_Bitcoin_blockchain.pdf'>Report Link</a>

<h3>Link to source code in Github</h3> 
<a href= "https://github.com/lakshmi2688/Illicit-transactions-detection-in-Bitcoin-system">Source code</a>
