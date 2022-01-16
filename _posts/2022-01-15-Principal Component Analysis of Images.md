---
layout: post
title: "Principal Component Analysis of Images"
date: 2022-01-15
---

<h3>Abstract</h3> 
<p>The goal of this analysis is to implement PCA using Eigen Decomposition, Scikit Learn and Power Interation Algorithms and understand the steps, and assumptions of the technique.</p>

<p>Principal component analysis (PCA) is a method that is used to transform a set of variables into a smaller set of variables that explain most of the variability in the original dataset. PCA has no response variable, so it is an "unsupervised" learning method.The principal components are orthogonal to one another, they are statistically linearly independent of one another… which is why our columns of reduced data are linearly independent of one another!</p>

<p>Why would we want to use such a method? It can be useful for data compression and visualization, and the results can also be used in other downstream tasks, such as regression, classification, and clustering. Using the results from PCA instead of the original features often leads to less noisy results, as the first few principal components tend to contain the signal in data (as opposed to the noise). One downside is that after applying PCA, the regression and classification coefficients often become uninterpretable.</p>

<p>The goal of PCA is to project a dataset consisting of observations  𝑥1,…,𝑥𝑛 ∈ ℝ𝐷  onto a lower dimensional subspace of dimension p such that we maximize the variance of the projected data. An equivalent way of viewing PCA is that we are projecting the data onto a subspace that is "closest" to the observations. If we try to reconstruct the original data from the data projected using PCA, we will get the "best" possible reconstruction.The first principal component is the direction that captures the most variance. The second principal component is the direction that is orthogonal to the first direction and captures as much variance as possible, etc. Each principal component is orthogonal to the previous components.</p>

<p>Prior to performing PCA we should standardize the variables to have a mean of zero and a standard deviation of 1. Take the matrix of independent variables X and, for each column, subtract the mean of that column from each entry. (This ensures that each column has a mean of zero.). Decide whether or not to standardize. Given the columns of X, are features with higher variance more important than features with lower variance, or is the importance of features independent of the variance? (In this case, importance means how well that feature predicts Y.) If the importance of features is independent of the variance of the features, then divide each observation in a column by that column’s standard deviation </p>

<p>First, the covariance matrix XᵀX is a matrix that contains estimates of how every variable in X relates to every other variable in X. Understanding how one variable is associated with another is quite powerful.</p>

<p>Second, eigenvalues and eigenvectors are important. Eigenvectors represent directions. Think of plotting your data on a multidimensional scatterplot. Then one can think of an individual eigenvector as a particular “direction” in your scatterplot of data. Eigenvalues represent magnitude, or importance. Bigger eigenvalues correlate with more important directions.</p>

<p>Lots of variability usually indicates signal, whereas little variability usually indicates noise. Thus, the more variability there is in a particular direction is, theoretically, indicative of something important we want to detect.</p>

<h4> Links to Data set and Data dictionary</h4>
<ul><li>The dataset using for this analysis is directly imported from sklearn.datasets</li>


<h3>We cover the following techniques for implmenting PCA</h3>
<ul>
    <li>PCA using Eigen decomposition </li>
    <li>PCA using scikit-learn</li>
    <li>PCA using Power Iteration algorithmn</li>
</ul>


<h3>Link to source code in Github</h3> 
<a href= "https://github.com/lakshmi2688/COVID_Impact_on_US_Households">Source code</a>
