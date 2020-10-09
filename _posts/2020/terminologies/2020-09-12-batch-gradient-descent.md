---
title: Batch Gradient Descent - Terminologies
author: Arjun Mota
date: 2020-09-12 13:19:00 +0530
image: /assets/img/sample/batch_gradient_descent_cover.png
social_card: /assets/img/social_card/batch_gradient_descent.png
summary: Batch Gradient descent is an algorithm for the optimization of a model to reduce a prediction error. This article contains the definition of a batch gradient descent and detailed explanation with pseudocode, formulas and diagrams.
categories: [Artificial Intelligence, Terminologies]
tags: [batch-gradient-descent, gradient-descent-types, machine-learning-glossary, machine-learning]
math: true
toc: true
---

## Background

Batch gradient descent is one of the types of optimization algorithms from the gradient descent family. It is widely used in machine learning and deep learning algorithms for optimizing a model for better prediction. To understand this algorithm, you should have some understanding of differential equations to find a gradient of the cost function.<br/>

### Definition

The batch gradient descent algorithm calculates a gradient of the cost function for all the independent parameters (input data) passed to a model. Now, computed gradient value along with the learning rate passed to a model will be used to update the existing weights of the model. This way weights will be updated until the error in prediction is reduced to a minimum so that prediction will happen with a minimum error. The gradient is the value that tells us how much cost function changes when any feature weight is changed. It is also called a partial derivative in mathematical terms.<br/>

### In Brief

In simple terms, while reducing an error through cost function, batch gradient descent helps us to teach our model a direction where an error reduces. By using that direction, our model will be able to find weights that will be used in more accurate predictions.<br/>

Because it calculates a gradient for a batch of all values at once, it is called a batch gradient descent.<br/>

Let's go ahead and understand how the batch gradient descent works.

## Diagram

### Batch Gradient Descent Direction Diagram

<img src="/assets/img/sample/batch_gradient_descent_direction_diagram.png" alt="Batch Gradient Descent Direction Diagram"><br/>

### Batch Gradient Descent Convergence Diagram

<img src="/assets/img/sample/batch_gradient_descent_convergence_diagram.png" alt="Batch Gradient Descent Convergence Diagram">

### Diagram > Explanation

•   As we can see, weight changes the overall error in a prediction.<br/>
•   We start with random weights and then optimize it to reduce an error through a batch gradient descent .<br/>
•   In the diagram above, our algorithm moves from the left and right side of a curve while dealing with different weights.<br/>
•   Using learning rate model parameter new weights will get assigned to features and the model reacts to those weights in terms of change in an error.<br/>
•   Our goal is to find weights with minimum error, as the new weights are calculated our model goes down to reach the bottom which is the place for minimum error. Going downward is an ideal situation but it is not always true if the learning rate and our input data is not properly cleaned and scaled respectively.<br/>
•   Learning rate is a very important parameter to reach a bottom efficiently. You will understand more once we will discuss the learning rate further.<br/><br/>

Just keep this pseudocode in mind for further explanation.<br/>

## Pseudocode > Batch Gradient Descent

```terminal
Steps:
    1. Initialize random feature weights.
    2. Calculate the gradient for all records.
    3. Adjust feature weights by calculating new weights.
    4. Use new weights for prediction and calculate an error.
    5. Repeat steps 2, 3, and 4 for adjusting feature weights and
       do it until an error no longer reduces or reached some iterations limit.
```

## Math Behind

To find a gradient, we need to calculate a partial derivative of a cost function. Below is the formula for a partial derivative of a cost function for a single feature:<br/>

### Partial Derivative of a Single Feature > Formula

<span class="centered_equation">
\$\$
\frac{\partial}{\partial \theta_{j}} \operatorname{MSE}(\boldsymbol{\theta})=\frac{2}{n} \sum_{i=1}^{n}\left(\boldsymbol{\theta}^{T} \mathbf{x}^{(i)}-y^{(i)}\right) x_{j}^{(i)}
\$\$
</span>

