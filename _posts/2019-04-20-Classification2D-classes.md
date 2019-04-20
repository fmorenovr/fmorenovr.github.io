---
layout: post
title:  "Machine Learning - Supervised Learning"
subtitle: Linear Regression
date:   2019-04-20 12:15:12 -0500
categories: ml
---

# Deep Learning

## 1. Packages

* numpy is the fundamental package for scientific computation with Python.
* matplotlib is a robust library for generating graphs in Python.


```python
# Importing libraries
# Python imports
# Allow matplotlib to plot inside this notebook
%matplotlib inline
import sys
import numpy as np
import matplotlib.pyplot as plt
import matplotlib

# for auto-reloading extenrnal modules
# see http://stackoverflow.com/questions/1907993/autoreload-of-modules-in-ipython
%load_ext autoreload
%autoreload 2

# Print versions used
print('Python: {}.{}.{}'.format(*sys.version_info[:3]))
print('numpy: {}'.format(np.__version__))
print('matplotlib: {}'.format(matplotlib.__version__))
```

    Python: 3.6.5
    numpy: 1.15.1
    matplotlib: 2.2.2


## 2. Dataset

### Config Dataset


```python
np.random.seed(0)
N = 100 # number of points per class
D = 2 # dimensionality
K = 2 # number of classes
X = np.zeros((D,N*K))
y = np.zeros((1,N*K), dtype='uint8')
```


```python
print(X.shape)
```

    (2, 200)



```python
print(y.shape)
```

    (1, 200)


### Visualize Dataset


```python
# Display plots inline and change default figure size
%matplotlib inline
matplotlib.rcParams['figure.figsize'] = (10.0, 8.0)
matplotlib.rcParams['image.interpolation'] = 'nearest'
matplotlib.rcParams['image.cmap'] = 'gray'

np.random.seed(0)

# Generating the datast
for jj in range(K):
    ix = range(N*jj, N*(jj+1))
    rad = np.linspace(0.0,1,N) # radius
    th = np.linspace(jj*4, (jj+1)*4, N) + np.random.randn(N)*0.2 # theta
    out = np.transpose(np.c_[rad*np.sin(th), rad*np.cos(th)])
    X[:, ix] = out
    y[:, ix] = jj
    
fig = plt.figure()
plt.scatter(X[0, :], X[1, :], c=np.squeeze(y), s=40, cmap=plt.cm.Spectral)
plt.xlim([-1,1])
plt.ylim([-1,1])
fig.savefig('spiral_dataset.png')
```


![png](2D-classes_files/2D-classes_9_0.png)



```python
# Helper function to plot a decision boundary.
# If you don't fully understand this function don't worry, it just generates the contour plot below.
def plot_decision_boundary(model, X, y):
    # Set min and max values and give it some padding
    x_min, x_max = X[0, :].min() - 1, X[0, :].max() + 1
    y_min, y_max = X[1, :].min() - 1, X[1, :].max() + 1
    h = 0.01
    # Generate a grid of points with distance h between them
    xx, yy = np.meshgrid(np.arange(x_min, x_max, h), np.arange(y_min, y_max, h))
    # Predict the function value for the whole grid
    Z = model(np.c_[xx.ravel(), yy.ravel()])
    Z = Z.reshape(xx.shape)
    # Plot the contour and training examples
    plt.contourf(xx, yy, Z, cmap=plt.cm.Spectral)
    plt.ylabel('x2')
    plt.xlabel('x1')
    plt.scatter(X[0, :], X[1, :], c=y.ravel(), cmap=plt.cm.Spectral)
```

## 3 - General Architecture of the learning algorithm ##

For one example $x^{(i)}$:
$$z^{(i)} = w^T x^{(i)} + b \tag{1}$$
$$\hat{y}^{(i)} = a^{(i)} = sigmoid(z^{(i)})\tag{2}$$ 
$$ \mathcal{L}(a^{(i)}, y^{(i)}) =  - y^{(i)}  \log(a^{(i)}) - (1-y^{(i)} )  \log(1-a^{(i)})\tag{3}$$

The cost is then computed by summing over all training examples:
$$ J = \frac{1}{m} \sum_{i=1}^m \mathcal{L}(a^{(i)}, y^{(i)})\tag{6}$$

**Key steps**:
In this exercise, you will carry out the following steps: 
    - Initialize the parameters of the model
    - Learn the parameters for the model by minimizing the cost  
    - Use the learned parameters to make predictions (on the test set)
    - Analyse the results and conclude

## 4 - Building the parts of our algorithm ## 

The main steps for building a Neural Network are:
1. Define the model structure (such as number of input features) 
2. Initialize the model's parameters
3. Loop:
    - Calculate current loss (forward propagation)
    - Calculate current gradient (backward propagation)
    - Update parameters (gradient descent)

You often build 1-3 separately and integrate them into one function we call `model()`.


### 4.1 - Initializing parameters

**Exercise:** Implement parameter initialization in the cell below. You have to initialize w as a vector of zeros. If you don't know what numpy function to use, look up np.zeros() in the Numpy library's documentation


```python
def initialize_with_zeros(D, K):
    """
    This function creates a vector of zeros of shape (dim, 1) for w and initializes b to 0.
    
    Argument:
    dim -- size of the w vector we want (or number of parameters in this case)
    
    Returns:
    W -- initialized vector of shape (D, K)
    b -- initialized scalar (corresponds to the bias) of size K
    """
    
    ### START CODE HERE ### (≈ 2 lines of code)
    W = np.zeros((D,K))
    b = np.zeros((K,1))#np.random.random_sample(K,)
    ### END CODE HERE ###
    
    return W, b
```


```python
W_debug, b_debug = initialize_with_zeros(D, K)
print ("W = " + str(W_debug))
print ("b = " + str(b_debug))
```

    W = [[0. 0.]
     [0. 0.]]
    b = [[0.]
     [0.]]


**Expected Output**: 


<table style="width:15%">
    <tr>
        <td>  ** w **  </td>
        <td> [[ 0.  0.] </td>
    <tr>
        <td colspan=2>
 [ 0.  0.]] 
        </td>
    </tr>
    <tr>
        <td>  ** b **  </td>
        <td> [[ 0.] </td>
    <tr>
        <td colspan=2>    [ 0.]]  </td>
    </tr>
</table>



