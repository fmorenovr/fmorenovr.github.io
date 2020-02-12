---
layout: post
title: "Regularization"
subtitle: "Regularization algorithms for Models and algorithms"
description: "Regularization Algorithms"
date:   2019-05-18 12:15:12 -0500
permalink: /ml/regularization
---

# Overfitting/Underfitting Problems

When we are training a model, we could face to 2 scenarios:

* Underfitting: (high bias, {% raw %} $ L({\theta}) \gt \gt 0 $ {% endraw %}) Is when our loss function maps poorly to the trend of the data, this happens when the loss function is too simple or use too few features.

* Overfitting: (high variance, {% raw %} $ L({\theta}) \approx 0 $ {% endraw %}) Is whenloss function fits the available data but does not generalize well to predict data, this happens when the loss function is too complicate that creates a lot of unnecesary curves and angles.

<p align="center">
  <img src="/assets/ml/regularization/over_under_fitting.png">
</p>

Way to avoid this scenarios:

* Feature selection or model selection algorithm.

* Increase the sample size

* Regularization

# Regularization

**Regularization** is the process to prevent overfitting/underfitting by adding an additional penalty term in the error function.

## Techniques

### Early Stopping

Is a kind of cross-validation strategy. When we see that the performance on the validation set is getting worse, we immediately stop the training on the model.

<p align="center">
  <img src="/assets/ml/regularization/early_stopping.png" style="width:50%;height:50%;">
</p>

### LASSO (L1 regularizer)

Least Absolute Shrinkage and Selection Operator (LASSO) 

### Ridge (L2 regularizer)

### Elastic Net

