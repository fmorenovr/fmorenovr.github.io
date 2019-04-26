---
layout: page
title: "Regularization"
subtitle: "Regularization algorithms for Models and algorithms"
description: "Regularization Algorithms"
permalink: /ml/regularization
---

# Overfitting/Underfitting Problems

* Underfitting: (high bias, {% raw %} $ J({\theta}) \gt \gt 0 $ {% endraw %}) Is when our loss function maps poorly to the trend of the data, this happens when the loss function is too simple or use too few features.

* Overfitting: (high variance, {% raw %} $ J({\theta}) \approx 0 $ {% endraw %}) Is whenloss function fits the available data but does not generalize well to predict data, this happens when the loss function is too complicate that creates a lot of unnecesary curves and angles.

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
    
There is 4 algorithms:

* Ridge Regression or called L2 regularization

  A standard linear or polynomial regression model will fail in the case where there is high collinearity (the existence of near-linear relationships among the independent variables) among the feature variables. Ridge Regression adds a small squared bias factor to the variables. Such a squared bias factor pulls the feature variable coefficients away from this rigidness, introducing a small amount of bias into the model but greatly reducing the variance.

* Least Absolute Shrinkage and Selection Operator (LASSO) or called L1 regularization

  In opposite to Ridge Regression it only penalizes high coefficients. Lasso has the effect of forcing some coefficient estimates to be exactly zero when hyper parameter θ is sufficiently large. LASSO works well for feature selection in case we have a huge number of features (it reduce redundant features and identify the important ones).

* Elastic Net

  Combines characteristics of both lasso and ridge. Elastic Net reduces the impact of different features while not eliminating all of the features. Lasso will eliminate many features, and reduce overfitting in your linear model. Ridge will reduce the impact of features that are not important in predicting your y values. Elastic Net combines feature elimination from Lasso and feature coefficient reduction from the Ridge model to improve your model’s predictions.

* Least Angle Regression (LARS)

So, the equation in a regression problem with regularization is:

<p align="center">
{% raw %}
  $ J_{regularizated}(\theta) = \dfrac{1}{m} [ J(\theta)  + R_{\lambda} ]$
{% endraw %}
</p>

<p align="center">
{% raw %}
  $ R_\lambda = \sum_{j=0}^{n} [\dfrac{1}{2} \lambda_2 \theta_j ^2 + \lambda_1 \| \theta_j \|] $
{% endraw %}
</p>

But, taking {% raw %} $ \lambda = \dfrac{\lambda_1}{\lambda_1 + \lambda_2} $ {% endraw %}, we have:

<p align="center">
{% raw %}
  $ R_\lambda = \sum_{j=0}^{n} [\dfrac{1}{2} (1-\lambda) \theta_j ^2 + \lambda | \theta_j |] $
{% endraw %}
</p>

Where:
 * m is the data set size.
 * n is the number of features.
 * {% raw %} $ \theta $ {% endraw %} is the weights calculated for the regression.
 * {% raw %} $ \lambda_1 , \lambda_2 $ {% endraw %} regularization parameters, they could be {% raw %} $ 0 \lt \lambda_1 , \lambda_2 \lt \inf $ {% endraw %}.  
 * {% raw %} $ R_{\lambda} $ {% endraw %} regularization equation:  
    * If {% raw %} $ \lambda = 0 $ {% endraw %}, then we have Ridge Regression.
    * If {% raw %} $ \lambda = 1 $ {% endraw %}, then we have LASSO.
    * If {% raw %} $ 0 \lt \lambda \lt 1 $ {% endraw %}, then we have Elastic Net.
 
 