where, <span class="inline_equation">\\( \frac{\partial}{\partial \theta_{j}} \operatorname{MSE}(\boldsymbol{\theta}) \\)</span> = partial derivative of a cost function with regards to the parameter <span class="equation_variables">\\( \theta_{j} \\)</span>. <span class="equation_variables">\\( \theta_{j} \\)</span> is a weight of a feature.<br/>
<span class="inline_equation">\\( \boldsymbol{n} \\)</span> = number of records or input data's length<br/>
<span class="inline_equation">\\( \boldsymbol{\theta}^{T} \\)</span> = transpose of a weight theta<br/>
<span class="inline_equation">\\(  \mathbf{x}^{(i)} \\)</span> = feature value from an input vector<br/>
<span class="inline_equation">\\(  y^{(i)} \\)</span> = actual value of dependent variable from an input vector<br/>
<span class="inline_equation">\\(  x_{j}^{(i)} \\)</span> = feature value from an input vector (for single feature it is same as \\(  x^{(i)} \\) or we can say it is jth feature value from ith input vector)<br/>

The above formula is just to remember to know how a partial derivative is calculated, but we want to calculate a partial derivative for more than one feature. Hence following formula is used to compute a partial derivative of all in one go.<br/>

### Partial Derivative of a Multiple Features > Formula

<span class="centered_equation">
\$\$
\nabla_{\boldsymbol{\theta}} \operatorname{MSE}(\boldsymbol{\theta})=\left(\begin{array}{c}
\frac{\partial}{\partial \theta_{0}} \operatorname{MSE}(\boldsymbol{\theta}) \\cr
\frac{\partial}{\partial \theta_{1}} \operatorname{MSE}(\boldsymbol{\theta}) \\cr
\vdots \\cr
\frac{\partial}{\partial \theta_{n}} \operatorname{MSE}(\boldsymbol{\theta})
\end{array}\right)
\$\$
</span>
is then become the following short formula:<br/>
<span class="centered_equation">
\$\$
\nabla_{\boldsymbol{\theta}} \operatorname{MSE}(\boldsymbol{\theta})=\frac{2}{n} \mathbf{X}^{T}(\mathbf{X} \boldsymbol{\theta}-\mathbf{y})
\$\$
</span>

I assume that you already understood the first  formula from above two formulas, so just want to add to the first one that <span class="inline_equation">\\(  \theta_{0}\ to \ \theta_{n} \\)</span> indicates weights of multiple features from 0 to n. But as you can see we have new formula for computing all. Where, <br/>

<span class="inline_equation">\\(  \nabla_{\boldsymbol{\theta}} \operatorname{MSE}(\boldsymbol{\theta}) \\)</span> = (nabla) inverted triangle symbol indicates a gradient vector of partial derivatives of the cost function<br/>
<span class="equation_variables">n</span> = number of records or input data's length<br/>
<span class="inline_equation">\\(  \mathbf{X} \\)</span> =  input data matrix<br/>
<span class="inline_equation">\\(  \mathbf{X}^{T} \\)</span> = transpose matrix of an input<br/>
<span class="inline_equation">\\(  \theta \\)</span> = weights of all the features<br/>
<span class="equation_variables">y</span> = actual values of a dependent variable from an input<br/>

## Explanation > Batch Gradient Descent

### Partial Derivative of a Single Feature

•	In the first formula, we are taking a transpose of a theta weight that is in one feature doesn't change and multiplying it with input feature x to get a prediction.<br/>
•	Then subtracting a prediction with actual value to get an error.<br/>
•	Multiplying this error with the input value of a feature mentioned as <span class="equation_variables">\\(  x_{j}^{(i)} \\)</span>.<br/>
•	We will do this for all input records and take a sum of it.<br/>
•	That sum will be multiplied with a result of <span class="equation_variables">\\(  \frac{2}{n} \\)</span> where n is the number of records.<br/>
•	This entire calculation will give us a partial derivative of a cost function for a single feature.<br/>
•	But in real-life situations, we rarely have to deal with a single feature, hence the formula mentioned after that is for multivariable partial deviation.<br/><br/>

