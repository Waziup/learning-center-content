---
title: Machine Learning 
desc: General introduction to Machine Learning
---

In this lesson, we'll learn the basics about Machine Learning (ML).

# General Introduction

Machine Learning is a subfield of AI. Machine learning is a process that uses an algorithm to analyze data, learn from the data and make a statement or prediction about it. Unlike software, which was programmed by hand and performed tasks by specific instructions, the machine can be trained using large amounts of data and algorithms. This allows it to learn how to perform a task.

But none reached the goal of "Artificial General Intelligence" and even “Artificial Narrow Intelligence” was difficult to achieve with early machine learning approaches.

# Applications

It turned out that one of the best areas of application for machine learning was the Computer Vision program. However, a lot of manual programming was required for the machine learning to work. Data Scientists wrote classifiers like Edge Detection Filters. The program could now figure out where objects began and where they ended, recognize the shape of an object, and recognize the letters STOP. From this, an algorithm was developed that recognized images and learned what a stop sign is. That's a good idea, but on days when it was very foggy, for example, or trees partially covered the sign, the algorithm was rarely able to identify the sign.

There are also other important areas where machine leaning is applied.

# Overview of different styles of learning in Machine learning algorithms

There four different styles in machine learning algorithms, all of them are discussed below.

## 1. Unsupervised Learning

Is a type of algorithm that learns patterns from untagged data.

The input data is not labeled, so the result is not known. Models are created by deriving structural elements in input data. Methods are applied to select special occurrences of patterns in data.

Mathematical processes are applied to reduce the data in redundancy or group them by similarity.

Unsupervised learning is usually being used in:
- Clustering
- Association rule learning
- Dimensionality reduction tasks

An algorithm where unsupervised learning is applied:
- K-Means
- Eclat algorithm

## 2. Supervised Learning

Is a task of learning a function which maps an input to an output based on example input-output pairs, it saw (learned) before.

Here the input data is labeled. The model has to be trained before it can be used and give predictions (inference is conducted). The model needs to be trained as long as it achieves the desired accuracy on data for validation.

Supervised learning is usually used to solve the following problems:
- Classification
- Regression

Algorithms where supervised learning is applied:
- Convolutional neural networks (CNNs)
- Linear Regression

## 3. Semi-Supervised Learning

Is a task in machine learning that combines a small amount of labeled data and a large amount of unlabeled data.

Semi-Supervised learning is usually used to solve the following problems:
- Classification
- Regression

## 4. Reinforced Learning

In reinforced learning a learning argent learns from its environment. So, it works on interacting with the environment. The type of input data is not predefined. An agent rewards the model for success and does not reward it for a failure.

Reinforced Learning learning is usually used to solve the following problems:
- Exploitation 
- Exploration

Algorithms where reinforced learning is applied:
- Q-Learning,
- SARSA


# Overview of different Machine learning algorithms grouped by similarity

In the following there is an overview about the different algorithms that are being used in machine learning, they are grouped by similarity.

## Algorithms used for Regression Analysis

Regression algorithms are trying to map an association between variables. Models are refined by the measurement of errors in predictions that are made by a model.

Regression methods are originated from the scientific field of statistics and had been adopted to statistical machine learning.

Here are some examples of Regression Analysis:

- Ordinary Least Squares Regression (OLSR)
- Linear Regression
- Logistic Regression
- Stepwise Regression
- Multivariate Adaptive Regression Splines (MARS)
- Locally Estimated Scatterplot Smoothing (LOESS)

## Algorithms that are instance-based

Instance-based learning, also called memory-based learning, is a learning algorithm, which instead of performing a generalization, compares an input with instances seen during training. This means the complexity to solve the problem will grow with the learned data, which was used during training. 

Here are some examples of algorithms that are instance-based:

- k-Nearest Neighbor (kNN)
- kernel machines
- Self-Organizing Map (SOM)
- Radial basis function network (RBF)
- Locally Weighted Learning (LWL)
- Support Vector Machines (SVM)

## Algorithms used for regularization