```python
def initialize_randomly(D, K):
    """
    This function creates a vector of zeros of shape (dim, 1) for w and initializes b to 0.
    
    Argument:
    dim -- size of the w vector we want (or number of parameters in this case)
    
    Returns:
    W -- initialized vector of shape (D, K)
    b -- initialized scalar (corresponds to the bias) of size K
    """
    
    ### START CODE HERE ### (≈ 2 lines of code)
    W = np.random.randn(D, K)
    b = np.random.randn(K,1)
    ### END CODE HERE ###
    
    return W, b
```


```python
W_ran, b_ran = initialize_randomly(D, K)
print ("W = " + str(W_ran))
print ("b = " + str(b_ran))
```

    W = [[-0.36918184 -0.23937918]
     [ 1.0996596   0.65526373]]
    b = [[ 0.64013153]
     [-1.61695604]]



```python
def initialize_he(D, K):
    """
    This function creates a vector of zeros of shape (dim, 1) for w and initializes b to 0.
    
    Argument:
    dim -- size of the w vector we want (or number of parameters in this case)
    
    Returns:
    W -- initialized vector of shape (D, K)
    b -- initialized scalar (corresponds to the bias) of size K
    """
    
    ### START CODE HERE ### (≈ 2 lines of code)
    W = np.random.randn(D, K)*np.sqrt(2/K)
    b = np.random.randn(K,1)*np.sqrt(2/K)
    
    ### END CODE HERE ###
    
    return W, b
```


```python
W_he, b_he = initialize_he(D, K)
print ("W = " + str(W_he))
print ("b = " + str(b_he))
```

    W = [[-0.02432612 -0.73803091]
     [ 0.2799246  -0.09815039]]
    b = [[0.91017891]
     [0.31721822]]



```python
def initialize_params(D, K, init_type='zeros'):
    if init_type == 'zeros':
        print('zero-based init')
        return initialize_with_zeros(D, K)
    elif init_type == 'random':
        print('random-based init')
        return initialize_randomly(D, K)
    elif init_type == 'he':
        print('he-based init')
        return initialize_he(D, K)
```

### 4.2 - Activation Functions

Sigmoid Function: it takes a real-valued number and “squashes” it into range between 0 and 1. In particular, large negative numbers become 0 and large positive numbers become 1. The sigmoid function has seen frequent use historically since it has a nice interpretation as the firing rate of a neuron: from not firing at all (0) to fully-saturated firing at an assumed maximum frequency (1).

**Exercise**: Using your code from "Python Basics", implement `sigmoid()`. As you've seen in the figure above, you need to compute $sigmoid( w^T x + b) = \frac{1}{1 + e^{-(w^T x + b)}}$ to make predictions. Use np.exp().


```python
def sigmoid(z):
    """
    Compute the sigmoid of z

    Arguments:
    z -- A scalar or numpy array of any size.

    Return:
    s -- sigmoid(z)
    """

    ### START CODE HERE ### (≈ 1 line of code)
    s = 1.0/(1.0+np.exp(-z))
    ### END CODE HERE ###
    
    return s
```


```python
print ("sigmoid([0, 2]) = " + str(sigmoid(np.array([0,2]))))
```

    sigmoid([0, 2]) = [0.5        0.88079708]


**Expected Output**: 

<table>
  <tr>
    <td>**sigmoid([0, 2])**</td>
    <td> [ 0.5         0.88079708]</td> 
  </tr>
</table>


```python
# Plot the logistic function
xval=11
no_samp=100
z = np.linspace(-xval, xval, no_samp)
plt.plot(z, sigmoid(z), 'b-')
plt.xlabel('$z$', fontsize=12)
plt.ylabel('$\sigma(z)$', fontsize=12)
plt.title('logistic function')
plt.xlim(-xval, xval)
plt.show()
#
```


![png](2D-classes_files/2D-classes_26_0.png)



```python
def sigmoid_deriv(z):
    """
    Compute the derivative of the sigmoid of z

    Arguments:
    z -- A scalar or numpy array of any size.

    Return:
    s -- sigmoid_deriv(z)
    """

    ### START CODE HERE ### (≈ 1 line of code)
    s = sigmoid(z) *(1 - sigmoid(z))
    
    ### END CODE HERE ###
    
    return s
```


```python
# Plot the logistic function
xval=11
no_samp=100
z = np.linspace(-xval, xval, no_samp)
plt.plot(z, sigmoid_deriv(z), 'b-')
plt.xlabel('$z$', fontsize=12)
plt.ylabel('$\sigma(z)$', fontsize=12)
plt.title('logistic function')
plt.xlim(-xval, xval)
plt.show()
#
```


![png](2D-classes_files/2D-classes_28_0.png)


### 4.3 - Cost Function
We’ll use cross-entropy for our cost function. The formula for a single training example is:
    
$$
L(y, \hat{y}) = -y \log(\hat{y}) - (1-y) \log(1-\hat{y})
$$

Averaging over a training set of $𝑚$ examples we then have:
    
$$
L(Y, \hat{Y}) = -\frac{1}{m} \sum_{i=1}^m \left( y^{(i)} \log(\hat{y}^{(i)}) + (1-y^{(i)}) \log(1-\hat{y}^{(i)}) \right)
$$


```python
def compute_cost(Y, Y_hat):

    ### START CODE HERE ### (≈ 2 lines of code)
    m = Y.shape[1]
    L = -(1/m)*np.sum(Y*np.log(Y_hat) + (1-Y)*np.log(1-Y_hat))
    
    ### END CODE HERE ###
    return L
```

### 4.4 - Forward and Backward propagation

Now that your parameters are initialized, you can do the "forward" and "backward" propagation steps for learning the parameters.

**Exercise:** Implement a function `propagate()` that computes the cost function and its gradient.


For backpropagation, we will need to know how $𝐿$ changes with respect to each component $w_j$ of $w$. That is, we must compute each $\partial L / \partial w_j$

\begin{align}
  z &= w^T x + b,\newline
  \hat{y} &= \sigma(z),\newline
  L(y, \hat{y}) &= -y \log(\hat{y}) - (1-y) \log(1-\hat{y})
\end{align}

And the chain rule tells us:

$$
\frac{\partial L}{\partial w_j} = \frac{\partial L}{\partial \hat{y}} \frac{\partial \hat{y}}{\partial z} \frac{\partial z}{\partial w_j}
$$

