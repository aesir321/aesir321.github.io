---
layout: post
title:  "Lasso regession for feature selection"
date:   2022-01-31 08:39:30 +0100
categories: data-science machine-learning
---
* What is this article about?
* What is Lasso regression?
* How does Lasso regression work?
* What can Lasso regression be used for?
* How to use Lasso regression
* How to interpret the results of Lasso regression?
* Sources
    - https://www.coursera.org/lecture/machine-learning-data-analysis/what-is-lasso-regression-0KIy7
    - https://towardsdatascience.com/ridge-and-lasso-regression-a-complete-guide-with-python-scikit-learn-e20e34bcbf0b
    - http://www.spectdata.com/index.php/2019/08/08/variable-selection-using-lasso/
    
* Add a theory and applied section

It is easier than ever today, especially for newcomers to the field, to skip or miss out on some of the more fundamental algorithms and jump straight to complex solutions that can be put together relatively easily by many of the machine learning frameworks around today such as TensorFlow or PyTorch.  There is nothing wrong with this in and of itself - everyone should follow their passion and there are definitely many areas where these solutions are excellent.  However, they are not simple and there is always a certain elegance in using a simple algorithm to solve a problem, that offers not only a solution to the problem but is also explainable and interpretable.  This article will cover how a variant of linear regression can be used to perform feature selection on big datasets and thus be used to provide insight into the driving parameters of your data science problem.

Least Absolute Shrinkage and Selection Operator Regression (Lasso Regression) is just a form of linear regression with a regularisation term added to the cost function using the $\ell^1$ norm.  The cost function is as shown below
$$
\begin{align}
J(\boldsymbol\theta) = \frac{1}{m}\sum^{m}_{i=1}\left(\boldsymbol\theta^{\intercal} \mathbf{x}^{(i)} - y^{(i)}\right) + \alpha\sum^{n}_{1=n}|\theta_i|
\end{align}
$$
where $J(\boldsymbol\theta)$ is our cost function parameterised by $\boldsymbol\theta$, $m$ is the number of samples, $\mathbf{x}$ is the vector of our predictions, $y$ is the ground truth, $\alpha$ determines the strength or weight of the regularisation applied and $|\theta_i|$ is the $\ell^1$ norm of the element of our model parameters.  Altogether you can see 