Regularization is a technique used in Regression Analysis to reduce complexity of a model and shrink coefficients of independent features.
So the task of regularization is to convert complex models into simpler ones, that need less computational cost and also avoid the risk of overfitting. 

Here are some examples of algorithms that are used for regularization:

- Least Absolute Shrinkage and Selection Operator Regression (LASSO) (L1)
- Ridge Regression (L2)
- Elastic-Net Regression
- Least-Angle Regression (LARS)

## Algorithms used for Decision Trees

Decision Trees belong to the family of supervised machine learning algorithms. They can be used in classification and regression. Consequently, there are two types of decision trees:

1. **Categorical** Variable Decision Trees: Solves a classification problem, the leaves of the tree represent the categories. 
2. **Continuous** Variable Decision Trees: Solves a regression problem, the leaves are "bins" that represent ranges in a numerical space.

Here are some examples of algorithms that are used for decision trees:

- Iterative Dichotomiser 3 (ID3)
- C4.5 and C5.0 (successor of ID3)
- Classification And Regression Tree (CART)
- Chi-square automatic interaction detection Performs multi-level splits when computing classification trees (CHAID)
- Multivariate adaptive regression splines (MARS)
- Decision Stumps
- Conditional Decision Trees

## Algorithms that implement Bayes' Theorem

The Bayes' Theorem provides a way of thinking about the relationship between data and a specific model. The theorem is a method to determine conditional probabilities, this means the probability of a specific event occurring, if another event already occurred. Bayesian can be applied to solve regression and classification problems.

Here are some examples of algorithms that implement Bayes' Theorem:

- Naive Bayes
- Gaussian Naive Bayes
- Bayesian Belief Network (BBN)
- Bayesian Network (BN)
- Multinomial Naive Bayes
- Averaged One-Dependence Estimators (AODE)

## CLustering Algorithms

Clustering is a Machine Learning technique that aims to group similar data points. In theory data that is in the same group, should share the same properties. Clustering can be a supervised- or unsupervised learning method. They are typically organized by the modeling approaches such as hierarchal and centroid-based.

Here are some examples of CLustering Algorithms:

- K-Means Clustering
- Mean-Shift Clustering
- Density-Based Spatial Clustering of Applications with Noise (DBSCAN)
- Expectation–Maximization (EM) Clustering using Gaussian Mixture Models (GMM)
- Agglomerative Hierarchical Clustering

