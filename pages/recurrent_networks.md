---
layout: page
title: "Recurrent Neural Networks"
subtitle: "Recurrent Neural Networks algorithms"
description: "RNN Algorithms"
permalink: /ml/recurrent_networks
---

# Recurrent Neural Networks

Is a class of [ANN](/ml/neural_networks) where connections between nodes form a directed graph along a temporal sequence.  
RNNs can use their internal state (memory) to process sequences of inputs.

## Traditional Architecture

Recurrent neural networks, also known as RNNs, are a class of neural networks that allow previous outputs to be used as inputs while having hidden states. They are typically as follows:

<p align="center">
  <img src="/assets/ml/recurrent_networks/model.png">
</p>

## Architectures

There are different architectures to different applications:

| Architectures | Ilustration | Description
:-------------------------:|:-------------------------:
 One-to-One {% raw %} $ T_x = T_y = 1 $ {% endraw %} |  ![][o2o] | Traditional Neural Network
 One-to-Many {% raw %} $ T_x = 1, T_y \gt 1 $ {% endraw %} | ![][o2m] | An observation as input mapped to a sequence with multiple steps as an output.
 Many-to-One {% raw %} $ T_x \gt 1, T_y = 1 $ {% endraw %} | ![][m2o] | A sequence of multiple steps as input mapped to class or quantity prediction.
 Many-to-Many {% raw %} $ T_x = T_y $ {% endraw %} | ![][m2m_1] | A sequence of multiple steps as input mapped to a sequence with multiple steps as output.
 Many-to-Many {% raw %} $ T_x \neq T_y $ {% endraw %} | ![][m2m_2] | A sequence of multiple steps as input mapped to a sequence with multiple steps as output.

### Forward Propagation

<p align="center">
  <img src="/assets/ml/recurrent_networks/architecture.png">
</p>

For each timestep t, the activation {% raw %} $ a^{ \lt t \gt } $ {% endraw %} and the output {% raw %} $ y^{ \lt t \gt } $ {% endraw %} are expressed as follows:

<p align="center">
{% raw %}
  $
    a^{\lt t \gt} = g_1 (W_{aa} a^{ \lt t-1 \gt} + W_{ax} x^{ \lt t \gt } + b_a)
  $
  and 
  $ 
    \hat{y}^{\lt t \gt} = g_2 ( W_{ya} a^{\lt t \gt} + b_y)
  $
{% endraw %}
</p>

where {% raw %} $ W_{ax}, W_{aa}, W_{ya}, b_a, b_y $ {% endraw %} are coefficients that are shared temporally and {% raw %} $ g_1, g_2 $ {% endraw %} activation functions.

Where {% raw %} $ g_1 $ {% endraw %} usually is Tanh or ReLU and {% raw %} $ g_2 $ {% endraw %} usually is sigmoid or Softmax (depends of how variables you do like to identify).

### Loss Function

In the case of a recurrent neural network, the loss function L of all time steps is defined based on the loss at every time step as follows:

Lets write the error as {% raw %} $ E^{( t )} = L^{\lt t \gt} (\hat{y}^{\lt t \gt}, y^{\lt t \gt}) $ {% endraw %} and define the total Loss Function (or cost function or loss entropy) as:

<p align="center">
{% raw %}
  $
    L(\hat{y} , y) = \sum_{t=1}^{T_y} E^{( t )}
  $
{% endraw %}
</p>

### Back Propagation Through Time

Backpropagation is done at each point in time. At timestep T, the derivative of the loss L with respect to weight matrix W is expressed as follows:

<p align="center">
{% raw %}
  $
    \dfrac{\partial L^{(T)}}{\partial W} = \sum_{t=1}^{T} \dfrac{\partial E^{(T)}}{\partial W} |_{(t)}
  $ 
{% endraw %}
</p>

#### Gradient Calculation

By convention we take {% raw %} $ W_{ax} = U, W_{aa} = W, W_{ya} = V $ {% endraw %} such that the model looks like:

<p align="center">
  <img height="300" width="200" src="/assets/ml/recurrent_networks/new_model.png">
</p>

So equations above will be:

<p align="center">
{% raw %}
  $
    a^{\lt t \gt} = g_1 (W a^{ \lt t-1 \gt} + U x^{ \lt t \gt } + b_a)
  $
  and 
  $ 
    \hat{y}^{\lt t \gt} = g_2 ( V a^{\lt t \gt} + b_y)
  $
{% endraw %}
</p>

With {% raw %} $ x, y, \hat{y} \in \mathbb{R}^{n}, a \in \mathbb{R}^{m}, U \in \mathbb{R}^{mxn}, V \in \mathbb{R}^{nxm}, W \in \mathbb{R}^{mxm} $ {% endraw %}

Now, we need to obtain the gradient descent terms {% raw %} $ \dfrac{\partial L^{(T)}}{\partial U}, \dfrac{\partial L^{(T)}}{\partial W}, \dfrac{\partial L^{(T)}}{\partial V} $ {% endraw %}:

So, Lets call {% raw %} $ q^{ \lt t \gt } = V a^{\lt t \gt} + b_y  $ {% endraw %} and {% raw %} $ z^{ \lt t \gt } = W a^{ \lt t-1 \gt} + U x^{ \lt t \gt } + b_a  $ {% endraw %}, Then:

Taking some timestep **t** and L as softmax los function, in other words, {% raw %} $ L(\hat{y} , y) = - \dfrac{1}{n} \sum_{t=1}^{T_y} E^{( t )} $ {% endraw %} with {% raw %} $ E^{( t )} = - y^{\lt t \gt} log(\hat{y}^{\lt t \gt}) $ {% endraw %}

**I. V**

The matrix parameter V is only present in the function {% raw %} $ \hat{y}^{ \lt t \gt } $ {% endraw %} so we have:

<p align="center">
{% raw %}
  $
    \dfrac{\partial E^{(t)}}{\partial V} = \dfrac{\partial E^{(t)}}{\partial \hat{y}^{\lt t \gt}} \dfrac{\partial \hat{y}^{\lt t \gt}}{\partial q^{ \lt t \gt}} \dfrac{\partial q^{ \lt t \gt}}{\partial V}
  $ 
{% endraw %}
</p>

We know the softmax derivate (if you want to see step by step derivative process, press [here](/ml/softmax)) we have:

<p align="center">
{% raw %}
  $
    \dfrac{\partial E^{(t)}}{\partial \hat{y}^{\lt t \gt}} \dfrac{\partial \hat{y}^{\lt t \gt}}{\partial q^{ \lt t \gt}} = \dfrac{\partial E^{(t)}}{\partial q^{\lt t \gt}} = (\hat{y}^{\lt t \gt} - y^{\lt t \gt})
  $ 
{% endraw %}
</p>

<p align="center">
{% raw %}
  $
    \dfrac{\partial q^{ \lt t \gt}}{\partial V} = (a^{\lt t \gt})^T
  $ 
{% endraw %}
</p>

So, Finally:

<p align="center">
{% raw %}
  $
    \dfrac{\partial E^{(t)}}{\partial V} = (\hat{y}^{\lt t \gt} - y^{\lt t \gt}) (a^{\lt t \gt})^T
  $ 
{% endraw %}
</p>

**II. W**

The matrix parameter W appears in the argument for {% raw %} $ a^{\lt t \gt} $ {% endraw %} that depends on {% raw %} $ z^{\lt t \gt} $ {% endraw %}, now we define the chain rule as:

<p align="center">
{% raw %}
  $
    \dfrac{\partial E^{(t)}}{\partial W} = \dfrac{\partial E^{(t)}}{\partial \hat{y}^{\lt t \gt}} \dfrac{\partial \hat{y}^{\lt t \gt}}{\partial q^{ \lt t \gt}} \dfrac{\partial q^{\lt t \gt}}{\partial a^{ \lt t \gt}} \dfrac{\partial a^{ \lt t \gt}}{\partial W}
  $ 
{% endraw %}
</p>

We know the value for the three first partial derivates (see above).

<p align="center">
{% raw %}
  $
    \dfrac{\partial q^{\lt t \gt}}{\partial a^{ \lt t \gt}} = V
  $ 
{% endraw %}
</p>

So:

<p align="center">
{% raw %}
  $
    \dfrac{\partial E^{(t)}}{\partial W} = \dfrac{\partial E^{(t)}}{\partial q^{ \lt t \gt}} \dfrac{\partial q^{\lt t \gt}}{\partial a^{ \lt t \gt}} \dfrac{\partial a^{ \lt t \gt}}{\partial W} = (\hat{y}^{\lt t \gt} - y^{\lt t \gt}) . V . \dfrac{\partial a^{ \lt t \gt}}{\partial W}
  $ 
{% endraw %}
</p>

We need to analyze the term {% raw %} $ \dfrac{\partial a^{ \lt t \gt}}{\partial W} $ {% endraw %} and this term depends on all previously terms **a**.

We need to sum up the contributions of each time step to the gradient. In other words, because W is used in every step up to the output we care about, we need to backpropagate gradients from t through the network all the way to 0:

At the last layer we have:

<p align="center">
{% raw %}
  $
    \dfrac{\partial E^{(t)}}{\partial W} = \dfrac{\partial E^{(t)}}{\partial a^{\lt t \gt}} \dfrac{\partial a^{ \lt t \gt}}{\partial W} = \dfrac{\partial E^{(t)}}{\partial a^{\lt t \gt}} \dfrac{\partial a^{(t)}}{\partial a^{\lt t \gt}} \dfrac{\partial a^{ \lt t \gt}}{\partial W}
  $ 
{% endraw %}
</p>

At the penultimate layer:

<p align="center">
{% raw %}
  $
    \dfrac{\partial E^{(t)}}{\partial W} = \dfrac{\partial E^{(t)}}{\partial a^{\lt t-1 \gt}} \dfrac{\partial a^{ \lt t-1 \gt}}{\partial W} = \dfrac{\partial E^{(t)}}{\partial a^{\lt t \gt}} \dfrac{\partial a^{(t)}}{\partial a^{\lt t-1 \gt}} \dfrac{\partial a^{ \lt t-1 \gt}}{\partial W}
  $ 
{% endraw %}
</p>

At the t-n layer:

<p align="center">
{% raw %}
  $
    \dfrac{\partial E^{(t)}}{\partial W} = \dfrac{\partial E^{(t)}}{\partial a^{\lt t-n \gt}} \dfrac{\partial a^{ \lt t-n \gt}}{\partial W} = \dfrac{\partial E^{(t)}}{\partial a^{\lt t \gt}} \dfrac{\partial a^{(t)}}{\partial a^{\lt t-1 \gt}} \dfrac{\partial a^{ \lt t-1 \gt}}{\partial \partial a^{ \lt t-2 \gt}} ... \dfrac{\partial a^{ \lt t-n+1 \gt}}{\partial \partial a^{ \lt t-n \gt}} \dfrac{\partial a^{ \lt t-n \gt}}{\partial W}
  $ 
{% endraw %}
</p>

<p align="center">
{% raw %}
  $
    \dfrac{\partial E^{(t)}}{\partial W} = \dfrac{\partial E^{(t)}}{\partial a^{\lt t \gt}} \dfrac{\partial a^{(t)}}{\partial a^{\lt t-n \gt}} \dfrac{\partial a^{ \lt t-n \gt}}{\partial W}
  $ 
{% endraw %}
</p>

So, Sum all these terms to calculate the total from 0 to t:

<p align="center">
{% raw %}
  $
    \dfrac{\partial E^{ ( t )}}{\partial W} = \sum_{k=0}^{t} \dfrac{\partial E^{(t)}}{\partial a^{\lt t \gt}} \dfrac{\partial a^{ \lt t \gt}}{\partial a^{ \lt k \gt}}\dfrac{\partial a^{ \lt k \gt}}{\partial W}
  $ 
{% endraw %}
</p>

The Real equation:

<p align="center">
{% raw %}
  $
    \dfrac{\partial E^{ ( t )}}{\partial W} = \sum_{k=0}^{t} \dfrac{\partial E^{(t)}}{\partial \hat{y}^{\lt t \gt}} \dfrac{\partial \hat{y}^{\lt t \gt}}{\partial q^{ \lt t \gt}} \dfrac{\partial q^{\lt t \gt}}{\partial a^{ \lt t \gt}} \dfrac{\partial a^{ \lt t \gt}}{\partial a^{ \lt k \gt}}\dfrac{\partial a^{ \lt k \gt}}{\partial W}
  $ 
{% endraw %}
</p>

