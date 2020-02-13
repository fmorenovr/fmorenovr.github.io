---
layout: post
title: "Regularization"
date:   2020-01-20 12:15:12 -0500

tags:
  - Machine Learning
  - Regularization
  - Regressions

categories:
  - ml
---

# Overfitting/Underfitting Problems

When we are performing a parameter estimator {%raw%} $ J(\theta) $ {%endraw%}, we could face to 2 scenarios:

<p align="center">
  <img src="/assets/ml/regularization/fit_model.png">
</p>

* Underfitting: (high bias, low variance, {% raw %} $ J({\theta}) \gt \gt 0 $ {% endraw %}).

* Overfitting: (low bias, high variance, {% raw %} $ J({\theta}) \approx 0 $ {% endraw %}).

<p align="center">
  <img src="/assets/ml/regularization/bias-variance-tradeoff.png">
</p>

Way to avoid this scenarios:

* Feature selection or model selection algorithm.

* Increase the sample size

* Regularization

# Regularization

**Regularization** is the process to prevent overfitting/underfitting by adding an additional penalty term in the error function.

## Definiton

Suppose we want to estimate the parameters {%raw%} $ \theta $ {%endraw%} which minimize a Cost function {% raw %} $ J(\theta) $ {% endraw %} defined by the sum of all error across all samples between the prediction output {% raw %} $ \hat{y} = f(\theta , X) $ {% endraw %} and the expected output {% raw %} $ y ${% endraw %}. Where {%raw%} $ \hat{y} $ {%endraw%} is the expected value of {%raw%} $ y $ {%endraw%} given {%raw%} $ y $ {%endraw%}. In other words, {%raw%} $ \hat{y} = \mathrm{E}[y\|\theta, X]$ {%endraw%}, the expected value of the error {%raw%} $ \mathrm{E}[\epsilon]=0$ {%endraw%}, has some variance {%raw%} $ \mathrm{Var}[\epsilon]=\sigma^2_{\epsilon}$ {%endraw%}.

#So, taking the Ordinary Least Square (OLS) error for each term we have:
So, getting the error for each term:

<p align="center">
{% raw %}
  $
  L(\hat{y}_i, y_i) = \hat{y}_i - y_i = \epsilon_i
  $
{% endraw %}
</p>

In general, the Cost function:

<p align="center">
{% raw %}
  $
  J(\theta) = \sum ^n _ {i=1} L(\hat{y}_i, y_i) = \epsilon
  $
{% endraw %}
</p>





(in this case is the Mean Square Error) defined by the average error 
 In general, if we take as loss function to _Least Square Error_ {%raw%} $ L(\hat{y}_i, y_i) $ {%endraw%}:

<p align="center">
{% raw %}
  $
  L(\hat{y}_i, y_i) = \dfrac{1}{2} (\hat{y}_i - y_i)^2
  $
{% endraw %}
</p>

Our Cost function (MSE) will be:

<p align="center">
{% raw %}
  $
  J(\theta) = \dfrac{1}{n} \sum ^n _ {i=1} L(\hat{y}_i, y_i)
  $
{% endraw %}
</p>

<p align="center">
{% raw %}
  $
  \hat{\theta} = argmin J() \hat{y} - y
  $
{% endraw %}
</p>

### Ridge (L2 regularizer)



### LASSO (L1 regularizer)

Least Absolute Shrinkage and Selection Operator (LASSO) is quite similar conceptually to ridge regression. It also adds a penalty for non-zero coefficients. As a result, for high values of {%raw%} $ \lambda $ {%endraw%}, many coefficients are exactly zeroed under lasso, which is never the case in ridge regression.


### Elastic Net

### Generalization 

Be the norm-p defined as:

<p align="center">
{% raw %}
  $ || \theta ||_p = \sqrt{\sum^m _{j=1} | \theta_i |^p} $
{% endraw %}
</p>

So, adding the regularizer function {%raw%} $ R(\theta) $ {%endraw%} to the Cost function defined above:

<p align="center">
{% raw %}
  $ J(\theta) = \dfrac{1}{n} [ \sum ^n _ {i=1} L(\hat{y}_i, y_i) + R(\theta)_{\lambda,\alpha} ] $
{% endraw %}
</p>

<p align="center">
{% raw %}
  $ R(\theta)_{\lambda,\alpha} = \lambda [ \dfrac{(1-\alpha)}{2} || \theta ||_2 + \alpha || \theta ||_1 ] $
{% endraw %}
</p>

Where:
 * {%raw%} $ f $ {%endraw%} is the estimator function.
 * {% raw %} $ X \in \mathbb{R}^{nxm} , y \in \mathbb{R}^{n} $ {% endraw %} is the data sample.
 * {% raw %} $ {x}^i $ {% endraw %} is one sample, {% raw %} $ x_j $ {% endraw %} is one feature and {% raw %} $ {x_j}^i $ {% endraw %} is the j-th feature in sample i.
 * {% raw %} $ \theta = (\theta_1, \dots, \theta_m ) \in \mathbb{R}^{m} $ {% endraw %} are the parameters.
 * {% raw %} $ \hat{y} \in \mathbb{R}^{n} $ {% endraw %} is the predicted output.
 * {% raw %} $ n $ {% endraw %} is the sample size.
 * {% raw %} $ m $ {% endraw %} is the number of features.
 * {% raw %} $ \lambda \in \mathbb{R} $ {% endraw %} regularization parameter, where {% raw %} $ 0 \lt \lambda \lt \inf $ {% endraw %}.  
 * {% raw %} $ R_{\lambda} $ {% endraw %} regularization equation with {% raw %} $ \alpha \in [0, 1] $ {% endraw %}:
    * If {% raw %} $ \alpha = 0 $ {% endraw %}, then we have Ridge Regression.
    * If {% raw %} $ \alpha = 1 $ {% endraw %}, then we have LASSO.
    * If {% raw %} $ 0 \lt \alpha \lt 1 $ {% endraw %}, then we have Elastic Net.

## Normal Equation

If m > n:

<p align="center">
{% raw %}
  $ \theta = (X^T X + \lambda R) X^T y $
{% endraw %}
</p>

Else is Non-invertible. Also, R is:

<p align="center">
{% raw %}
  $
  R = \begin{bmatrix}
    0  & 0 & 0 & \dots & 0 \\
    0  & 1 & 0 & \dots & 0 \\
    0  & 0 & 1 & \dots & 0 \\
    \vdots & & \ddots & & \vdots\\
    0  & 0 & 0 & \dots & 1
    \end{bmatrix}
  $
{% endraw %}
</p>

With:

<p align="center">
{% raw %}
  $
  R \in \mathbb{R}^{(n+1)x(n+1)}
  $
{% endraw %}
</p>

## References

* [LARS](https://web.stanford.edu/~hastie/Papers/LARS/LeastAngle_2002.pdf).

* [LARS definition](http://www.cis.hut.fi/Opinnot/T-61.6040/presentations_s06/LARS.pdf).

* [Linear Dependencies](https://www.researchgate.net/profile/Jaakko_Hollmen/publication/228752004_Learning_linear_dependency_trees_from_multivariate_time-series_data/links/0fcfd5089400ff2177000000/Learning-linear-dependency-trees-from-multivariate-time-series-data.pdf).

* [LARS analysis](https://arxiv.org/pdf/math/0406456.pdf).