**Hints**:

Forward Propagation:
- You get X
- You compute $A = \hat{y} = \sigma(w^T X + b) = (a^{(1)}, a^{(2)}, ..., a^{(m-1)}, a^{(m)})$
- You calculate the cost function: $J = -\frac{1}{m}\sum_{i=1}^{m}y^{(i)}\log(a^{(i)})+(1-y^{(i)})\log(1-a^{(i)})$

Here are the two formulas you will be using: 

$$ \frac{\partial J}{\partial w} = \frac{1}{m}X(A-Y)^T\tag{7}$$
$$ \frac{\partial J}{\partial b} = \frac{1}{m} \sum_{i=1}^m (a^{(i)}-y^{(i)})\tag{8}$$


```python
def propagate(W, b, X, Y, use_reg=False, reg_lambda=0.01):
    """
    Implement the cost function and its gradient for the propagation explained above

    Arguments:
    w -- weights, a numpy array of size (num_px * num_px * 3, 1)
    b -- bias, a scalar
    X -- data of size (num_px * num_px * 3, number of examples)
    Y -- true "label" vector (containing 0 if non-cat, 1 if cat) of size (1, number of examples)

    Return:
    cost -- negative log-likelihood cost for logistic regression
    dW -- gradient of the loss with respect to w, thus same shape as w
    db -- gradient of the loss with respect to b, thus same shape as b
    
    Tips:
    - Write your code step by step for the propagation. np.log(), np.dot()
    """
    
    m = X.shape[1]
    
    # FORWARD PROPAGATION (FROM X TO COST)
    ### START CODE HERE ### (≈ 2 lines of code)
    A = sigmoid(np.dot(np.transpose(W),X)+b)
    J = compute_cost(Y, A)
    ### END CODE HERE ###
    
    if use_reg:
        ### START CODE HERE ### (≈ 2 lines of code)
        J = J + reg_lambda*0.5*np.sum(W*W)
        ### END CODE HERE ###
    
    # BACKWARD PROPAGATION (TO FIND GRAD)
    ### START CODE HERE ### (≈ 2 lines of code)
    dJdW = (1/m)*np.dot(X,np.transpose(A-Y))
    dJdb = (1/m)*np.sum(A-Y)
    ### END CODE HERE ###
    
    if use_reg:
        ### START CODE HERE ### (≈ 2 lines of code)
        dJdW = dJdW + reg_lambda*0.5*np.sum(W*W)
        ### END CODE HERE ###

    assert(dJdW.shape == W.shape)
    assert(dJdb.dtype == float)
    cost = np.squeeze(J)
    assert(cost.shape == ())
    
    grads = {"dW": dJdW,
             "db": dJdb}
    
    return grads, cost
```


```python
W_debug, b_debug, X_debug, y_debug = np.array([[1.],[2.]]), 2., np.array([[1.,2.,-1.],[3.,4.,-3.2]]), np.array([[1,0,1]])
grads, cost = propagate(W_debug, b_debug, X_debug, y_debug)
print ("dW = " + str(grads["dW"]))
print ("db = " + str(grads["db"]))
print ("cost = " + str(cost))
```

    dW = [[0.99845601]
     [2.39507239]]
    db = 0.001455578136784208
    cost = 5.801545319394553


**Expected Output**:

<table style="width:50%">
    <tr>
        <td>  ** dw **  </td>
      <td> [[ 0.99845601]
     [ 2.39507239]]</td>
    </tr>
    <tr>
        <td>  ** db **  </td>
        <td> 0.00145557813678 </td>
    </tr>
    <tr>
        <td>  ** cost **  </td>
        <td> 5.801545319394553 </td>
    </tr>

</table>

### 4.5 - Optimization
- You have initialized your parameters.
- You are also able to compute a cost function and its gradient.
- Now, you want to update the parameters using gradient descent.

**Exercise:** Write down the optimization function. The goal is to learn $w$ and $b$ by minimizing the cost function $J$. For a parameter $\theta$, the update rule is $ \theta = \theta - \alpha \text{ } d\theta$, where $\alpha$ is the learning rate.


```python
def optimize(W, b, X, Y, num_iterations, learning_rate, use_reg = False, reg_lambda = 0.01, print_cost = False):
    """
    This function optimizes w and b by running a gradient descent algorithm
    
    Arguments:
    w -- weights, a numpy array of size (num_px * num_px * 3, 1)
    b -- bias, a scalar
    X -- data of shape (num_px * num_px * 3, number of examples)
    Y -- true "label" vector (containing 0 if non-cat, 1 if cat), of shape (1, number of examples)
    num_iterations -- number of iterations of the optimization loop
    learning_rate -- learning rate of the gradient descent update rule
    use_reg -- use regularization
    reg_lambda -- regularization weight
    print_cost -- True to print the loss every 100 steps
    
    Returns:
    params -- dictionary containing the weights w and bias b
    grads -- dictionary containing the gradients of the weights and bias with respect to the cost function
    costs -- list of all the costs computed during the optimization, this will be used to plot the learning curve.
    
    Tips:
    You basically need to write down two steps and iterate through them:
        1) Calculate the cost and the gradient for the current parameters. Use propagate().
        2) Update the parameters using gradient descent rule for w and b.
    """
    
    costs = []
    
    for ii in range(num_iterations):
        
        
        # Cost and gradient calculation (≈ 1-4 lines of code)
        ### START CODE HERE ### 
        grads, cost = propagate(W, b, X, Y, use_reg, reg_lambda)
        ### END CODE HERE ###
        
        # Retrieve derivatives from grads
        dW = grads["dW"]
        db = grads["db"]
        
        # update rule (≈ 2 lines of code)
        ### START CODE HERE ###
        W = W - learning_rate*dW
        b = b - learning_rate*db
        ### END CODE HERE ###
        
        # Record the costs
        if ii % 100 == 0:
            costs.append(cost)
        
        # Print the cost every 200 training iterations
        if print_cost and ii % 200 == 0:
            print ("Cost after iteration %i: %f" %(ii, cost))
    
    params = {"W": W,
              "b": b}
    
    grads = {"dW": dW,
             "db": db}
    
    return params, grads, costs
```