We deduce that:

<p align="center">
{% raw %}
  $
    \dfrac{\partial a^{ \lt t \gt}}{\partial W} = \sum_{k=0}^{t} \dfrac{\partial a^{ \lt t \gt}}{\partial a^{ \lt k \gt}}\dfrac{\partial a^{ \lt k \gt}}{\partial W}
  $ 
{% endraw %}
</p>

Is the same as:

<p align="center">
{% raw %}
  $
    \dfrac{\partial E^{(t)}}{\partial W} = (\hat{y}^{\lt t \gt} - y^{\lt t \gt}) . V . \sum_{k=0}^{t} \dfrac{\partial a^{ \lt t \gt}}{\partial a^{ \lt k \gt}}\dfrac{\partial a^{ \lt k \gt}}{\partial W}
  $ 
{% endraw %}
</p>


**II. U**

The matrix parameter U is similar to doing it for W since they appear in the ame euqation to calculate {% raw %} $ a^{\lt t \gt} $ {% endraw %}:

<p align="center">
{% raw %}
  $
    \dfrac{\partial E^{(t)}}{\partial U} = \dfrac{\partial E^{(t)}}{\partial \hat{y}^{\lt t \gt}} \dfrac{\partial \hat{y}^{\lt t \gt}}{\partial q^{ \lt t \gt}} \dfrac{\partial q^{\lt t \gt}}{\partial a^{ \lt t \gt}} \dfrac{\partial a^{ \lt t \gt}}{\partial U}
  $ 
{% endraw %}
</p>

So we have a very similar expression:

<p align="center">
{% raw %}
  $
    \dfrac{\partial E^{(t)}}{\partial U} = (\hat{y}^{\lt t \gt} - y^{\lt t \gt}) . V . \sum_{k=0}^{t} \dfrac{\partial a^{ \lt t \gt}}{\partial a^{ \lt k \gt}}\dfrac{\partial a^{ \lt k \gt}}{\partial U}
  $ 
{% endraw %}
</p>

### Vanishing/Exploding Gradient Problem

This occurs when we multiply a lot of times values close to zero or very high values.

Is generated by the chain rule:

<p align="center">
{% raw %}
  $
    \dfrac{\partial a^{ \lt t \gt}}{\partial a^{\lt k \gt}} = \dfrac{\partial a^{ \lt t \gt}}{\partial a^{\lt t-1 \gt}} \dfrac{\partial a^{ \lt t-1 \gt}}{\partial \partial a^{ \lt t-2 \gt}} ... \dfrac{\partial a^{ \lt k+2 \gt}}{\partial \partial a^{ \lt k+1 \gt}} \dfrac{\partial a^{ \lt k+1 \gt}}{\partial a^{ \lt k \gt}}
  $ 
{% endraw %}
</p>

<p align="center">
{% raw %}
  $
    \dfrac{\partial a^{ \lt t \gt}}{\partial a^{\lt k \gt}} = \prod_{i=k+1}^{t} \dfrac{\partial a^{\lt j \gt}}{\partial a^{\lt j-1 \gt}} 
  $ 
{% endraw %}
</p>

Solutions to avoid that are:

* Select good activation functions
* Initialize parameters as Identity matrix and bias equals to zero
* Use Gated Cells (LSTM/GRU).

## Summary

The pros and cons of a typical RNN architecture are summed up in the table below:

| Advantages | Drawbacks
:-------------------------:|:-------------------------:
 * Possibility of processing input of any length  |  * Computation being slow 
 * Model size not increasing with size of input | * Difficulty of accessing information from a long time ago
 * Computation takes into account historical information | Cannot consider any future input for the 
 * Weights are shared across time | 

## Applications

* Handwriting
* Speech Recognition
* Text Generation (Word Sequenece)
* Text to Speech
* Music Generation
* Sentiment Classification
* Name Entity Recognition
* Machine Translation



[o2o]:        /assets/ml/recurrent_networks/one-to-one.png
[o2m]:        /assets/ml/recurrent_networks/one-to-many.png
[m2o]:        /assets/ml/recurrent_networks/many-to-one.png
[m2m_1]:      /assets/ml/recurrent_networks/many-to-many-same.png
[m2m_2]:      /assets/ml/recurrent_networks/many-to-many-different.png
