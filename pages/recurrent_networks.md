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

Where {% raw %} $ W_{ax}, W_{aa}, W_{ya}, b_a, b_y $ {% endraw %} are coefficients that are shared temporally and {% raw %} $ g_1, g_2 $ {% endraw %} activation functions. Where {% raw %} $ g_1 $ {% endraw %} usually is **Tanh or ReLU** and {% raw %} $ g_2 $ {% endraw %} usually is **sigmoid or Softmax** (depends of how variables you do like to identify).

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

### Back Propagation Through Time (BPTT)

Backpropagation is done at each point in time. By convention we take {% raw %} $ W_{ax} = U, W_{aa} = W, W_{ya} = V $ {% endraw %}, such that the model looks like:

<p align="center">
  <img height="300" width="200" src="/assets/ml/recurrent_networks/new_model.png">
</p>

So equations above will be:

<p align="center">
{% raw %}
  $
    a^{\lt t \gt} = g_1 (W a^{ \lt t-1 \gt} + U x^{ \lt t \gt } + b_a)
  $
{% endraw %}
</p>

<p align="center">
{% raw %}
  $
    \hat{y}^{\lt t \gt} = g_2 ( V a^{\lt t \gt} + b_y)
  $
{% endraw %}
</p>

Lets call {% raw %} $ q^{ \lt t \gt } = V a^{\lt t \gt} + b_y  $ {% endraw %} and {% raw %} $ z^{ \lt t \gt } = W a^{ \lt t-1 \gt} + U x^{ \lt t \gt } + b_a  $ {% endraw %}, Then:

<p align="center">
{% raw %}
  $
    a^{\lt t \gt} = g_1 (z^{ \lt t \gt})
  $
{% endraw %}
</p>

<p align="center">
{% raw %}
  $
    \hat{y}^{\lt t \gt} = g_2 (q^{ \lt t \gt})
  $
{% endraw %}
</p>

With {% raw %} $ x \in \mathbb{R}^{n}, y, \hat{y}, b_y \in \mathbb{R}^{m}, a, b_a \in \mathbb{R}^{h}, U \in \mathbb{R}^{hxn}, W \in \mathbb{R}^{hxh}, V \in \mathbb{R}^{mxh} $ {% endraw %}. Now, we need to obtain the gradient descent terms at last timestep {% raw %} $ T_y $ {% endraw %}: {% raw %} $ \dfrac{\partial L}{\partial U}, \dfrac{\partial L}{\partial W}, \dfrac{\partial L}{\partial V} $ {% endraw %}.

At timestep T, the derivative of the loss L with respect to some weight matrix M is expressed as follows:

<p align="center">
{% raw %}
  $
    \dfrac{\partial L^{(T)}}{\partial M} = \sum_{t=1}^{T} \dfrac{\partial E^{(T)}}{\partial M} |_{(t)}
  $ 
{% endraw %}
</p>

If we analyse {% raw %} $ T = T_y $ {% endraw %}, we can rewrite as (using U, W, V):

<p align="center">
{% raw %}
  $
    \dfrac{\partial L}{\partial U} = \sum_{t=1}^{T_y} \dfrac{\partial E^{(t)}}{\partial U} |_{(t)}
  $ 
{% endraw %}
</p>

<p align="center">
{% raw %}
  $
    \dfrac{\partial L}{\partial W} = \sum_{t=1}^{T_y} \dfrac{\partial E^{(t)}}{\partial W} |_{(t)}
  $ 
{% endraw %}
</p>

<p align="center">
{% raw %}
  $
    \dfrac{\partial L}{\partial V} = \sum_{t=1}^{T_y} \dfrac{\partial E^{(t)}}{\partial V} |_{(t)}
  $ 
{% endraw %}
</p>

By convention, you could call {% raw %} $ \theta = \[ U W  V^T \] $ {% endraw %} to join all three matrix U, W, V in one matrix parameter and {% raw %} $ \theta \in \mathbb{R}^{(m)x(2n+m)} $ {% endraw %} and analyse with that parameter, but it could be more complicate.

So, the derivative of the loss L with respect to weight matrix {% raw %} $ \theta $ {% endraw %} is expressed as follows:

<p align="center">
{% raw %}
  $
    \dfrac{\partial L}{\partial \theta} = \sum_{t=1}^{T_y} \dfrac{\partial E^{(t)}}{\partial \theta} |_{(t)}
  $ 
{% endraw %}
</p>

#### Gradient Calculation

