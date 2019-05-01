---
layout: page
title: "Recurrent Neural Networks"
subtitle: "Recurrent Neural Networks algorithms"
description: "RNN Algorithms"
permalink: /ml/recurrent_networks
---

# Recurrent Neural Networks

<p align="center">
  <img src="/assets/ml/regularization/over_under_fitting.png">
</p>


## Gradient Descent Equiations

<p align="center">
{% raw %}
  $
  \theta_0 = \theta_0 - \alpha \dfrac{1}{m} [ \dfrac{\partial J(\theta)}{\partial \theta_0} ]
  $
{% endraw %}
</p>

for j from 1 to n:

<p align="center">
{% raw %}
  $
  \theta_j = \theta_j - \alpha \dfrac{1}{m} [ \dfrac{\partial J(\theta)}{\partial \theta_j} + \dfrac{\partial R_{\lambda}}{\partial \theta_j}]
  $
{% endraw %}
</p>

<p align="center">
{% raw %}
  $  \theta_j = \theta_j - \alpha \dfrac{1}{m} [ \dfrac{\partial J(\theta)}{\partial \theta_j} + (1-\lambda) \theta_j + \lambda \dfrac{\theta_j}{| \theta_j |} ] $
{% endraw %}
</p>
