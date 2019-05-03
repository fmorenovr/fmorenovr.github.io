---
layout: page
title: "Regularization"
subtitle: "Regularization algorithms for Models and algorithms"
description: "Regularization Algorithms"
permalink: /ml/regularization
---

# Overfitting/Underfitting Problems

* Underfitting: (high bias, {% raw %} $ L({\theta}) \gt \gt 0 $ {% endraw %}) Is when our loss function maps poorly to the trend of the data, this happens when the loss function is too simple or use too few features.

* Overfitting: (high variance, {% raw %} $ L({\theta}) \approx 0 $ {% endraw %}) Is whenloss function fits the available data but does not generalize well to predict data, this happens when the loss function is too complicate that creates a lot of unnecesary curves and angles.

Way to solve this problems:

* Reduce the number of features:

    * Select which features to keep
    
    * Use amodel selection algorithm

* Regularization

    * Keep all features but reduce the magnitude of parameters.

<p align="center">
  <img src="/assets/ml/regularization/over_under_fitting.png">
</p>

# Regularization

**Regularization** is the process to prevent overfitting in algorithms that try to minimize loss function (Like regressions).  

## Algorithms

There is 4 algorithms:

* Ridge Regression or called L2 regularization

  A standard linear or polynomial regression model will fail in the case where there is high collinearity (the existence of near-linear relationships among the independent variables) among the feature variables. Ridge Regression adds a small squared bias factor to the variables. Such a squared bias factor pulls the feature variable coefficients away from this rigidness, introducing a small amount of bias into the model but greatly reducing the variance.

* Least Absolute Shrinkage and Selection Operator (LASSO) or called L1 regularization

  In opposite to Ridge Regression it only penalizes high coefficients. Lasso has the effect of forcing some coefficient estimates to be exactly zero when hyper parameter θ is sufficiently large. LASSO works well for feature selection in case we have a huge number of features (it reduce redundant features and identify the important ones).

* Elastic Net

  Combines characteristics of both lasso and ridge. Elastic Net reduces the impact of different features while not eliminating all of the features. Lasso will eliminate many features, and reduce overfitting in your linear model. Ridge will reduce the impact of features that are not important in predicting your y values. Elastic Net combines feature elimination from Lasso and feature coefficient reduction from the Ridge model to improve your model’s predictions.

* Least Angle Regression (LARS)

## Equations

The Loss Function Regularizated equation is:

<p align="center">
{% raw %}
  $ L_{regularizated}(\hat{y}, y, \theta) = \dfrac{1}{n} [ L(\hat{y}, y)  + R(\theta)_{\lambda} ]$
{% endraw %}
</p>

<p align="center">
{% raw %}
  $ R(\theta)_\lambda = \lambda [\dfrac{(1-\alpha)}{2} \sum_{j=1}^{m} \theta_j ^2 + \alpha \sum_{j=1}^{m} | \theta_j |] $
{% endraw %}
</p>

With {% raw %} $ \theta = (\theta_1, \dots, \theta_m ) \in \mathbb{R}^{m}, \lambda \in \mathbb{R} $ {% endraw %} and {% raw %} $ \alpha \in [0, 1] $ {% endraw %}.

Where:
 * {% raw %} $ y $ {% endraw %} is the output given data.
 * {% raw %} $ \hat{y} $ {% endraw %} is the output predicted.
 * n is the data set size.
 * m is the number of features.
 * {% raw %} $ \theta $ {% endraw %} is the weights calculated for the regression.
 * {% raw %} $ \lambda $ {% endraw %} regularization parameter, where {% raw %} $ 0 \lt \lambda \lt \inf $ {% endraw %}.  
 * {% raw %} $ R_{\lambda} $ {% endraw %} regularization equation:  
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
