---
layout: post
title: "Principal Component Analysis of Images"
date: 2022-01-15
---

<h3>Abstract</h3> 
<p>The goal of this analysis is to implement PCA using Eigen Decomposition, Scikit Learn and Power Interation Algorithms and understand the steps, and assumptions of the technique.</p>

<p>Principal component analysis (PCA) is a method that is used to transform a set of variables into a smaller set of variables that explain most of the variability in the original dataset. PCA has no response variable, so it is an "unsupervised" learning method.The principal components are orthogonal to one another, they are statistically linearly independent of one another… which is why our columns of reduced data are linearly independent of one another!</p>

<p>Why would we want to use such a method? It can be useful for data compression and visualization, and the results can also be used in other downstream tasks, such as regression, classification, and clustering. Using the results from PCA instead of the original features often leads to less noisy results, as the first few principal components tend to contain the signal in data (as opposed to the noise). One downside is that after applying PCA, the regression and classification coefficients often become uninterpretable.</p>

<p>The goal of PCA is to project a dataset consisting of observations  𝑥1,…,𝑥𝑛 ∈ ℝ𝐷  onto a lower dimensional subspace of dimension p such that we ** maximize the variance of the projected data ** . An equivalent way of viewing PCA is that we are ** projecting the data onto a subspace that is "closest" to the observations **. If we try to reconstruct the original data from the data projected using PCA, we will get the "best" possible reconstruction.The first principal component is the direction that captures the most variance. The second principal component is the direction that is orthogonal to the first direction and captures as much variance as possible, etc. Each principal component is orthogonal to the previous components.</p>

<p>In PCA we are interested in the components that maximize the variance. If one component (e.g. human height) varies less than another (e.g. weight) because of their respective scales (meters vs. kilos), PCA might determine that the direction of maximal variance more closely corresponds with the ‘weight’ axis, if those features are not scaled. As a change in height of one meter can be considered much more important than the change in weight of one kilogram, this is clearly incorrect. 
   
<p>
**Prior to performing PCA we should either standardize the variables to have a mean of zero and a standard deviation of 1 if features are of different scales or demean the data if features are of the same scale**
   
Normalization rescales the values into a range of [0,1]. This might be useful in some cases where all parameters need to have the same positive scale. Standardization rescales data to have a mean (μ) of 0 and standard deviation (σ) of 1 (unit variance).

**We use the covariance matrix when the variable scales are similar and the correlation matrix when variables are on different scales. Using the correlation matrix is equivalent to standardizing each of the variables (to mean 0 and standard deviation 1). In general, PCA with and without standardizing will give different results. Especially when the scales are different.**</p>

<li>Take the matrix of independent variables X and, for each column, subtract the mean of that column from each entry. This is demean and ensures that each column has a mean of zero. Demeaning data but not standardizing is equivalent to computing principal components from the covariance matrix of data. Here all features should be of the same scale. For our example, we calculate PCs from covariance matrix</li>

<li>Decide whether or not to divide by sd. Given the columns of X, are features with higher variance more important than features with lower variance, or is the importance of features independent of the variance? (In this case, importance means how well that feature predicts Y). If the importance of features is independent of the variance of the features, then divide each observation in a column by that column’s standard deviation. Using standardized data is equivalent to computing principal components from the correlation matrix of data. If the features are of different scales, we use this approach.</li>
</p>

<p>First, the covariance matrix XᵀX is a matrix that contains estimates of how every variable in X relates to every other variable in X. Understanding how one variable is associated with another is quite powerful. Building the covariance matrix is the actual first step of PCA. In this step, we will be building a square dxd matrix where each row represents a feature and each column also represents a feature. Each entry represents the covariance between the row feature and the column feature at that position. Covariance tells us how the two features vary with respect to one another. If a given sample has a value above the mean (which we’ve set to zero through demean) for both features then we get a positive result as the product. The same is true if the values for both features are below the mean. Conversely, if one value is below and one is above we will get a negative value. If the covariance for a given pair of features is positive, both of these features tend to increase or decrease together. If the covariance is negative, one feature tends to increase as the other decreases. If the covariance is zero then the two features are unrelated. Correlation is defined as the covariance divided by the product of both standard deviations.</p>

<p>Second, eigenvalues and eigenvectors are important. Eigenvectors represent directions. Think of plotting your data on a multidimensional scatterplot. Then one can think of an individual eigenvector as a particular “direction” in your scatterplot of data. Eigenvalues represent magnitude, or importance. Bigger eigenvalues correlate with more important directions.</p>

<p>Lots of variability usually indicates signal, whereas little variability usually indicates noise. Thus, the more variability there is in a particular direction is, theoretically, indicative of something important we want to detect.</p>

<h3>Assumptions and advantages of PCA</h3>
<p>
    
Assumptions:
- Linearity : PCA assumes that the principle components are a linear combination of the original features. If this is not true, PCA will not give you sensible results.
- Large variance implies more structure : PCA uses variance as the measure of how important a particular dimension is. So, high variance axes are treated as principle components, while low variance axes are treated as noise.
- Orthogonality : PCA assumes that the principle components are orthogonal.

PCA can be useful in exploring large data sets to see the structure of the relationships among variables when a correlation matrix would be overwhelming. Also, unlike correlation, it allows for relationships among sets of variables, rather than just pairs. Sometimes PCA doesn’t work. If the variables are all very uncorrelated, PCA may not be very useful.

Advantages:
    
- Lack of redundancy of data given the orthogonal components 
- Reduced complexity in images’ grouping with the use of PCA
- Smaller database representation since only the trainee images are stored in the form of their projections on a reduced basis
- Reduction of noise since the maximum variation basis is chosen and so the small variations in the back-ground are ignored automatically. It filters out the noise, and leaves us with stronger signal.
</p>

<h3> Data</h3>
<p>The dataset using for this analysis is directly imported from sklearn.datasets</p>

<h3>We cover the following techniques for implementing PCA</h3>
<ul>
    <li>Using Eigen decomposition </li>
    <li>Using scikit-learn</li>
    <li>Using Power Iteration algorithmn</li>
</ul>

<h3>Link to source code in Github</h3> 
<a href= "https://github.com/lakshmi2688/PCA_Images">Source code</a>