Further information can be obtained from the article [The 5 Clustering Algorithms Data Scientists Need to Know, by George Seif](https://towardsdatascience.com/the-5-clustering-algorithms-data-scientists-need-to-know-a36d136ef68).

## Association Rule Learning Algorithms

Association Rule learning is an unsupervised technique. It checks the dependency of one data item on another item and maps them accordingly. Association rule learning tries to find, according to different rules, associations or relations among variables of a given dataset.

Here are some examples of Association Rule Learning Algorithms:
- Eclat algorithm
- Apriori algorithm

## Algorithms that use Neural Networks

Neural Networks are inspired by operations of neurons in the human brain. 

The models are created with help of a supervised learning process. 
Neural networks are a big subfield of machine learning, containing hundreds of algorithms and variations for many problem types.

Here are some examples of neural networks:
- Perceptron
- Multilayer Perceptrons (MLP)

In recent years the neural networks are getting bigger and bigger, more layers, more parameters, ... . Also, the size of the training data was increased. Therefore, a new subfield of machine learning was found to host these kinds of algorithms. It is called **Deep Learning**. 

Here are some examples of deep leaning algorithms:
- Convolutional Neural Networks (CNNs)
- Recurrent Neural Networks (RNNs)
- Deep Belief Networks (DBN)

## Ensemble learning algorithms

Ensemble learning combination of different methods using numerous learning algorithms, to get better prediction results. The results are usually better than one approach alone. The models being trained independently and are combined afterwards. This is a lengthy process, because they have to be combined in a useful way.

Here are some examples of ensemble learning algorithms:

- Random Forest
- Boosting
- AdaBoost
- Weighted Average (Blending)
- Gradient Boosting Machines (GBM)

## Algorithms to reduce dimensionality  

The reduction of dimensionality specify various techniques for reducing the number of input variables in training data. The higher the number of variables or features, the harder the model is to learn. 
Clustering follows the same approach, but dimensionality reduction follows a strict unsupervised learning method.

Here are some examples of dimensionality reduction algorithms:

- Kernel PCA (KPCA)
- Singular Value Decomposition (SVD)
- Non-negative Matrix Factorization (NMF)
- Manifold learning
- Linear Discriminant Analysis (LDA)

## Remarks

This list does not claim to be complete, there are many algorithms excluded, for example those that are important in some subfields of machine learning. Like Natural Language Processing (NLP), Computer Vision (CV), Reinforced Learning and many more.

# How to approach a machine learning problem

There are five major steps involved on how to approach a machine learning problem [Brow14]. They are being discussed below.

## 1. Define the Problem

In this phase one tires to understand the problem in holistic way. 
This can be split into three questions.

### 1. What is the problem?

Here the problem is described, to further understand it. List assumptions and similar problems.

### 2. Why this problem needs to be solved?

This question includes advantages one gain from solving the problem. It is a motivation to think about benefits a solution provides.

### 3. How would one solve the problem? 

Try to understand how the problem would be solved manually, to get insights in this domain.

## 2. Prepare Data 

In that phase one tries to understand the data, for that some scatter plots or histograms are useful.

### 1. Data Selection

In data selection it is being examined what data is available, what data is missing and what is redundant or simply not needed. The relevant training examples are then chosen. 

### 2. Data Preprocessing

Data preprocessing tries to organize the selected data by formatting, cleaning and sampling.

### 3. Data Transformation

Data transformation involves engineering features by scaling, attribute aggregation and attribute decomposition. 

## 3. Spot Check Algorithms

Spot check algorithms means to compare different approaches solving the problem. There are some low code frameworks that let you compare different algorithms. They train different models on a given dataset. Afterwards they can compared according to different metrics.

After a first spot check the most promising algorithms can be chosen. Afterwards parameters can be refined to make them even more effective in solving the problem, but this is part of the next step.

## 4. Improve Results

### 1. Algorithm Tuning: 

In this process the hyperparameter of the model architecture are changed (in a specific range) and the model is trained in various combinations. The best model can be chosen afterwards.

### 2. Ensemble Methods:

Like stated before, there can be a combination of different machine learning models to give the best results. So, it should be considered to combine different approaches, if this is feasible.

### 3. Extreme Feature Engineering

In extreme feature engineering the attribute decomposition and aggregation seen in data preparation is being used to make the training data more explicit. It involves transforming data to forms that better relate to the learning targets. It can augment the value of your data and improves the overall performance of your model. It involves techniques like:

- **Imputation**: handling the missing values in data
- **Discretization**: grouping sets of values together in some logical fashion into buckets or bins
- **Categorical encoding**: encode categorical values into numerical features -> simpler to learn
- **Feature splitting**: splitting features into parts can improve the value of features
- **Handling outliers**: outliers are unusually high or low values in a dataset, there are some options: 
  - removal
  - replacing
  - capping 
  - discretization 
- **Variable transformations**: could help normalizing skewed data, e.g. logarithmic transformation
- **Scaling**: scaling inputs of data can improve your model, here values are normalized, this can be achieved differently
  - Variance scaling. data points are subtracted by their mean, the result is divided by the distribution variance, this gives a distribution with 0 mean and a variance of 1
  - Min-Max scaling: rescaling the values in a range from 0 to 1
- **Create features**: deriving new features from existing ones, done by simple mathematical operations like: mean, median, difference, sum, mode or a product of two values

## 5. Present Results

It is always good to summarize findings, to remember them and use them in future. In order to do so, they can be grouped into: **context, problem, solution, findings, limitations and conclusions**.

# Sources

[Brow14] Jason Brownlee, "Applied Machine Learning Process" https://machinelearningmastery.com/process-for-working-through-machine-learning-problems/ Version 2019