Taking some timestep **t** and L as softmax los function, in other words, {% raw %} $ L(\hat{y} , y) = - \dfrac{1}{N} \sum_{t=1}^{T_y} E^{( t )} $ {% endraw %} (N is the number of data samples) with {% raw %} $ E^{( t )} = - y^{\lt t \gt} log(\hat{y}^{\lt t \gt}) $ {% endraw %}.

**I. V**

The matrix parameter V is only present in the function {% raw %} $ \hat{y}^{ \lt t \gt } $ {% endraw %} so we have:

<p align="center">
{% raw %}
  $
    \dfrac{\partial E^{(t)}}{\partial V} = \dfrac{\partial E^{(t)}}{\partial \hat{y}^{\lt t \gt}} \dfrac{\partial \hat{y}^{\lt t \gt}}{\partial q^{ \lt t \gt}} \dfrac{\partial q^{ \lt t \gt}}{\partial V}
  $ 
{% endraw %}
</p>

We know the softmax derivate (if you want to see step by step derivative process, press [here](/ml/activation_functions)) we have:

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
    \dfrac{\partial E^{(t)}}{\partial V} = (\hat{y}^{\lt t \gt} - y^{\lt t \gt}) . (a^{\lt t \gt})^T
  $ 
{% endraw %}
</p>

**II. W**

The matrix parameter W appears in the argument for {% raw %} $ a^{\lt t \gt} $ {% endraw %} that depends on {% raw %} $ z^{\lt t \gt} $ {% endraw %}, now we define the chain rule as:

<p align="center">
{% raw %}
  $
    \dfrac{\partial E^{(t)}}{\partial W} = \dfrac{\partial E^{(t)}}{\partial \hat{y}^{\lt t \gt}} \dfrac{\partial \hat{y}^{\lt t \gt}}{\partial q^{ \lt t \gt}} \dfrac{\partial q^{\lt t \gt}}{\partial a^{ \lt t \gt}} \dfrac{\partial a^{ \lt t \gt}}{\partial z^{ \lt t \gt}} \dfrac{\partial z^{ \lt t \gt}}{\partial W}
  $ 
{% endraw %}
</p>

Is the same as:

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

At the (t-n) layer, we need:

<p align="center">
{% raw %}
  $
    \dfrac{\partial E^{(t)}}{\partial W} = \dfrac{\partial E^{(t)}}{\partial a^{\lt t-n \gt}} \dfrac{\partial a^{ \lt t-n \gt}}{\partial W}
  $ 
{% endraw %}
</p>

Chain rule:

<p align="center">
{% raw %}
  $
    \dfrac{\partial E^{(t)}}{\partial W} = \dfrac{\partial E^{(t)}}{\partial a^{\lt t \gt}} \dfrac{\partial a^{(t)}}{\partial a^{\lt t-1 \gt}} \dfrac{\partial a^{ \lt t-1 \gt}}{\partial a^{ \lt t-2 \gt}} ... \dfrac{\partial a^{ \lt t-n+1 \gt}}{\partial a^{ \lt t-n \gt}} \dfrac{\partial a^{ \lt t-n \gt}}{\partial W}
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

**Resume of Gradient Equations**

Total Loss Function:

<p align="center">
{% raw %}
  $
    L(\hat{y} , y) = \sum_{t=1}^{T_y} E^{( t )}
  $
{% endraw %}
</p>

The Partial derivate of Loss function is the sum of all partial derivate in each step time **t**. Replacing (using equations for each matrix above) we obtain:

U:

<p align="center">
{% raw %}
  $
    \dfrac{\partial L}{\partial U} = \sum_{t=1}^{T_y} \dfrac{\partial E^{(t)}}{\partial U} |_{(t)}
  $ 
{% endraw %}
</p>

<p align="center">
{% raw %}
  $
    \dfrac{\partial L}{\partial U} = \sum_{t=1}^{T_y} \dfrac{\partial E^{(t)}}{\partial \hat{y}^{\lt t \gt}} \dfrac{\partial \hat{y}^{\lt t \gt}}{\partial q^{ \lt t \gt}} \dfrac{\partial q^{\lt t \gt}}{\partial a^{ \lt t \gt}} \dfrac{\partial a^{ \lt t \gt}}{\partial U}
  $ 
{% endraw %}
</p>

<p align="center">
{% raw %}
  $
    \dfrac{\partial L}{\partial U} = \sum_{t=1}^{T_y} [ (\hat{y}^{\lt t \gt} - y^{\lt t \gt}) . V . \sum_{k=0}^{t} \dfrac{\partial a^{ \lt t \gt}}{\partial a^{ \lt k \gt}}\dfrac{\partial a^{ \lt k \gt}}{\partial U} ]
  $ 
{% endraw %}
</p>

