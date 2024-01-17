---
title: Stochastic Gradient Descent - Terminologies
author: Arjun Mota
date: 2020-10-05 15:47:00 +0530
image: /assets/img/sample/stochastic_gradient_descent_cover.png
social_card: /assets/img/social_card/stochastic_gradient_descent.png
summary: Stochastic gradient descent is an optimization algorithm that is used to reduce an error in a model through the identification of proper weights. This article contains the definition of stochastic gradient descent and a detailed explanation with pseudocode.
categories: [Artificial Intelligence, Terminologies]
tags: [stochastic-gradient-descent, gradient-descent-types, machine-learning-glossary, machine-learning]
toc: true
---

## Background

Stochastic gradient descent is an optimization algorithm from the gradient descent family that is better than batch gradient descent in finding proper feature weights. It is extensively used in various use-cases in machine learning. Before going further with an explanation, I would recommend you to go through <a href="/posts/batch-gradient-descent/">batch gradient descent</a> as it is the base for understanding any other gradient descent algorithm.

## Definition

In the batch gradient descent, we were calculating gradient for all data points in each iteration whereas in stochastic gradient descent (SGD), the gradient will be computed on random samples from training data in each iteration (epoch). Keep in mind the following pseudocode for understanding this algorithm.

## Pseudocode

```terminal
Steps:
    1. Initialize random feature weights.
    2. Calculate the gradient for randomly selected records from the training data.
    3. Adjust feature weights by calculating new weights.
    4. Use new weights for prediction and calculate an error.
    5. Repeat steps 2, 3, and 4 for adjusting feature weights and
       do it until an error no longer reduces or reached some iterations limit.
```

## Explanation

•   Just like batch gradient descent, here we will start with the random initialization of weights.<br/>
•   Then randomly select some data points from training data.<br/>
•   Calculate gradient and find new weights and update existing feature weights.<br/>
•   This entire process will be repeated until an error no longer reduces or reached some iterations limit.<br/>
•   There is a possibility that some of the samples will be randomly selected multiple times, for that matter, there are other variants of the stochastic gradient descent that takes care of this is explained below.<br/>

It is as simple as that and slightly different from the batch gradient descent. Rest of all the operations works as same as <a href="/posts/batch-gradient-descent/">batch gradient descent (BGD)</a>. Keep in mind that the above pseudocode is just a common set of operations behind the algorithm.<br/>

So, let us look at what are all the variants of the stochastic gradient descent available for us.

## Variants

### First

```terminal
Steps:
    1. Initialize random feature weights.
    2. Randomly shuffle data points in the training data.
    3. Calculate the gradient for randomly selected records with
    replacement from the training data.
    4. Adjust feature weights by calculating new weights.
    5. Use new weights for prediction and calculate an error.
    6. Repeat steps 3, 4, and 5 for adjusting feature weights and
       do it until an error no longer reduces or reached
       some iterations limit.
```

Entire training data will be shuffled only once in the beginning and samples will be selected with replacement means currently selected data points will be available for the next selection.

### Second

```terminal
Steps:
    1. Initialize random feature weights.
    2. Calculate the gradient for randomly selected records with
    replacement from the training data.
    3. Randomly shuffle data points in the training data.
    4. Adjust feature weights by calculating new weights.
    5. Use new weights for prediction and calculate an error.
    6. Repeat steps 2, 3, 4, and 5 for adjusting feature weights and
       do it until an error no longer reduces or reached
       some iterations limit.
```

Here the difference is that training data points will be shuffled in every iteration (epoch), so that chances of getting the same sample will be reduced.

## Diagram > Batch Gradient Descent Minima Diagram

I am keeping this diagram from the batch gradient descent for the understanding of the references of local and global minima throughout this article.<br/>

<img src="/assets/img/sample/batch_gradient_descent_minima_diagram.png" alt="Batch Gradient Descent Minima Diagram">

## Stochastic Gradient Descent > Things To Remember

•   Since it is using random samples, it is proved to identify global minima better than batch gradient descent.<br/>
•   Using SGD, training a huge dataset is possible as only one sample of training data will remain in memory at a time.<br/>
•   Since we are using random samples so cost function will be jumping more compare to batch gradient descent.<br/>
•   In case of an irregular cost function, SGD will be useful to get out of local minima.<br/>
•   Because of the random nature of SGD, stopping at minimum is difficult, therefore a concept called learning rate schedule is used.<br/>
•   In the learning rate schedule, the learning rate will be changed during a training period so that SGD will be able to stop at global minima.<br/>
•   If the learning rate is changed too fast then SGD may get stuck at the local minima and if the learning rate is changed too slowly then SGD will take a longer time to reach the minima or may never reach.

## Conclusion

•   Stochastic gradient descent is a better option than batch gradient descent in terms of memory and performance.<br/>
•   Though, random samples used in SGD still not able to utilize hardware properly that is the reason <a href="/posts/mini-batch-gradient-descent/">Mini-batch Gradient Descent</a> exists.<br/><br/>

## End Quote

> "A gradient measures how much the output of a function changes if you change the inputs a little bit."  <b>-  Lex Fridman (MIT)</b>