```python
params, grads, costs = optimize(W_debug, b_debug, X_debug, y_debug, num_iterations= 100, learning_rate = 0.009, print_cost = False)

print ("W = " + str(params["W"]))
print ("b = " + str(params["b"]))
print ("dW = " + str(grads["dW"]))
print ("db = " + str(grads["db"]))
```

    W = [[0.19033591]
     [0.12259159]]
    b = 1.9253598300845747
    dW = [[0.67752042]
     [1.41625495]]
    db = 0.21919450454067657


**Expected Output**: 

<table style="width:40%">
    <tr>
       <td> **w** </td>
       <td>[[ 0.19033591] [ 0.12259159]] </td>
    </tr>
    
    <tr>
       <td> **b** </td>
       <td> 1.92535983008 </td>
    </tr>
    
    <tr>
       <td> **dw** </td>
       <td> [[ 0.67752042] [ 1.41625495]] </td>
    </tr>
    
    <tr>
       <td> **db** </td>
       <td> 0.219194504541 </td>
    </tr>

</table>

**Exercise:** The previous function will output the learned w and b. We are able to use w and b to predict the labels for a dataset X. Implement the `predict()` function. There are two steps to computing predictions:

1. Calculate $\hat{Y} = A = \sigma(w^T X + b)$

2. Convert the entries of a into 0 (if activation <= 0.5) or 1 (if activation > 0.5), stores the predictions in a vector `Y_prediction`. If you wish, you can use an `if`/`else` statement in a `for` loop (though there is also a way to vectorize this). 


```python
def predict(W, b, X):
    '''
    Predict whether the label is 0 or 1 using learned logistic regression parameters (w, b)
    
    Arguments:
    w -- weights, a numpy array of size (num_px * num_px * 3, 1)
    b -- bias, a scalar
    X -- data of size (num_px * num_px * 3, number of examples)
    
    Returns:
    Y_prediction -- a numpy array (vector) containing all predictions (0/1) for the examples in X
    '''
    
    m = X.shape[1]
    Y_prediction = np.zeros((1,m))
    
    # Compute vector "A" predicting the probabilities of a cat being present in the picture
    ### START CODE HERE ### (≈ 1 line of code)
    A = sigmoid(np.dot(np.transpose(W),X)+b)
    ### END CODE HERE ###
    
    for ii in range(A.shape[1]):
        
        # Convert probabilities A[0,i] to actual predictions p[0,i]
        ### START CODE HERE ### (≈ 4 lines of code)
        if A[0, ii]>0.5:
            Y_prediction[0,ii] = 1
        else:
            Y_prediction[0,ii] = 0
        ### END CODE HERE ###
    
    assert(Y_prediction.shape == (1, m))
    
    return Y_prediction
```


```python
W_debug = np.array([[0.1124579],[0.23106775]])
b_debug = -0.3
X_debug = np.array([[1.,-1.1,-3.2],[1.2,2.,0.1]])
print ("predictions = " + str(predict(W_debug, b_debug, X_debug)))
```

    predictions = [[1. 1. 0.]]


**Expected Output**: 

<table style="width:30%">
    <tr>
         <td>
             **predictions**
         </td>
          <td>
            [[ 1.  1.  0.]]
         </td>  
   </tr>

</table>

## 5 - Merge all functions into a model ##

You will now see how the overall model is structured by putting together all the building blocks (functions implemented in the previous parts) together, in the right order.

**Exercise:** Implement the model function. Use the following notation:
    - Y_prediction_test for your predictions on the test set
    - Y_prediction_train for your predictions on the train set
    - w, costs, grads for the outputs of optimize()


```python
def train(X_train, y_train, K=2, num_iterations=2000, learning_rate=0.5, use_reg=False, reg_lambda=0.01, init_type='zeros', print_cost=False):
    """
    Builds the logistic regression model by calling the function you've implemented previously
    
    Arguments:
    X_train -- training set represented by a numpy array of shape (num_px * num_px * 3, m_train)
    Y_train -- training labels represented by a numpy array (vector) of shape (1, m_train)
    X_test -- test set represented by a numpy array of shape (num_px * num_px * 3, m_test)
    Y_test -- test labels represented by a numpy array (vector) of shape (1, m_test)
    num_iterations -- hyperparameter representing the number of iterations to optimize the parameters
    learning_rate -- hyperparameter representing the learning rate used in the update rule of optimize()
    print_cost -- Set to true to print the cost every 100 iterations
    
    Returns:
    d -- dictionary containing information about the model.
    """
    
    
    # initialize parameters with zeros (≈ 1 line of code)
    ### START CODE HERE ### (≈ 1 line of code)
    D = X_train.shape[0]
    W, b = initialize_params(D, K, init_type)
    ### END CODE HERE ###

    # Gradient descent (≈ 1 line of code)
    ### START CODE HERE ### (≈ 1 line of code)
    parameters, grads, costs = optimize(W, b, X_train, y_train, num_iterations, learning_rate, use_reg, reg_lambda, print_cost)
    ### END CODE HERE ###
        
    # Retrieve parameters w and b from dictionary "parameters"
    W = parameters["W"]
    b = parameters["b"]
    
    Y_prediction_train = predict(W, b, X)
    
    # Print train/test Errors
    print("train accuracy: {} %".format(100 - np.mean(np.abs(Y_prediction_train - y_train)) * 100))
    
    d = {"costs": costs,
         "W" : W, 
         "b" : b,
         "learning_rate" : learning_rate,
         "num_iterations": num_iterations}
    
    return d
```


