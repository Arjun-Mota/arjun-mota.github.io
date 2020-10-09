---
title: Mini-Batch Gradient Descent - Terminologies
author: Arjun Mota
date: 2020-10-09 17:53:00 +0530
image: /assets/img/sample/mini_batch_gradient_descent_cover.png
social_card: /assets/img/social_card/mini_batch_gradient_descent.png
summary: Mini-batch gradient descent is an optimization algorithm that is used to reduce an error in a model through the identification of proper weights. This article contains the definition of mini-batch gradient descent and a detailed explanation with pseudocode.
categories: [Artificial Intelligence, Terminologies]
tags: [mini-batch-gradient-descent, gradient-descent-types, machine-learning-glossary, machine-learning]
toc: true
---

## Background

Mini-batch gradient descent is another algorithm from the gradient descent family. It is a mix of batch and stochastic gradient descent and that way It has the best of both worlds. To understand mini-batch gradient descent, you must understand batch and stochastic gradient descent algorithms first. So, before going further with an explanation, I would recommend you to go through <a href="/posts/batch-gradient-descent/">batch gradient descent</a> and <a href="/posts/stochastic-gradient-descent/">stochastic gradient descent.</a>

## Definition

In mini-batch gradient descent instead of calculating gradient for all data points in each epoch like batch gradient descent or taking a random number of data points in each epoch like stochastic gradient descent here, we take a fixed number of data points called mini-batches in each epoch. The number of data points will be fixed in each epoch and considerably smaller than stochastic gradient descent.<br/>

By using a smaller number of data points in each epoch, mini-batch gradient descent can utilize hardware better than the other two gradient descent algorithms.<br/>

Just like stochastic gradient descent, mini-batch gradient descent also has two variants. But before knowing those variants, understand the following pseudocode for mini-batch gradient descent.

## Pseudocode

```terminal
Steps:
    1. Initialize random feature weights, batch size, epoch size.
    2. For each epoch
        2.1 For each batch from batch size
        2.2 Select random records from the training data.
        2.2 Calculate the gradient for selected batch of records.
        2.3 Adjust feature weights by calculating new weights.
        2.4 Use new weights for prediction and calculate an error again.
```
## Explanation

•   Mini-batch starts with random feature weights, the fixed batch size for a certain number of epochs.<br/>
•   For each epoch, we will have a certain number of mini-batches to draw from the training data.<br/>
•   For each batch, we will select random records from the training data and use them to calculate the gradient and update weights.<br/>
•   After updating weights for a predefined number of batches, we will again go for another epoch.<br/>
•   This way mini-batch gradient descent updates model more than stochastic and batch gradient descent with less memory usage.<br/>
•   Because of that it gives mini-batch gradient descent the efficiency of batch gradient descent and robustness of stochastic gradient descent.<br/>

## Variants

### First

```terminal
Steps:
    1. Initialize random feature weights, batch size, epoch size.
    2. For each epoch
        2.1 For each batch from batch size
            2.1.1 Select random records from the training data with replacement.
            2.1.2 Calculate the gradient for selected batch of records.
            2.1.3 Adjust feature weights by calculating new weights.
        2.2. Use new weights for prediction and calculate an error again.
```

For each epoch, the number of mini-batches will be drawn and used for weight updates.

## Second

```terminal
Steps:
    1. Initialize random feature weights, batch size, epoch size.
    2. For each epoch
        2.1 Shuffle training data
        2.2 For each batch from batch size
            2.2.1 Select random records from the training data with replacement.
            2.2.2 Calculate the gradient for selected batch of records.
            2.2.3 Adjust feature weights by calculating new weights.
        2.3. Use new weights for prediction and calculate an error again.
```

The only difference in this variant is the shuffling operation where each epoch training data will be shuffled to reduce redundancy.

## Conclusion

•   Main purpose of mini-batch gradient descent is to utilize hardware (GPU) for model training.<br/>
•   With mini-batches to process each time, training a model will be memory efficient.<br/>
•   Mini-batch gradient descent is also useful in the training model on a large dataset.<br/>
•   It is essential for mini-batch gradient descent to have a good learning schedule to reach global minima otherwise it will walk around local minima.<br/><br/>

Check out other gradient descent algorithms:<br/><br/>
<a href="/posts/batch-gradient-descent/">Batch Gradient Descent</a><br/>
<a href="/posts/stochastic-gradient-descent/">Stochastic Gradient Descent.</a><br/><br/>

## End Quote

>  I know that I am intelligent, because I know that I know nothing. <b>- Socrates</b>