W:

<p align="center">
{% raw %}
  $
    \dfrac{\partial L}{\partial W} = \sum_{t=1}^{T_y} \dfrac{\partial E^{(t)}}{\partial W} |_{(t)}
  $ 
{% endraw %}
</p>

<p align="center">
{% raw %}
  $
    \dfrac{\partial L}{\partial W} = \sum_{t=1}^{T_y} \dfrac{\partial E^{(t)}}{\partial \hat{y}^{\lt t \gt}} \dfrac{\partial \hat{y}^{\lt t \gt}}{\partial q^{ \lt t \gt}} \dfrac{\partial q^{\lt t \gt}}{\partial a^{ \lt t \gt}} \dfrac{\partial a^{ \lt t \gt}}{\partial W}
  $ 
{% endraw %}
</p>

<p align="center">
{% raw %}
  $
    \dfrac{\partial L}{\partial W} = \sum_{t=1}^{T_y} [ (\hat{y}^{\lt t \gt} - y^{\lt t \gt}) . V . \sum_{k=0}^{t} \dfrac{\partial a^{ \lt t \gt}}{\partial a^{ \lt k \gt}}\dfrac{\partial a^{ \lt k \gt}}{\partial W} ]
  $ 
{% endraw %}
</p>

V:

<p align="center">
{% raw %}
  $
    \dfrac{\partial L}{\partial V} = \sum_{t=1}^{T_y} \dfrac{\partial E^{(t)}}{\partial V} |_{(t)}
  $ 
{% endraw %}
</p>

<p align="center">
{% raw %}
  $
    \dfrac{\partial L}{\partial V} = \sum_{t=1}^{T_y} \dfrac{\partial E^{(t)}}{\partial \hat{y}^{\lt t \gt}} \dfrac{\partial \hat{y}^{\lt t \gt}}{\partial q^{ \lt t \gt}} \dfrac{\partial q^{ \lt t \gt}}{\partial V}
  $ 
{% endraw %}
</p>

<p align="center">
{% raw %}
  $
    \dfrac{\partial L}{\partial V} = \sum_{t=1}^{T_y} [ (\hat{y}^{\lt t \gt} - y^{\lt t \gt}) . (a^{\lt t \gt})^T ]
  $ 
{% endraw %}
</p>

### Vanishing/Exploding Gradient Problem

The vanishing and exploding gradient phenomena are often encountered in the context of RNNs. The reason why they happen is that it is difficult to capture long term dependencies because of multiplicative gradient that can be exponentially decreasing/increasing with respect to the number of layers.

Is generated by the chain rule:

<p align="center">
{% raw %}
  $
    \dfrac{\partial a^{ \lt t \gt}}{\partial a^{\lt k \gt}} = \dfrac{\partial a^{ \lt t \gt}}{\partial a^{\lt t-1 \gt}} \dfrac{\partial a^{ \lt t-1 \gt}}{\partial a^{ \lt t-2 \gt}} ... \dfrac{\partial a^{ \lt k+2 \gt}}{\partial a^{ \lt k+1 \gt}} \dfrac{\partial a^{ \lt k+1 \gt}}{\partial a^{ \lt k \gt}}
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

##### Type of Gates

  In order to remedy the vanishing gradient problem, specific gates are used in some types of RNNs and usually have a well-defined purpose. They are usually noted {% raw %} $ \Gamma $ {% endraw %} and are equal to:

<p align="center">
{% raw %}
  $
    \Gamma = \sigma (W a^{ \lt t-1 \gt} + U x^{ \lt t \gt } + b)
  $
{% endraw %}
</p>

where 
W, U, b are coefficients specific to the gate and {% raw %} $ \sigma $ {% endraw %} is the sigmoid function. The main ones are summed up in the table below:

| Type of Gate | Role | Used in 
:-------------------------:|:-------------------------:
 Candidate Gate {% raw %} $ c^{\lt t \gt} $ {% endraw %} | How much past should matter now? | GRU/LSTM
  Input Gate {% raw %} $ i^{\lt t \gt} $ {% endraw %} | Drop previous information? | GRU/LSTM
  Forget Gate {% raw %} $ f^{\lt t \gt} $ {% endraw %} | Erase a cell or not? | LSTM
  Output Gate {% raw %} $ o^{\lt t \gt} $ {% endraw %} | How much to reveal of a cell? | LSTM

Gated Recurrent Unit (GRU) and Long Short-Term Memory units (LSTM) deal with the vanishing gradient problem encountered by traditional RNNs, with LSTM being a generalization of GRU. Below is a table summing up the characterizing equations of each architecture:


#### Long Short Term Memory (LSTM)

The architecture is as follows:

<p align="center">
  <img height="300" width="200" src="/assets/ml/recurrent_networks/lstm.png">
</p>

With equations like:

**Forget Gate**

<p align="center">
{% raw %}
  $
    f^{\lt t \gt} = g_1 (W_f a^{ \lt t-1 \gt} + U_f x^{ \lt t \gt } + b_f)
  $
{% endraw %}
</p>

* Use previous cell output and input.
* Decide what to forget: in Sigmoid case: value 0 and 1 – "completely forget" vs. "completely keep"

**Input Gate**

<p align="center">
{% raw %}
  $
    i^{\lt t \gt} = g_2 (W_i a^{ \lt t-1 \gt} + U_i x^{ \lt t \gt } + b_i)
  $
{% endraw %}
</p>

* Input: Decide what values to update.

**Update Gate**

**1. Candidate Gate**

<p align="center">
{% raw %}
  $
    g^{\lt t \gt} = g_3 (W_c a^{ \lt t-1 \gt} + U_c x^{ \lt t \gt } + b_c)
  $
{% endraw %}
</p>

* Candidate: Generate new vector of "candidate values" that could be added to the state.

**2. Memory State**

<p align="center">
{% raw %}
  $
    c^{\lt t \gt} = f^{\lt t \gt} . (c^{\lt t-1 \gt})^T + i^{\lt t \gt} . (g^{\lt t \gt})^T
  $
{% endraw %}
</p>

* Apply forget operation to previous internal cell state: {% raw %} $ f^{\lt t \gt} . (c^{\lt t-1 \gt})^T $ {% endraw %}.

* Add new candidate values, scaled by how much we decided to update: {% raw %} $ i^{\lt t \gt} . (g^{\lt t \gt})^T $ {% endraw %}.

**Output Gate**

<p align="center">
{% raw %}
  $
    o^{\lt t \gt} = g_4 (W_o a^{ \lt t-1 \gt} + U_o x^{ \lt t \gt } + b_o)
  $
{% endraw %}
</p>

* Output: Decide what parts of state to output.

**Hidden State**

<p align="center">
{% raw %}
  $
    a^{\lt t \gt} = o^{\lt t \gt} . (g_5(c^{\lt t \gt}))^T
  $
{% endraw %}
</p>

* Output filtered version of cell state: {% raw %} $ o^{\lt t \gt} . (g_5(c^{\lt t \gt}))^T $ {% endraw %}

**Output**

<p align="center">
{% raw %}
  $
    \hat{y}^{\lt t \gt} = g_6( V a^{\lt t \gt}  + b_y)
  $
{% endraw %}
</p>

With {% raw %} $ x \in \mathbb{R}^{n}; y, \hat{y}, b_y \in \mathbb{R}^{m}; a, g, f, i, o, c, b_{f,i,o,c} \in \mathbb{R}^{h}; U_{f,i,o,c} \in \mathbb{R}^{hxn}; W_{f,i,o,c} \in \mathbb{R}^{hxh}; V \in \mathbb{R}^{mxh} $ {% endraw %}. Now, we need to obtain the gradient descent terms at last timestep {% raw %} $ T_y $ {% endraw %}: {% raw %} $ \dfrac{\partial L}{\partial U_{f,i,o,c}}, \dfrac{\partial L}{\partial W_{f,i,o,c}}, \dfrac{\partial L}{\partial V} $ {% endraw %}.

Where {% raw %} $ W_{f,i,o,c}, b_{f,i,o,c} $ {% endraw %} are coefficients that are shared temporally and {% raw %} $ g_1, g_2, g_3, g_4, g_5 $ {% endraw %} activation functions. Where {% raw %} $ g_1, g_2, g_3 $ {% endraw %} usually is **sigmoid** and {% raw %} $ g_4, g_5 $ {% endraw %} usually is **Tanh** and {% raw %} $ g_6 $ {% endraw %} usually is **sigmoid or Softmax** (depends of how variables you do like to identify).

##### Loss Function

At the same way, the loss function is:

<p align="center">
{% raw %}
  $
    L(\hat{y} , y) = \sum_{t=1}^{T_y} E^{( t )}
  $
{% endraw %}
</p>

##### Back Propagation Through Time (BPTT)

#### Gated Recurrent Unit (GRU)

The architecture is as follows:

<p align="center">
  <img height="300" width="200" src="/assets/ml/recurrent_networks/gru.png">
</p>

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