```python
# train model here (≈ 1 line of code), e.g. with learning_rate = 0.05
### START CODE HERE ### (≈ 1 line of code)
d =  train(X, y, K, num_iterations=9800, learning_rate = 0.05, use_reg = False, reg_lambda=0.01, init_type = 'zeros', print_cost = True)
### END CODE HERE ###
```

    zero-based init
    Cost after iteration 0: 1.386294
    Cost after iteration 200: 1.134444
    Cost after iteration 400: 1.018996
    Cost after iteration 600: 0.957370
    Cost after iteration 800: 0.920485
    Cost after iteration 1000: 0.896595
    Cost after iteration 1200: 0.880233
    Cost after iteration 1400: 0.868558
    Cost after iteration 1600: 0.859963
    Cost after iteration 1800: 0.853477
    Cost after iteration 2000: 0.848484
    Cost after iteration 2200: 0.844579
    Cost after iteration 2400: 0.841481
    Cost after iteration 2600: 0.838996
    Cost after iteration 2800: 0.836982
    Cost after iteration 3000: 0.835337
    Cost after iteration 3200: 0.833982
    Cost after iteration 3400: 0.832859
    Cost after iteration 3600: 0.831923
    Cost after iteration 3800: 0.831139
    Cost after iteration 4000: 0.830478
    Cost after iteration 4200: 0.829920
    Cost after iteration 4400: 0.829447
    Cost after iteration 4600: 0.829044
    Cost after iteration 4800: 0.828700
    Cost after iteration 5000: 0.828405
    Cost after iteration 5200: 0.828152
    Cost after iteration 5400: 0.827934
    Cost after iteration 5600: 0.827747
    Cost after iteration 5800: 0.827585
    Cost after iteration 6000: 0.827444
    Cost after iteration 6200: 0.827323
    Cost after iteration 6400: 0.827217
    Cost after iteration 6600: 0.827125
    Cost after iteration 6800: 0.827046
    Cost after iteration 7000: 0.826976
    Cost after iteration 7200: 0.826915
    Cost after iteration 7400: 0.826862
    Cost after iteration 7600: 0.826816
    Cost after iteration 7800: 0.826776
    Cost after iteration 8000: 0.826740
    Cost after iteration 8200: 0.826709
    Cost after iteration 8400: 0.826682
    Cost after iteration 8600: 0.826658
    Cost after iteration 8800: 0.826637
    Cost after iteration 9000: 0.826619
    Cost after iteration 9200: 0.826602
    Cost after iteration 9400: 0.826588
    Cost after iteration 9600: 0.826576
    train accuracy: 72.5 %


**Expected Output**: 

<table style="width:40%"> 

    <tr>
        <td> **Cost after iteration 0 **  </td> 
        <td> 1.386294 </td>
    </tr>
      <tr>
        <td> <center> $\vdots$ </center> </td> 
        <td> <center> $\vdots$ </center> </td> 
    </tr>  
    <tr>
        <td> **Train Accuracy**  </td> 
        <td> 72.5 % </td>
    </tr>
    
</table> 


```python
W = d['W']
b = d['b']
plt.title("Decision Boundary for simple NN")
# plot decision boundary here (≈ 1 line of code)
plot_decision_boundary(lambda x: predict(W,b,x.T), X, y)
```


![png](2D-classes_files/2D-classes_47_0.png)


## 6 - Further Analysis

### 6.1 - Choice of learning rate

**Reminder**:
In order for Gradient Descent to work you must choose the learning rate wisely. The learning rate $\alpha$  determines how rapidly we update the parameters. If the learning rate is too large we may "overshoot" the optimal value. Similarly, if it is too small we will need too many iterations to converge to the best values. That's why it is crucial to use a well-tuned learning rate.

Let's compare the learning curve of our model with several choices of learning rates. Run the cell below. This should take about 1 minute. Feel free also to try different values than the three we have initialized the `learning_rates` variable to contain, and see what happens. 


