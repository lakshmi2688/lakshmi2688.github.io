---
layout: post
title: "Multi Class Classification using Deep Learning"
date: 2022-12-05
---

<h3>Abstract</h3> 
<p>The goal of this analysis is to solve a multiclass classification problem by applying some of the concepts from Deep Learning and implement the same in Tensorflow.
<a name='5'></a>   
### 5 - Adam Optimizer

Adam is one of the most effective optimization algorithms for training neural networks. It combines ideas from RMSProp  and Momentum. 

**How does Adam work?**
1. It calculates an exponentially weighted average of past gradients, and stores it in variables $v$ (before bias correction) and $v^{corrected}$ (with bias correction). 
2. It calculates an exponentially weighted average of the squares of the past gradients, and  stores it in variables $s$ (before bias correction) and $s^{corrected}$ (with bias correction). 
3. It updates parameters in a direction based on combining information from "1" and "2".

The update rule is, for $l = 1, ..., L$: 

$$\begin{cases}
v_{dW^{[l]}} = \beta_1 v_{dW^{[l]}} + (1 - \beta_1) \frac{\partial \mathcal{J} }{ \partial W^{[l]} } \\
v^{corrected}_{dW^{[l]}} = \frac{v_{dW^{[l]}}}{1 - (\beta_1)^t} \\
s_{dW^{[l]}} = \beta_2 s_{dW^{[l]}} + (1 - \beta_2) (\frac{\partial \mathcal{J} }{\partial W^{[l]} })^2 \\
s^{corrected}_{dW^{[l]}} = \frac{s_{dW^{[l]}}}{1 - (\beta_2)^t} \\
W^{[l]} = W^{[l]} - \alpha \frac{v^{corrected}_{dW^{[l]}}}{\sqrt{s^{corrected}_{dW^{[l]}}} + \varepsilon}
\end{cases}$$
where:
- t counts the number of steps taken of Adam 
- L is the number of layers
- $\beta_1$ and $\beta_2$ are hyperparameters that control the two exponentially weighted averages. 
- $\alpha$ is the learning rate
- $\varepsilon$ is a very small number to avoid dividing by zero

Initialize the Adam variables $v, s$ which keep track of the past information.
The variables $v, s$ are python dictionaries that need to be initialized with arrays of zeros. Their keys are the same as for `grads`, that is:
for $l = 1, ..., L$:
```python
v["dW" + str(l)] = ... #(numpy array of zeros with the same shape as parameters["W" + str(l)])
v["db" + str(l)] = ... #(numpy array of zeros with the same shape as parameters["b" + str(l)])
s["dW" + str(l)] = ... #(numpy array of zeros with the same shape as parameters["W" + str(l)])
s["db" + str(l)] = ... #(numpy array of zeros with the same shape as parameters["b" + str(l)])

```

Implement the parameters update with Adam. Recall the general update rule is, for $l = 1, ..., L$: 

$$\begin{cases}
v_{dW^{[l]}} = \beta_1 v_{dW^{[l]}} + (1 - \beta_1) \frac{\partial \mathcal{J} }{ \partial W^{[l]} } \\
v^{corrected}_{dW^{[l]}} = \frac{v_{dW^{[l]}}}{1 - (\beta_1)^t} \\
s_{dW^{[l]}} = \beta_2 s_{dW^{[l]}} + (1 - \beta_2) (\frac{\partial \mathcal{J} }{\partial W^{[l]} })^2 \\
s^{corrected}_{dW^{[l]}} = \frac{s_{dW^{[l]}}}{1 - (\beta_2)^t} \\
W^{[l]} = W^{[l]} - \alpha \frac{v^{corrected}_{dW^{[l]}}}{\sqrt{s^{corrected}_{dW^{[l]}}} + \varepsilon}
\end{cases}$$

<p>
<ul>
   <li>Take the matrix of independent variables X and, for each column, subtract the mean of that column from each entry. This is demeaning and ensures that each column has a mean of zero. Demeaning data but not standardizing is equivalent to computing principal components from the covariance matrix of data. Here we assume all features are of the same scale. For our example, we calculate PCs from covariance matrix</li>

   <li>Decide whether or not to divide by sd. Given the columns of X, are features with higher variance more important than features with lower variance, or is the importance of features independent of the variance? (In this case, importance means how well that feature predicts Y). If the importance of features is independent of the variance of the features, then divide each observation in a column by that column’s standard deviation. Using standardized data is equivalent to computing principal components from the correlation matrix of data. If the features are of different scales, we use this approach</li>
</ul>
</p>

<p>First, the covariance matrix XᵀX is a matrix that contains estimates of how every variable in X relates to every other variable in X. Understanding how one variable is associated with another is quite powerful. Building the covariance matrix is the actual first step of PCA. In this step, we will be building a square dxd matrix where each row represents a feature and each column also represents a feature. Each entry represents the covariance between the row feature and the column feature at that position. Covariance tells us how the two features vary with respect to one another. If a given sample has a value above the mean (which we’ve set to zero through demean) for both features then we get a positive result as the product. The same is true if the values for both features are below the mean. Conversely, if one value is below and one is above we will get a negative value. If the covariance for a given pair of features is positive, both of these features tend to increase or decrease together. If the covariance is negative, one feature tends to increase as the other decreases. If the covariance is zero then the two features are unrelated. Correlation is defined as the covariance divided by the product of both standard deviations.</p>

<p>Second, eigenvalues and eigenvectors are important. Eigenvectors represent directions. Think of plotting your data on a multidimensional scatterplot. Then one can think of an individual eigenvector as a particular “direction” in your scatterplot of data. Eigenvalues represent magnitude, or importance. Bigger eigenvalues correlate with more important directions.</p>

<p>Lots of variability usually indicates signal, whereas little variability usually indicates noise. Thus, the more variability there is in a particular direction is, theoretically, indicative of something important we want to detect.</p>

<h2>Assumptions and advantages of PCA</h2>

<p>
<h3>Assumptions:</h3>
<ul>
<li> Linearity : PCA assumes that the principle components are a linear combination of the original features. If this is not true, PCA will not give you sensible results.</li>
<li> Large variance implies more structure : PCA uses variance as the measure of how important a particular dimension is. So, high variance axes are treated as principle components, while low variance axes are treated as noise.</li>
<li> Orthogonality : PCA assumes that the principle components are orthogonal.</li>
</ul>
</p>

<p>PCA can be useful in exploring large data sets to see the structure of the relationships among variables when a correlation matrix would be overwhelming. Also, unlike correlation, it allows for relationships among sets of variables, rather than just pairs. Sometimes PCA doesn’t work. If the variables are all very uncorrelated, PCA may not be very useful.</p>

<p>
<h3>Advantages:</h3>
<ul>    
<li> Lack of redundancy of data given the orthogonal components </li>
<li> Reduced complexity in images’ grouping with the use of PCA </li>
<li> Smaller database representation since only the trainee images are stored in the form of their projections on a reduced basis </li>
<li> Reduction of noise since the maximum variation basis is chosen and so the small variations in the back-ground are ignored automatically. It filters out the noise, and leaves us with stronger signal. </li>
</ul>
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
