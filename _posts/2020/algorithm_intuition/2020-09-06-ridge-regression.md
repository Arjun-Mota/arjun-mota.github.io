---
title: Ridge Regression (L2 Regularization) - Algorithm Intuition
author: Arjun Mota
date: 2020-09-06 17:40:00 +0530
image: /assets/img/sample/ridge_regression_cover.png
social_card: /assets/img/social_card/ridge_regression.png
summary: Ridge regression algorithm explanation and formulas used in development.
categories: [Artificial Intelligence, Algorithm Intuition]
tags: [regression, machine-learning, supervised-machine-learning]
math: true
toc: true
---

## Background

### Brief

Ridge regression is also known as L2 regularization and Tikhonov regularization. It is a regularized version of linear regression to find a better fitting line. It adds l2 penalty terms in the cost function and thereby reducing coefficients lower towards zero and minimizing their impact on the training data. It is useful to avoid over-fitting of the data in a model. The alpha parameter of a model is used to calculate cost function to manage bias-variance tradeoff and reduce an error in prediction.

As this is regularized version of a linear regression, so check out Linear regression here: <a href="/posts/linear-regression/">Linear Regression</a>.

## Intuition

As it is a regularized version of linear regression, so I would not be covering all the similar details. I would suggest you go through linear regression first and consider all the calculations till cost function and rest are mentioned here for ridge regression. We will directly look at where it differs from the linear regression.<br/>

Ridge regression has a slightly different cost function than the linear regression. Let's understand it.

## Math Behind

We can perform the ridge regression either by closed-form equation or gradient descent. As the popular sklearn library uses a closed-form equation, so we will discuss the same.

### Cost Function > Ridge Regression

Here is the closed-form equation:<br/>

<span class="centered_equation">
\$\$
\widehat{\boldsymbol{\theta}}=\left(\mathbf{x}^{T} \mathbf{x}+\alpha \mathbf{A}\right)^{-1} \mathbf{x}^{T} \mathbf{y}
\$\$
</span>

In the above equation, <span class="inline_equation">\\( \widehat{\boldsymbol{\theta}} \\)</span> = (theta hat) symbol used for ridge regression coefficients,<br/>
<span class="equation_variables">x</span> = matrix of our input variables as mentioned in the linear regression and also mentioned in the prediction section below,<br/>
<span class="inline_equation">\\( \mathbf{x}^{T} \\)</span>= transpose of a matrix x,<br/>
<span class="inline_equation">\\( \alpha \\)</span> = alpha model parameter constant value for how much l2 penalty we want to give to our feature,<br/>
<span class="equation_variables">A</span> = identity matrix of (n+1) * (n+1) size where n is the number of records,<br/>
<span class="equation_variables">y</span> = dependent variable of our model.<br/>

### Ridge Regression > Things to Remember

Above equation is given by french mathematician André-Louis Cholesky, and that is why you need to pass "cholesky" as a solver parameter in the ridge regression implementation of python's sklearn library.<br/>

⦿ It is crucial to scale (e.g. StandardScaler) input features because regression models are sensitive to them. <br/>

⦿ Another thing to remember is that in the above equation, alpha is the parameter that we will give to our model while developing, so it has to be chosen wisely.<br/>

⦿ Small alpha will give better results as it will change the coefficient by a small margin, unlike large alpha. The larger alpha value can lead to the under-fitting of a model, so you should experiment with different alpha values. Wisely chosen alpha value will prevent a model from over-fitting.<br/>

⦿ Transforming our input features with a polynomial method and then applying ridge regression also proved to be making a great model.<br/>

Check out how to transform features to polynomial and perform polynomial regression here: <a href="/posts/polynomial-regression">Polynomial Regression</a><br/>

### Prediction

After doing this computation, we will get new coefficients that we can use to predict with the following formula:<br/>

<span class="centered_equation">
\$\$
y = x * \widehat{\boldsymbol{\theta}}
\$\$
</span>

Where x is our input variables matrix as mentioned below and <span class="equation_variables">\\( \widehat{\boldsymbol{\theta}} \\)</span> (theta hat) is the ridge regression coefficients calculated earlier with a bias matrix <span class="equation_variables">\\( \boldsymbol{\theta_{0}} \\)</span>.<br/>

<span class="centered_equation">
\$\$ x = \\pmatrix{
1 & x_{11} & x_{12} & \\ldots & x_{1k} \\cr
1 & x_{21} & x_{22} & \\ldots & x_{2k} \\cr
\\vdots & \\vdots & \\vdots & \\ldots & \vdots \\cr
\\vdots & \\vdots & \\vdots & \\ldots & \vdots \\cr
1 & x_{n1} & x_{n2} & \\ldots & x_{nk} \\cr
} \$\$
</span>

All the input records are present from second column onward in x as 1's in the first column are kept for taking a bias value from <span class="equation_variables">\\( \boldsymbol{\theta_{0}} \\)</span> because bias values will be multiplied with the first column. We have n records and k features/variables in this matrix.

This is the only difference in a ridge regression compare to linear regression. By adding a l2 penalty to cost function with alpha give us better coefficients that result in a regression line better than linear regression without regularization.<br/>

## Conclusion

Ridge regression is an improved version of linear regression. It differentiates important features from others.<br/>

Just to make it clear evaluation metrics are the same as linear regression. You can use <a href="/posts/mean-squared-error/">MSE</a>, <a href="/posts/root-mean-squared-error/">RMSE</a>, <a href="/posts/mean-absolute-error/">MAE</a>, etc, whichever suits your usecase.<br/>

Check out evaluation metrics here: <a href="/categories/evaluation-metrics/">Evaluation Metrics</a><br/>

As mentioned earlier, it moves coefficients towards 0 but does not make them 0. Because of that irrelevant features will hurt the model and this is a limitation that is prevented by fellow regularized algorithm <a href="/posts/lasso-regression/">Lasso regression.</a><br/><br/>

## End Quote

> Machine learning is the next internet. <b> - Tony Tether</b>