```python
learning_rates = [0.01, 0.05, 0.001, 0.005, 0.0001, 0.0005]
models = {}
for lr in learning_rates:
    print ("learning rate is: " + str(lr))
    # train model here with different learning rates (≈ 1 line of code)
    models[str(lr)] = train(X, y, K, num_iterations=9800, learning_rate = lr, use_reg = False, reg_lambda=0.01, init_type = 'zeros', print_cost = True)
    print ('\n' + "-------------------------------------------------------" + '\n')

for lr in learning_rates:
    plt.plot(np.squeeze(models[str(lr)]["costs"]), label= str(models[str(lr)]["learning_rate"]))

plt.ylabel('cost')
plt.xlabel('iterations')

legend = plt.legend(loc='upper center', shadow=True)
frame = legend.get_frame()
frame.set_facecolor('0.90')
plt.show()
```

    learning rate is: 0.01
    zero-based init
    Cost after iteration 0: 1.386294
    Cost after iteration 200: 1.317260
    Cost after iteration 400: 1.259435
    Cost after iteration 600: 1.210787
    Cost after iteration 800: 1.169627
    Cost after iteration 1000: 1.134579
    Cost after iteration 1200: 1.104536
    Cost after iteration 1400: 1.078611
    Cost after iteration 1600: 1.056094
    Cost after iteration 1800: 1.036416
    Cost after iteration 2000: 1.019118
    Cost after iteration 2200: 1.003828
    Cost after iteration 2400: 0.990245
    Cost after iteration 2600: 0.978120
    Cost after iteration 2800: 0.967250
    Cost after iteration 3000: 0.957464
    Cost after iteration 3200: 0.948621
    Cost after iteration 3400: 0.940602
    Cost after iteration 3600: 0.933307
    Cost after iteration 3800: 0.926649
    Cost after iteration 4000: 0.920557
    Cost after iteration 4200: 0.914967
    Cost after iteration 4400: 0.909825
    Cost after iteration 4600: 0.905085
    Cost after iteration 4800: 0.900705
    Cost after iteration 5000: 0.896651
    Cost after iteration 5200: 0.892890
    Cost after iteration 5400: 0.889395
    Cost after iteration 5600: 0.886142
    Cost after iteration 5800: 0.883109
    Cost after iteration 6000: 0.880277
    Cost after iteration 6200: 0.877629
    Cost after iteration 6400: 0.875150
    Cost after iteration 6600: 0.872826
    Cost after iteration 6800: 0.870644
    Cost after iteration 7000: 0.868593
    Cost after iteration 7200: 0.866664
    Cost after iteration 7400: 0.864847
    Cost after iteration 7600: 0.863134
    Cost after iteration 7800: 0.861518
    Cost after iteration 8000: 0.859991
    Cost after iteration 8200: 0.858547
    Cost after iteration 8400: 0.857182
    Cost after iteration 8600: 0.855888
    Cost after iteration 8800: 0.854662
    Cost after iteration 9000: 0.853500
    Cost after iteration 9200: 0.852396
    Cost after iteration 9400: 0.851348
    Cost after iteration 9600: 0.850352
    train accuracy: 72.0 %
    
    -------------------------------------------------------
    
    learning rate is: 0.05
    zero-based init
    Cost after iteration 0: 1.386294
    Cost after iteration 200: 1.134444
    Cost after iteration 400: 1.018996
    Cost after iteration 600: 0.957370
    Cost after iteration 800: 0.920485
    Cost after iteration 1000: 0.896595
    Cost after iteration 1200: 0.880233
    Cost after iteration 1400: 0.868558
    Cost after iteration 1600: 0.859963
    Cost after iteration 1800: 0.853477
    Cost after iteration 2000: 0.848484
    Cost after iteration 2200: 0.844579
    Cost after iteration 2400: 0.841481
    Cost after iteration 2600: 0.838996
    Cost after iteration 2800: 0.836982
    Cost after iteration 3000: 0.835337
    Cost after iteration 3200: 0.833982
    Cost after iteration 3400: 0.832859
    Cost after iteration 3600: 0.831923
    Cost after iteration 3800: 0.831139
    Cost after iteration 4000: 0.830478
    Cost after iteration 4200: 0.829920
    Cost after iteration 4400: 0.829447
    Cost after iteration 4600: 0.829044
    Cost after iteration 4800: 0.828700
    Cost after iteration 5000: 0.828405
    Cost after iteration 5200: 0.828152
    Cost after iteration 5400: 0.827934
    Cost after iteration 5600: 0.827747
    Cost after iteration 5800: 0.827585
    Cost after iteration 6000: 0.827444
    Cost after iteration 6200: 0.827323
    Cost after iteration 6400: 0.827217
    Cost after iteration 6600: 0.827125
    Cost after iteration 6800: 0.827046
    Cost after iteration 7000: 0.826976
    Cost after iteration 7200: 0.826915
    Cost after iteration 7400: 0.826862
    Cost after iteration 7600: 0.826816
    Cost after iteration 7800: 0.826776
    Cost after iteration 8000: 0.826740
    Cost after iteration 8200: 0.826709
    Cost after iteration 8400: 0.826682
    Cost after iteration 8600: 0.826658
    Cost after iteration 8800: 0.826637
    Cost after iteration 9000: 0.826619
    Cost after iteration 9200: 0.826602
    Cost after iteration 9400: 0.826588
    Cost after iteration 9600: 0.826576
    train accuracy: 72.5 %
    
    -------------------------------------------------------
    
    learning rate is: 0.001
    zero-based init
    Cost after iteration 0: 1.386294
    Cost after iteration 200: 1.378823
    Cost after iteration 400: 1.371484
    Cost after iteration 600: 1.364276
    Cost after iteration 800: 1.357197
    Cost after iteration 1000: 1.350242
    Cost after iteration 1200: 1.343411
    Cost after iteration 1400: 1.336701
    Cost after iteration 1600: 1.330109
    Cost after iteration 1800: 1.323634
    Cost after iteration 2000: 1.317273
    Cost after iteration 2200: 1.311023
    Cost after iteration 2400: 1.304883
    Cost after iteration 2600: 1.298850
    Cost after iteration 2800: 1.292923
    Cost after iteration 3000: 1.287099
    Cost after iteration 3200: 1.281376
    Cost after iteration 3400: 1.275752
    Cost after iteration 3600: 1.270226
    Cost after iteration 3800: 1.264794
    Cost after iteration 4000: 1.259456
    Cost after iteration 4200: 1.254210
    Cost after iteration 4400: 1.249053
    Cost after iteration 4600: 1.243983
    Cost after iteration 4800: 1.239000
    Cost after iteration 5000: 1.234101
    Cost after iteration 5200: 1.229285
    Cost after iteration 5400: 1.224550
    Cost after iteration 5600: 1.219894
    Cost after iteration 5800: 1.215315
    Cost after iteration 6000: 1.210813
    Cost after iteration 6200: 1.206386
    Cost after iteration 6400: 1.202031
    Cost after iteration 6600: 1.197748
    Cost after iteration 6800: 1.193536
    Cost after iteration 7000: 1.189392
    Cost after iteration 7200: 1.185315
    Cost after iteration 7400: 1.181304
    Cost after iteration 7600: 1.177359
    Cost after iteration 7800: 1.173476
    Cost after iteration 8000: 1.169656
    Cost after iteration 8200: 1.165896
    Cost after iteration 8400: 1.162197
    Cost after iteration 8600: 1.158555
    Cost after iteration 8800: 1.154971
    Cost after iteration 9000: 1.151444
    Cost after iteration 9200: 1.147971
    Cost after iteration 9400: 1.144552
    Cost after iteration 9600: 1.141186
    train accuracy: 68.5 %
    
    -------------------------------------------------------
    
    learning rate is: 0.005
    zero-based init
    Cost after iteration 0: 1.386294
    Cost after iteration 200: 1.350239
    Cost after iteration 400: 1.317267
    Cost after iteration 600: 1.287091
    Cost after iteration 800: 1.259447
    Cost after iteration 1000: 1.234091
    Cost after iteration 1200: 1.210802
    Cost after iteration 1400: 1.189379
    Cost after iteration 1600: 1.169643
    Cost after iteration 1800: 1.151430
    Cost after iteration 2000: 1.134596
    Cost after iteration 2200: 1.119009
    Cost after iteration 2400: 1.104553
    Cost after iteration 2600: 1.091124
    Cost after iteration 2800: 1.078628
    Cost after iteration 3000: 1.066982
    Cost after iteration 3200: 1.056111
    Cost after iteration 3400: 1.045947
    Cost after iteration 3600: 1.036432
    Cost after iteration 3800: 1.027510
    Cost after iteration 4000: 1.019133
    Cost after iteration 4200: 1.011257
    Cost after iteration 4400: 1.003843
    Cost after iteration 4600: 0.996854
    Cost after iteration 4800: 0.990259
    Cost after iteration 5000: 0.984027
    Cost after iteration 5200: 0.978133
    Cost after iteration 5400: 0.972552
    Cost after iteration 5600: 0.967262
    Cost after iteration 5800: 0.962243
    Cost after iteration 6000: 0.957475
    Cost after iteration 6200: 0.952944
    Cost after iteration 6400: 0.948632
    Cost after iteration 6600: 0.944526
    Cost after iteration 6800: 0.940612
    Cost after iteration 7000: 0.936880
    Cost after iteration 7200: 0.933317
    Cost after iteration 7400: 0.929913
    Cost after iteration 7600: 0.926659
    Cost after iteration 7800: 0.923546
    Cost after iteration 8000: 0.920566
    Cost after iteration 8200: 0.917711
    Cost after iteration 8400: 0.914976
    Cost after iteration 8600: 0.912352
    Cost after iteration 8800: 0.909833
    Cost after iteration 9000: 0.907416
    Cost after iteration 9200: 0.905093
    Cost after iteration 9400: 0.902860
    Cost after iteration 9600: 0.900713
    train accuracy: 70.5 %
    
    -------------------------------------------------------
    
    learning rate is: 0.0001
    zero-based init
    Cost after iteration 0: 1.386294
    Cost after iteration 200: 1.385541
    Cost after iteration 400: 1.384789
    Cost after iteration 600: 1.384039
    Cost after iteration 800: 1.383290
    Cost after iteration 1000: 1.382542
    Cost after iteration 1200: 1.381795
    Cost after iteration 1400: 1.381050
    Cost after iteration 1600: 1.380307
    Cost after iteration 1800: 1.379564
    Cost after iteration 2000: 1.378823
    Cost after iteration 2200: 1.378083
    Cost after iteration 2400: 1.377345
    Cost after iteration 2600: 1.376608
    Cost after iteration 2800: 1.375872
    Cost after iteration 3000: 1.375137
    Cost after iteration 3200: 1.374404
    Cost after iteration 3400: 1.373672
    Cost after iteration 3600: 1.372942
    Cost after iteration 3800: 1.372213
    Cost after iteration 4000: 1.371485
    Cost after iteration 4200: 1.370758
    Cost after iteration 4400: 1.370033
    Cost after iteration 4600: 1.369309
    Cost after iteration 4800: 1.368586
    Cost after iteration 5000: 1.367865
    Cost after iteration 5200: 1.367144
    Cost after iteration 5400: 1.366426
    Cost after iteration 5600: 1.365708
    Cost after iteration 5800: 1.364992
    Cost after iteration 6000: 1.364277
    Cost after iteration 6200: 1.363563
    Cost after iteration 6400: 1.362851
    Cost after iteration 6600: 1.362140
    Cost after iteration 6800: 1.361430
    Cost after iteration 7000: 1.360721
    Cost after iteration 7200: 1.360014
    Cost after iteration 7400: 1.359308
    Cost after iteration 7600: 1.358603
    Cost after iteration 7800: 1.357899
    Cost after iteration 8000: 1.357197
    Cost after iteration 8200: 1.356496
    Cost after iteration 8400: 1.355796
    Cost after iteration 8600: 1.355098
    Cost after iteration 8800: 1.354400
    Cost after iteration 9000: 1.353704
    Cost after iteration 9200: 1.353010
    Cost after iteration 9400: 1.352316
    Cost after iteration 9600: 1.351624
    train accuracy: 68.0 %
    
    -------------------------------------------------------
    
    learning rate is: 0.0005
    zero-based init
    Cost after iteration 0: 1.386294
    Cost after iteration 200: 1.382542
    Cost after iteration 400: 1.378823
    Cost after iteration 600: 1.375137
    Cost after iteration 800: 1.371485
    Cost after iteration 1000: 1.367864
    Cost after iteration 1200: 1.364277
    Cost after iteration 1400: 1.360721
    Cost after iteration 1600: 1.357197
    Cost after iteration 1800: 1.353704
    Cost after iteration 2000: 1.350243
    Cost after iteration 2200: 1.346812
    Cost after iteration 2400: 1.343412
    Cost after iteration 2600: 1.340042
    Cost after iteration 2800: 1.336702
    Cost after iteration 3000: 1.333391
    Cost after iteration 3200: 1.330110
    Cost after iteration 3400: 1.326858
    Cost after iteration 3600: 1.323635
    Cost after iteration 3800: 1.320440
    Cost after iteration 4000: 1.317273
    Cost after iteration 4200: 1.314135
    Cost after iteration 4400: 1.311024
    Cost after iteration 4600: 1.307940
    Cost after iteration 4800: 1.304884
    Cost after iteration 5000: 1.301854
    Cost after iteration 5200: 1.298851
    Cost after iteration 5400: 1.295875
    Cost after iteration 5600: 1.292924
    Cost after iteration 5800: 1.289999
    Cost after iteration 6000: 1.287100
    Cost after iteration 6200: 1.284226
    Cost after iteration 6400: 1.281377
    Cost after iteration 6600: 1.278553
    Cost after iteration 6800: 1.275753
    Cost after iteration 7000: 1.272978
    Cost after iteration 7200: 1.270227
    Cost after iteration 7400: 1.267499
    Cost after iteration 7600: 1.264795
    Cost after iteration 7800: 1.262115
    Cost after iteration 8000: 1.259457
    Cost after iteration 8200: 1.256823
    Cost after iteration 8400: 1.254211
    Cost after iteration 8600: 1.251621
    Cost after iteration 8800: 1.249054
    Cost after iteration 9000: 1.246508
    Cost after iteration 9200: 1.243985
    Cost after iteration 9400: 1.241482
    Cost after iteration 9600: 1.239001
    train accuracy: 68.5 %
    
    -------------------------------------------------------
    



