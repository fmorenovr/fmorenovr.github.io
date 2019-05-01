---
layout: post
title:  "Machine Learning"
subtitle: Describing Machine Learning Types and Algorithms
date:   2019-04-20 12:15:12 -0500
categories: ml
---

# Machine Learning

Machine Learning is a scientific discipline in the field of Artificial Intelligence that creates systems that learn automatically.  
"Learning" in this context means identifying complex patterns in millions of data.  
What the machine really learns is an algorithm that reviews the data and is able to predict or describe future behaviors.

Example:

It is said that a program can learn from an **experience E** with respect to some **task T** and **performance P**, if its performance in tasks T measured by P, improves the experience E.

* Task: Is the case or problem to process.

* Performance: Each P measured from task T.

* Experience: Each result (improve or not) obtianed from a learning algrithm.

## DS vs DA ds DM vs DAc

Difference between Data Science, Data Analysis, Data Mining and Data Analytics.

* Data Science: Use Scientific methods, process and algorithms to extract knowlegde and insights from data (structured or/and unstructured). Data Science = Statistics + Data Analysis + Machine Learning + Data Mining.

* Data Analysis: Is the process of inspecting, cleaning, transforming and modeling data with the goal of discovering useful information, conclusions and decision-making or relationship in the data.

* Data Mining: Is the process of discovering patterns in large data sets for predictive purpose.

* Data Analytics: Is the process of describe methods and logic for analysis.

## Preprocessing process

* Missing data: Set all NA values to the mean or just delete these examples.

* Categorical data: When you have no comparable data, convert or encode labeling data in to numerical values. (useful in dependent variables).

  | data | Type A | Type B | Type C
  :---------:|:---:|:-----------:
   sample 1  | 1 | 0 | 0
   sample 2  | 0 | 0 | 1
   sample 3  | 0 | 1 | 0


* Data set: Divide data into training-set, validation-set and test-set.

* Feature Scale: Standarize(or Normalize) data (like distribution) to get a better organization of them.

## Machine Learning Types

Is the different types of machine learning.

![](/assets/ml/types.png)

### Supervised Learning

This type is based on the term `Conceptual Learning`, in other words, the learning process is to find a way to relationate organized data.

See main article [Supervised Learning](/ml/supervised_learning).

### Semi-Supervised Learning

This type is based on the term `Inductive Learning`, in other words, the learning process is to find a way to relationate a bit quantity of organized data to generalize it in large quantity of unorganized data.

See main article [Semi-Supervised Learning](/ml/semi_supervised_learning).

### Unsupervised Learning

This type is based on the term `Self-Organized Learning`, in other words, the learning process is to find a way to relationate patterns and characteristics of unorganized data.

See main article [UnSupervised Learning](/ml/unsupervised_learning).

### Similarity Learning

This type is based on the term `Compare Learning`, in other words, the learning process is to find from previously organized data a similarity function that measures how similar or related two objects are.

See main article [Similarity Learning](/ml/similarity_learning).

### Active Learning

This type is based on the term `Query-Answer Learning`, in other words, the learning process is the interaction between users and query website to get more data from them.

See main article [Active Learning](/ml/active_learning).

### Transfer Learning

This type is based on the term `Experienced Learning`, in other words, the learning process is take a previous learned parameters from some date and start new learning process using the target data.

See main article [Transfer Learning](/ml/transfer_learning).

### Meta-Learning

This type is based on the term `Autodidact Learning`, in other words, the learning process is to understand how to solve learning problems with greater flexibility, improving the performance of existing algorithms or inducing the learning algorithm itself.

See main article [Meta-Learning](/ml/meta_learning).

## Machine Learning Models/Algorithms

There is a different models or approach those define algorithms based on mathematics and statistics models in machine learning.

### Regularization

Is the process to solve the overfitting problem.

See main article [Regularization](/ml/regularization).

### Neural Networks

Is the model based on human neurons to solve more complex problems.

See main article [ANN](/ml/neural_networks).

### Bayesian Networks

Is a model based on ANN with Bayesian statistics distributions.

See main article [BNN](/ml/bayesian_networks).

### Super Vector Machine

See main article [SVM](/ml/svm).


