---
layout: post
title: "Multi Class Classification using Deep Learning"
date: 2022-12-05
---

<h3>Abstract</h3> 
<p>The goal of this analysis is to solve a multiclass classification problem by applying some of the concepts from Deep Learning and implement the same in Tensorflow.
<a name='2'></a>
### 1 - (Batch) Gradient Descent

A simple optimization method in machine learning is gradient descent (GD). When you take gradient steps with respect to all $m$ examples on each step, it is also called Batch Gradient Descent. 
The  gradient descent rule is, for $l = 1, ..., L$: 
$$ W^{[l]} = W^{[l]} - \alpha \text{ } dW^{[l]} \tag{1}$$
$$ b^{[l]} = b^{[l]} - \alpha \text{ } db^{[l]} \tag{2}$$

where L is the number of layers and $\alpha$ is the learning rate. 


``` python
X = data_input
Y = labels
m = X.shape[1]  # Number of training examples
parameters = initialize_parameters(layers_dims)
for i in range(0, num_iterations):
    # Forward propagation
    a, caches = forward_propagation(X, parameters)
    # Compute cost
    cost_total = compute_cost(a, Y)  # Cost for m training examples
    # Backward propagation
    grads = backward_propagation(a, caches, parameters)
    # Update parameters
    parameters = update_parameters(parameters, grads)
    # Compute average cost
    cost_avg = cost_total / m
        
```

### 2 -  Stocastic Gradient Descent

A variant of Gardient Descent is Stochastic Gradient Descent (SGD), which is equivalent to mini-batch gradient descent, where each mini-batch has just 1 example. What changes is that you would be computing gradients on just one training example at a time, rather than on the whole training set. The code examples below illustrate the difference between stochastic gradient descent and (batch) gradient descent. 

```python
X = data_input
Y = labels
m = X.shape[1]  # Number of training examples
parameters = initialize_parameters(layers_dims)
for i in range(0, num_iterations):
    cost_total = 0
    for j in range(0, m):
        # Forward propagation
        a, caches = forward_propagation(X[:,j], parameters)
        # Compute cost
        cost_total += compute_cost(a, Y[:,j])  # Cost for one training example
        # Backward propagation
        grads = backward_propagation(a, caches, parameters)
        # Update parameters
        parameters = update_parameters(parameters, grads)
    # Compute average cost
    cost_avg = cost_total / m
```


In Stochastic Gradient Descent, you use only 1 training example before updating the gradients. When the training set is large, SGD can be faster. But the parameters will "oscillate" toward the minimum rather than converge smoothly. Here's what that looks like: 

<img src="/assets/images/kiank_sgd.png" style="width:750px;height:250px;">
<caption><center> <u> <font color='purple'> <b>Figure 1</b> </u><font color='purple'>  : <b>SGD vs GD</b><br> "+" denotes a minimum of the cost. SGD leads to many oscillations to reach convergence, but each step is a lot faster to compute for SGD than it is for GD, as it uses only one training example (vs. the whole batch for GD). </center></caption>

Implementing SGD requires 3 for-loops in total:
1. Over the number of iterations
2. Over the $m$ training examples
3. Over the layers (to update all parameters, from $(W^{[1]},b^{[1]})$ to $(W^{[L]},b^{[L]})$)

In practice, you'll often get faster results if you don't use the entire training set, or just one training example, to perform each update. 
    
<a name='3'></a>
### 3 - Mini-Batch Gradient Descent

Mini-batch gradient descent uses an intermediate number of examples for each step. With mini-batch gradient descent, you loop over the mini-batches instead of looping over individual training examples.
    
```python
X = data_input
Y = labels
m = X.shape[1]  # Number of training examples
parameters = initialize_parameters(layers_dims)
for i in range(0, num_epochs):
    #generate mini batches by shuffling and partitioning
    minibatches = random_mini_batches(X, Y, mini_batch_size)
    for minibatch in minibatches:
        #get x and y component of each minibatch
        (mini_X, mini_Y) = minibatch
        # Forward propagation
        a, caches = forward_propagation(mini_X, parameters)
        # Compute cost
        cost_total += compute_cost(a, mini_Y)  # Cost for one training example
        # Backward propagation
        grads = backward_propagation(a, mini_Y, caches)
        # Update parameters
        parameters = update_parameters(parameters, grads, learning_rate)
    # Compute average cost
    cost_avg = cost_total / m
```

<img src="images/kiank_minibatch.png" style="width:750px;height:250px;">
<caption><center> <u> <font color='purple'> <b>Figure 2</b> </u>: <font color='purple'>  <b>SGD vs Mini-Batch GD</b><br> "+" denotes a minimum of the cost. Using mini-batches in your optimization algorithm often leads to faster optimization. </center></caption>

There are two steps:
- **Shuffle**: Create a shuffled version of the training set (X, Y) as shown below. Each column of X and Y represents a training example. Note that the random shuffling is done synchronously between X and Y. Such that after the shuffling the $i^{th}$ column of X is the example corresponding to the $i^{th}$ label in Y. The shuffling step ensures that examples will be split randomly into different mini-batches. 

<img src="images/kiank_shuffle.png" style="width:550px;height:300px;">

- **Partition**: Partition the shuffled (X, Y) into mini-batches of size `mini_batch_size` (here 64). Note that the number of training examples is not always divisible by `mini_batch_size`. The last mini batch might be smaller. When the final mini-batch is smaller than the full `mini_batch_size`, it will look like this: 

<img src="images/kiank_partition.png" style="width:550px;height:300px;">

<a name='ex-2'></a>

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