* Least Angle Regression (LARS)

  Is a stylized version of the Stagewise procedure that uses a simple mathematical formula to accelerate the computations. so, LARS is a model selection method for linear regression (when you're worried about overfitting or want your model to be easily interpretable). To motivate it, let's consider some other model selection methods:
  
  * **Forward Selection** : starts with no variables in the model, and at each step it adds to the model the variable with the most explanatory power, stopping if the explanatory power falls below some threshold.
  
  * **Forward Stagewise Regression** : tries to remedy the greediness of forward selection by only partially adding variables. Whereas forward selection finds the variable with the most explanatory power and goes all out in adding it to the model, forward stagewise finds the variable with the most explanatory power and updates its weight by only epsilon in the correct direction. (So we might first increase the weight of peanut butter a little bit, then increase the weight of peanut butter again, then increase the weight of jelly, then increase the weight of bread, and then increase the weight of peanut butter once more.) The problem now is that we have to make a ton of updates, so forward stagewise can be very inefficient.

### Generalization 

We have a Cost function {% raw %} $ J(\theta) $ {% endraw %} (in this case is the Mean Square Error) defined by the average error across all samples between the prediction output {% raw %} $ \hat{y} = f(\theta , X) $ {% endraw %} and the expected output {% raw %} $ y ${% endraw %}. In general, if we take as loss function to _Least Square Error_ {%raw%} L(\hat{y}_i, y_i) {%endraw%}:

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

So, adding the regularizer function {%raw%} $ R(\theta) $ {%endraw%} to the Cost function defined above:

<p align="center">
{% raw %}
  $ L_{regularizated}(\theta) = \dfrac{1}{n} [ L(\theta)  + R(\theta)_{\lambda} ]$
{% endraw %}
</p>

<p align="center">
{% raw %}
  $ R(\theta)_\lambda = \lambda [\dfrac{(1-\alpha)}{2} \sum_{j=1}^{m} \theta_j ^2 + \alpha \sum_{j=1}^{m} | \theta_j |] $
{% endraw %}
</p>

Where:
 * {%raw%} $ f $ {%endraw%} is the estimator function.
 * {% raw %} $ X \in \mathbb{R}^{nxm} $ {% endraw %} is the data sample.
 * {% raw %} $ {x}^i $ {% endraw %} is one sample, {% raw %} $ x_j $ {% endraw %} is one feature and {% raw %} $ {x_j}^i $ {% endraw %} is the j-th feature in sample i.
 * {% raw %} $ \theta = (\theta_1, \dots, \theta_m ) \in \mathbb{R}^{m} $ {% endraw %} are the parameters.
 
 * {% raw %} $ y \in \mathbb{R}^{n} $ {% endraw %} is the given output data.
 * {% raw %} $ \hat{y} \in \mathbb{R}^{n} $ {% endraw %} is the predicted output.
 * {% raw %} $ n $ {% endraw %} is the sample size.
 * {% raw %} $ m $ {% endraw %} is the number of features.
 * {% raw %} $ \lambda \in \mathbb{R} $ {% endraw %} regularization parameter, where {% raw %} $ 0 \lt \lambda \lt \inf $ {% endraw %}.  
 * {% raw %} $ R_{\lambda} $ {% endraw %} regularization equation with {% raw %} $ \alpha \in [0, 1] $ {% endraw %}:
    * If {% raw %} $ \alpha = 0 $ {% endraw %}, then we have Ridge Regression.
    * If {% raw %} $ \alpha = 1 $ {% endraw %}, then we have LASSO.
    * If {% raw %} $ 0 \lt \alpha \lt 1 $ {% endraw %}, then we have Elastic Net.

### LARS

* **Algorithm**: The algorithm is very simple to understand:

  * **Forward Stagewise Regression**
  
    * Start Empty set {% raw %} $ \theta = 0 $ {% endraw %} of weigths.
    
    * Find the predictor feature {% raw %} $ x_j $ {% endraw %} most correlated with {% raw %} $ L(\hat{y} , y) $ {% endraw %}.
      
      We define {% raw %} $ c(\hat{y}) = (c_1, ..., c_m) $ {% endraw %} called the _vector of current correlations_ between feature {% raw %} $ x_j $ {% endraw %} and the predicted output {% raw %} $ \hat{y} $ {% endraw %} .  
      With and {% raw %} $ c_j = max(c_1, ..., c_m) $ {% endraw %} and {% raw %} $ c(\hat{y}) = \lt {X}^T, L(\hat{y} , y) \gt $ {% endraw %}
    
    * Take a small step ({% raw %} $ 0 \lt \epsilon \lt \| c_j \| $ {% endraw %}) or Large step ({% raw %} $ \epsilon = \| c_j \| $ {% endraw %}) in the direction of selected {% raw %} $ x_j $ {% endraw %}.
    
      So, taking {% raw %} $ \gamma_j = \epsilon . sign(c_j) $ {% endraw %}, we have {% raw %} $ \theta = \theta + \gamma_j . x_j $ {% endraw %} and {% raw %} $ \hat{y} = \hat{y} + J(\theta, X) $ {% endraw %}.
      
    * Increase {% raw %} $ \theta $ {% endraw %} in the direction of {% raw %} $ x_j $ {% endraw %} until another variable (feature) {% raw %} $ x_k $ {% endraw %} is equally correlated with residuals.
    
    * Choose equiangular/equicorrelation (bisect the angle between {% raw %} $ x_j $ {% endraw %} and {% raw %} $ x_k $ {% endraw %}) direction between {% raw %} $ x_j $ {% endraw %} and {% raw %} $ x_k $ {% endraw %}, and increase {% raw %} $ \theta $ {% endraw %} in that direction.

      Note: equiangular/equicorrelated means: {% raw %} $ c_j = c_k $ {% endraw %}.

      

      Where {% raw %} $ \gamma = $ {% endraw %}

    * Repeat until cover all predictors.


You can see this example below with m=3, and {% raw %} $ J(\theta , X) = \hat{u} = X \theta$ {% endraw %}:

* {% raw %} $ \hat{\mu_i} $ {% endraw %} are the current predicted output.

* {% raw %} $ \hat{y_i} $ {% endraw %} are the current proyection of the general predicted output {% raw %} $ \hat{y} $ {% endraw %} into {% raw %} $ L(x_1, ..., x_i) $ {% endraw %}.

* Start {% raw %} $ \theta = 0 \rightarrow  \hat{\mu_0} = 0 $ {% endraw %} and {% raw %} $ r = \hat{u_0} - y = \hat{y_1} $ {% endraw %}

* {% raw %} $ u_1 $ {% endraw %} is the unit vector of {% raw %} $\hat{y_1} $ {% endraw %}

* We calculate that {% raw %} $ c_1 = \lt X^T, r \gt $ {% endraw %} and {% raw %} $ \hat{\mu_1} = \hat{\mu_0} + \gamma_1 . u_1 $ {% endraw %}

  Where {% raw %} $ \gamma_1 $ {% endraw %} is chosen such that {% raw %} $ r = \hat{u_1} - y = \hat{y_2} $ {% endraw %} bisects the angle between {% raw %} $ x_1 $ {% endraw %} and {% raw %} $ x_2 $ {% endraw %}.

* Then stops the increasing of {% raw %} $ \hat{\mu_1} $ {% endraw %} when we notice that {% raw %} $ c_2 = \lt X^T, r \gt $ {% endraw %} is greater than {% raw %} $ c_1 $ {% endraw %}.

* Again, {% raw %} $ u_2 $ {% endraw %} is the unit vector of {% raw %} $\hat{y_2} $ {% endraw %}

* So we define {% raw %} $ \hat{\mu_2} = \hat{\mu_1} + \gamma_2 . u_2 $ {% endraw %} and so on until complete m features (in this case m=3 where {% raw %} $ \hat{\mu_3} = \hat{y} $ {% endraw %}).

<p align="center">
  <img src="/assets/ml/regularization/LARS.png">
</p>

 
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

## Gradient Descent Equiations

<p align="center">
{% raw %}
  $
  \theta_0 = \theta_0 - \alpha \dfrac{1}{n} [ \dfrac{\partial L}{\partial \theta_0} ]
  $
{% endraw %}
</p>
For j from 1 to n:

<p align="center">
{% raw %}
  $
  \theta_j = \theta_j - \alpha \dfrac{1}{n} [ \dfrac{\partial L}{\partial \theta_j} + \dfrac{\partial R_{\lambda}}{\partial \theta_j}]
  $
{% endraw %}
</p>

<p align="center">
{% raw %}
  $  \theta_j = \theta_j - \alpha \dfrac{1}{n} [ \dfrac{\partial L}{\partial \theta_j} + \lambda [(1-\alpha) \theta_j + \alpha \dfrac{\theta_j}{| \theta_j |} ] ] $
{% endraw %}
</p>


## References

* [LARS](https://web.stanford.edu/~hastie/Papers/LARS/LeastAngle_2002.pdf).

* [LARS definition](http://www.cis.hut.fi/Opinnot/T-61.6040/presentations_s06/LARS.pdf).

* [Linear Dependencies](https://www.researchgate.net/profile/Jaakko_Hollmen/publication/228752004_Learning_linear_dependency_trees_from_multivariate_time-series_data/links/0fcfd5089400ff2177000000/Learning-linear-dependency-trees-from-multivariate-time-series-data.pdf).

* [LARS analysis](https://arxiv.org/pdf/math/0406456.pdf).