Remember that this formula is not a batch gradient descent. The gradient vector that we got from the calculations so far will be used in updating existing feature weights that we will see in a moment, but before that let's understand how we can calculate a partial derivative of a cost function for multiple features. 

### Partial Derivative of a Multiple Features

•	There are two formulas mentioned, but we have to deal with the second one only as the first formula is just an explanation for multiple partial derivative calculations derived from a single feature formula.<br/>
•	Now, coming to the second formula where we are taking a transpose of an input x and multiplying with <span class="equation_variables">\\(  \frac{2}{n} \\)</span>.<br/>
•	Inside the braces, we are multiplying all the input values x with their weights <span class="equation_variables">\\(  \theta \\)</span> and subtracting it by actual values in y (dependent variable).<br/>
•	After that multiplying both the values, we will get a partial derivative of a cost function for all records.<br/>

Alright, now we will see how the weights are updated after finding a partial derivative.<br/>

### New Feature Weights > Updating Weights

•	Till this point, we have our gradient vector in <span class="equation_variables">\\(  \nabla_{\boldsymbol{\theta}} \operatorname{MSE}(\boldsymbol{\theta}) \\)</span>, and feature weights in <span class="equation_variables">\\(  \theta \\)</span>.<br/>
•	There is also one model parameter called a learning rate (lr), it is a floating-point value used for weight updates.<br/>
•	So, now we will use the following formula to get new weights for our model:<br>

<span class="centered_equation">
\$\$
\boldsymbol{\theta}^{(\text {new weights})}=\boldsymbol{\theta}^{(\text {old weights})}-lr *  \nabla_{\boldsymbol{\theta}} \operatorname{MSE}(\boldsymbol{\theta})
\$\$
</span>

•   We will multiply gradient vector with learning rate and subtract it from old weights to get new weights.<br/>
•   Once the new weights are calculated, again the entire process will be repeated until the model finds optimum values for the weights that give a minimum error in a prediction.<br/>
•   Larger learning rate will make this algorithm take more time to reach the bottom as it may skip the minimum value at the bottom and move to another side.<br/>
•   The learning rate decides the magnitude of a change in weights, if it is large then weights will be updated by a large margin and vice versa. So it has to be chosen properly by experimentation and evaluation.<br/>

That's it for the batch gradient descent, we are at the end of this optimization algorithm.<br/>

## Diagram > Batch Gradient Descent Minima Diagram

<img src="/assets/img/sample/batch_gradient_descent_minima_diagram.png" alt="Batch Gradient Descent Minima Diagram">

### Diagram > Explanation

•   With comparison to the first diagram, we can see a local and a global minima here.<br/>
•   Direction of a model to reach a minimum error state is also not straightaway downhill instead there are different ups and downs present in this scenario.<br/>
•   Local minima is a state in a gradient descent where a model considers that it reached the minimum error and stop going further.<br/>
•   Global minima is an actual state where error goes to a minimum and ideally, a model should identify that.<br/>
•   However, by using a batch gradient descent we are calculating gradient for all records at once and if the cost function is irregular then we will have one or more local minima and one global minima.<br/>
•   In that case, a batch gradient descent will take a long time to reach the global minima or may never reach if the learning rate is not suited and an input data is not scaled properly.<br/>

## Conclusion

As mentioned above, the problem with a batch gradient descent is that it will take a long time when a cost function is irregular. To overcome this issue, a stochastic gradient descent is introduced that calculates a gradient for a specific amount of records at each time.<br/><br/>
The stochastic gradient descent is better at finding a global minima than a batch gradient descent.<br/>
Overall a batch gradient descent is an optimization algorithm that changed the way machine learning works and helped achieving greater results.<br/><br/>
In modern machine learning frameworks, there are different variants of gradient descents based on new researches.<br/>
Though, it is very unlikely that you have to implement this algorithm from scratch as frameworks used in a model development have already implemented it.<br/>
So, you just have to pass some parameters and wait for it to do the magic!<br/><br/>

## End Quote

>"A breakthrough in machine learning would be worth ten Microsofts." <b>- Bill Gates</b>