![png](2D-classes_files/2D-classes_49_1.png)


### 6.2 - Regularization


```python
# train model here using regularization (≈ 1 line of code)
d = train(X, y, K, num_iterations=9800, learning_rate = 0.005, use_reg = True, reg_lambda=0.01, init_type = 'zeros', print_cost = True)
```

    zero-based init
    Cost after iteration 0: 1.386294
    Cost after iteration 200: 1.350436
    Cost after iteration 400: 1.318073
    Cost after iteration 600: 1.288928
    Cost after iteration 800: 1.262721
    Cost after iteration 1000: 1.239180
    Cost after iteration 1200: 1.218047
    Cost after iteration 1400: 1.199079
    Cost after iteration 1600: 1.182055
    Cost after iteration 1800: 1.166771
    Cost after iteration 2000: 1.153044
    Cost after iteration 2200: 1.140711
    Cost after iteration 2400: 1.129624
    Cost after iteration 2600: 1.119656
    Cost after iteration 2800: 1.110691
    Cost after iteration 3000: 1.102628
    Cost after iteration 3200: 1.095378
    Cost after iteration 3400: 1.088864
    Cost after iteration 3600: 1.083017
    Cost after iteration 3800: 1.077776
    Cost after iteration 4000: 1.073088
    Cost after iteration 4200: 1.068907
    Cost after iteration 4400: 1.065192
    Cost after iteration 4600: 1.061906
    Cost after iteration 4800: 1.059018
    Cost after iteration 5000: 1.056498
    Cost after iteration 5200: 1.054323
    Cost after iteration 5400: 1.052469
    Cost after iteration 5600: 1.050916
    Cost after iteration 5800: 1.049648
    Cost after iteration 6000: 1.048647
    Cost after iteration 6200: 1.047899
    Cost after iteration 6400: 1.047391
    Cost after iteration 6600: 1.047112
    Cost after iteration 6800: 1.047050
    Cost after iteration 7000: 1.047196
    Cost after iteration 7200: 1.047541
    Cost after iteration 7400: 1.048076
    Cost after iteration 7600: 1.048794
    Cost after iteration 7800: 1.049688
    Cost after iteration 8000: 1.050752
    Cost after iteration 8200: 1.051978
    Cost after iteration 8400: 1.053363
    Cost after iteration 8600: 1.054900
    Cost after iteration 8800: 1.056584
    Cost after iteration 9000: 1.058411
    Cost after iteration 9200: 1.060377
    Cost after iteration 9400: 1.062478
    Cost after iteration 9600: 1.064709
    train accuracy: 79.0 %


