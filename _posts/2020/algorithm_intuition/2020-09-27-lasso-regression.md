---
title: Lasso Regression  (L1 Regularization) - Algorithm Intuition
author: Arjun Mota
date: 2020-09-27 15:45:00 +0530
image: /assets/img/sample/lasso_regression_cover.png
social_card: /assets/img/social_card/lasso_regression.png
summary: Lasso regression algorithm explanation and formulas used in development.
categories: [Artificial Intelligence, Algorithm Intuition]
tags: [regression, machine-learning, supervised-machine-learning]
math: true
toc: true
---

## Background

### Brief

Lasso regression is also known as L1 regularization and LASSO stands for <b>L</b>east <b>A</b>bsolute <b>S</b>hrinkage and <b>S</b>election <b>O</b>perator. It is a regularized version of linear regression that adds l1 penalty terms in the cost function and thereby reducing coefficients to absolute zero and eliminating their impact to a model. Let's understand it better with it's cost function.

As this is regularized version of a linear regression, so check out Linear regression here: <a href="/posts/linear-regression/">Linear Regression</a>.

## Intuition

Because it is a regularized version of linear regression, so I would not be covering all the similar details. I would suggest you go through linear regression first and consider all the calculations till cost function and rest are mentioned here for lasso regression. We will directly look at where it differs from the linear regression.<br/>

## Math Behind

Following is the cost function of lasso regression:

### Cost Function > Lasso Regression

<span class="centered_equation">
\$\$
\operatorname{J}(\boldsymbol{\theta}) = \operatorname{MSE}(\boldsymbol{\theta})  + \alpha\sum _{j=1}^{m} \left|w _{j} \right|
\$\$
</span>

where,<br/>

<span class="centered_equation">
\$\$
w_{j} =\begin{cases}
-1 & \text { if } w _{j} < 0 \\ \cr
\ \ \ 0 & \text { if } w _{j} = 0 \\ \cr
+1 & \text { if } w _{j} > 0
\end{cases}
\$\$
</span>

here in the first equation, <br/>
<span class="equation_variables">m</span> = number of features,<br/>
<span class="equation_variables">\\( \operatorname{MSE}(\boldsymbol{\theta}) \\)</span> = gradient vector explained here in batch gradient descent <a href="/posts/batch-gradient-descent/#math-behind">Partial Derivative of a Cost Function</a><br/>
<span class="inline_equation">\\( \alpha \\)</span> = (alpha) constant model parameter for how much l1 penalty we want to give to our feature,<br/>
<span class="equation_variables">w</span> = weight of a feature.<br/>
as mentioned second mathematical information for weights <span class="inline_equation">\\( w_{j} \\)</span>, absolute values will be considered for weights. 0 weight remain 0 and less than 0 will become -1 and greater than 0 will become 1.<br/>


### Cost Function > Explanation

⦿ As stated in the equation above, <span class="equation_variables">\\( \operatorname{MSE}(\boldsymbol{\theta}) \\)</span> is a partial derivative of a cost function from a gradient descent.<br/>
⦿ In the L1 penalty calculation, weights are taken as absolute values before the multiplication of sum of all the weights with model parameter alpha.<br/>

⦿ Looking at second mathematical information <span class="inline_equation">\\( w_{j} \\)</span>, we can see how weights are transformed between -1, 0 and 1.<br/>

⦿ At the time of multiplication of summation of weights with alpha, -1 will reduce coefficient, 0 will not affect whereas 1 will increase the coefficient value.<br/>

⦿ Old weights will be updated by a newly identified <span class="equation_variables">\\( \theta  \\)</span> value along with a learning rate as mentioned in a <a href="/posts/batch-gradient-descent/">batch gradient descent.</a>

⦿ This new weights will be used for new predictions and this entire process will be continued until an error stop reducing.

⦿ Based on this weights and the L1 penalty calculation, we can say that Lasso regression is eliminating the impact of features which are least important to dependent variable/feature by setting them to 0 and -1 accordingly.<br/>

⦿ That way it also performs feature selection implicitly.<br/>


### Lasso Regression > Things to Remember

⦿ It is crucial to scale (e.g. StandardScaler) input features because regression models are sensitive to them. <br/>

⦿ Another thing to remember is that in the above equation, alpha is the parameter that we will give to our model while developing, so it has to be chosen wisely.<br/>

⦿ Small alpha will give better results as it will change the coefficient by a small margin, unlike large alpha. The larger alpha value can lead to the under-fitting of a model, so you should experiment with different alpha values. The wisely chosen alpha value will prevent a model from over-fitting.<br/>

⦿ Transforming our input features with a polynomial method and then applying lasso regression also proved to be making a great model.<br/>

Check out how to transform features to polynomial and perform polynomial regression here: <a href="/posts/polynomial-regression">Polynomial Regression</a><br/>


### Prediction

After doing this computation, we will get new coefficients/weights that we can use to predict with the following formula:<br/>

<span class="centered_equation">
\$\$
y = x * \boldsymbol{\theta}
\$\$
</span>

Where x is our input variables matrix as mentioned below and <span class="equation_variables">\\( \boldsymbol{\theta} \\)</span> is the lasso regression coefficients/weights  calculated earlier with a bias matrix <span class="equation_variables">\\( \boldsymbol{\theta_{0}} \\)</span>.<br/>

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

This is where lasso regression overcame problems of ridge regression by making negative weights to -1 and keeping weight 0 to 0. By adding the L1 penalty to cost function with alpha multiplied with sum of all absolute value of weights give us better coefficients that result in a regression line better than ridge regression.<br/>

## Conclusion

Lasso regression has improvement in weights calculation. It emphasises important features from others more and eliminates impact of least important features and that is why it is called as <b>L</b>east <b>A</b>bsolute <b>S</b>hrinkage and <b>S</b>election <b>O</b>perator.<br/>

Evaluation metrics are the same as linear regression. You can use <a href="/posts/mean-squared-error/">MSE</a>, <a href="/posts/root-mean-squared-error/">RMSE</a>, <a href="/posts/mean-absolute-error/">MAE</a>, etc, whichever suits your usecase.<br/>

Check out evaluation metrics here: <a href="/categories/evaluation-metrics/">Evaluation Metrics</a><br/>

Keep this in mind that when we transform input features into polynomials, they will become highly correlated. In that case, lasso regression will give higher coefficients.<br/>

It is useful in high dimensional data as it deals with feature selection and correlation of them.<br/>

Though, there is another good regression algorithm <a href="/posts/elastic-net-regression/">Elastic Net Regression</a>, which is a combination of both ridge and lasso regression.<br/>

If you want to know more about a batch gradient descent then check: <a href="/posts/batch-gradient-descent/">Batch Gradient Descent</a> <br/>
For a ridge regression check this: <a href="/posts/ridge-regression/">Ridge Regression (L2 Regularization)</a><br/><br/>

## End Quote

> "Artificial Intelligence is the new electricity." <b> - Andrew NG</b>