**Expected Output**: 

<table style="width:40%"> 

    <tr>
        <td> **Cost after iteration 0 **  </td> 
        <td> 1.386294 </td>
    </tr>
      <tr>
        <td> <center> $\vdots$ </center> </td> 
        <td> <center> $\vdots$ </center> </td> 
    </tr>  
    <tr>
        <td> **Train Accuracy**  </td> 
        <td> 73 % </td>
    </tr>
    
</table> 


```python
W = d['W']
b = d['b']
plt.title("Decision Boundary for simple NN")
# plot decision boundary here (≈ 1 line of code)
plot_decision_boundary(lambda x: predict(W,b,x.T), X, y)
```


![png](2D-classes_files/2D-classes_53_0.png)



```python
# train model here with different weight's initialization, e.g. 'he/random' (≈ 1 line of code)
d =  train(X, y, K, num_iterations=9800, learning_rate = 0.005, use_reg = True, reg_lambda=0.01, init_type = 'he', print_cost = True)
```

    he-based init
    Cost after iteration 0: 1.707731
    Cost after iteration 200: 1.529648
    Cost after iteration 400: 1.434619
    Cost after iteration 600: 1.378566
    Cost after iteration 800: 1.340209
    Cost after iteration 1000: 1.310336
    Cost after iteration 1200: 1.285100
    Cost after iteration 1400: 1.262875
    Cost after iteration 1600: 1.242928
    Cost after iteration 1800: 1.224881
    Cost after iteration 2000: 1.208500
    Cost after iteration 2200: 1.193615
    Cost after iteration 2400: 1.180085
    Cost after iteration 2600: 1.167785
    Cost after iteration 2800: 1.156605
    Cost after iteration 3000: 1.146447
    Cost after iteration 3200: 1.137221
    Cost after iteration 3400: 1.128847
    Cost after iteration 3600: 1.121252
    Cost after iteration 3800: 1.114372
    Cost after iteration 4000: 1.108148
    Cost after iteration 4200: 1.102529
    Cost after iteration 4400: 1.097469
    Cost after iteration 4600: 1.092925
    Cost after iteration 4800: 1.088860
    Cost after iteration 5000: 1.085241
    Cost after iteration 5200: 1.082039
    Cost after iteration 5400: 1.079225
    Cost after iteration 5600: 1.076776
    Cost after iteration 5800: 1.074670
    Cost after iteration 6000: 1.072887
    Cost after iteration 6200: 1.071409
    Cost after iteration 6400: 1.070220
    Cost after iteration 6600: 1.069305
    Cost after iteration 6800: 1.068649
    Cost after iteration 7000: 1.068242
    Cost after iteration 7200: 1.068071
    Cost after iteration 7400: 1.068126
    Cost after iteration 7600: 1.068397
    Cost after iteration 7800: 1.068875
    Cost after iteration 8000: 1.069552
    Cost after iteration 8200: 1.070421
    Cost after iteration 8400: 1.071474
    Cost after iteration 8600: 1.072705
    Cost after iteration 8800: 1.074107
    Cost after iteration 9000: 1.075674
    Cost after iteration 9200: 1.077402
    Cost after iteration 9400: 1.079286
    Cost after iteration 9600: 1.081320
    train accuracy: 82.0 %



```python
W = d['W']
b = d['b']
plt.title("Decision Boundary for simple NN")
# plot decision boundary here (≈ 1 line of code)
plot_decision_boundary(lambda x: predict(W,b,x.T), X, y)
```


![png](2D-classes_files/2D-classes_55_0.png)


### 6.3 - Learning Rates


```python
plt.figure(figsize=(16, 32))
epsilon_steps = [1.0, 0.1, 0.5, 0.01, 0.05, 0.001, 0.005, 0.0001, 0.0005]
for ii, epsilon_st in enumerate(epsilon_steps):
    plt.subplot(5, 2, ii+1)
    plt.title('Epsilon value %2.4f' % epsilon_st)
    # train model here with different learning rates (≈ 1 line of code)
    model = train(X, y, K, num_iterations=9800, learning_rate = epsilon_st, use_reg = True, reg_lambda=0.001, init_type = 'random', print_cost = False)
    W = model['W']
    b = model['b']
    # plot decision boundary here (≈ 1 line of code)
    plot_decision_boundary(lambda x: predict(W,b,x.T), X, y)
plt.show()
```

    random-based init
    train accuracy: 75.0 %
    random-based init
    train accuracy: 80.0 %
    random-based init
    train accuracy: 78.5 %
    random-based init
    train accuracy: 76.0 %
    random-based init
    train accuracy: 77.0 %
    random-based init
    train accuracy: 50.0 %
    random-based init
    train accuracy: 74.0 %
    random-based init
    train accuracy: 49.0 %
    random-based init
    train accuracy: 49.0 %



![png](2D-classes_files/2D-classes_57_1.png)

