---
title: Elastic Net Regression - Algorithm Intuition
author: Arjun Mota
date: 2020-10-01 14:30:00 +0530
image: /assets/img/sample/elastic_net_regression_cover.png
social_card: /assets/img/social_card/elastic_net_regression.png
summary: Elastic net regression algorithm explanation and formulas used in development.
categories: [Artificial Intelligence, Algorithm Intuition]
tags: [regression, machine-learning, supervised-machine-learning]
math: true
toc: true
---

## Background

### Brief

Elastic Net Regression is an algorithm that overcame the limitations of both ridge and lasso regression by incorporating both of them. Yes, you read this right it is a combination of ridge and lasso regression. That is the reason it is preferred over the latter two algorithms. It is also a regularized version of linear regression, so I would be skipping all the similar explanations. I would recommend you to understand <a href="/posts/linear-regression/">Linear Regression</a> first and then continue this article, so that you can understand elastic net regression properly. Let's understand the math behind this algorithm.

## Math Behind

The cost function of an elastic net regression consists of both l1 and l2 penalties. Following is the cost function of an elastic net regression.

### Cost Function > Elastic Net Regression

<span class="centered_equation">
\$\$
\operatorname{J}(\theta) = \operatorname{MSE}(\theta)  + r \alpha  \sum\_{j=1}^{n}\left|\theta\_{j}\right|+\frac{1-r}{2} \alpha \sum_{k=1}^{n} \left(\theta_{k}\right)^{2}
\$\$
</span>

Where, <span class="equation_variables">\\( \operatorname{MSE}(\boldsymbol{\theta}) \\)</span> = gradient vector explained here in batch gradient descent <a href="/posts/batch-gradient-descent/#math-behind">Partial Derivative of a Cost Function</a><br/>
<span class="equation_variables">r</span> = floating-point value of a mix ratio of ridge and lasso regression given between 0 to 1, where 0 is equivalent to the ridge regression and 1 is equivalent to the lasso regression.<br/>
<span class="equation_variables">\\( \alpha \\)</span> = (alpha) penalty constant parameter given to a model.<br/>
<span class="equation_variables">n</span> = number of features, remember it starts from 1 because a bias value is kept at 0th position.<br/>
<span class="equation_variables">\\( \theta_{j} \\) and \\( \theta_{k} \\)</span> = are weights corresponding to a feature.<br/>
<span class="equation_variables">|...|</span> = for taking an absolute value as used in a lasso regression.<br/>
At the end, weight is squared as used in a ridge regression.<br/>

### Cost Function > Explanation

⦿ As stated in the equation above, <span class="equation_variables">\\( \operatorname{MSE}(\boldsymbol{\theta}) \\)</span> is a partial derivative of a cost function from a gradient descent.<br/>

⦿ Mix ratio r is multiplied with a L1 penalty term of lasso regression.<br/>

⦿ At last, L2 penalty term of a ridge regression is multiplied with <span class="equation_variables">\\( \frac{1-r}{2} \\)</span>.<br/>

⦿ This calculation will give us a cost value that will be used in updating existing weights of features as mentioned in a <a href="/posts/batch-gradient-descent/#new-feature-weights--updating-weights">batch gradient descent > updating weights.</a><br/>

⦿ Have you noticed that if we give a mix ratio r=0 then it will be completely a ridge regression and r=1 will be a lasso regression.<br/>

⦿ Do not forget to scale the input data as this regularization algorithm is also very sensitive to scale like others.<br/>

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

## Conclusion

⦿ Elastic Net Regression is a middle state between a ridge and a lasso regression algorithms hence it manages to deal with limitations of both pretty well.<br/>

⦿ Plain linear regression without any regularization is not advised to use instead regularized models like ridge, lasso and elastic net should be used.<br/>

⦿ When the number of features is high then lasso and elastic net regression should be used as they minimize the impact of useless features.<br/>

⦿ Though elastic net regression performs better than lasso regression when the number of features is more than training records or some of the features are strongly correlated.<br/><br/>

For more information, check the following articles on different topics mentioned in this article:<br/>

<a href="/posts/batch-gradient-descent/">Batch Gradient Descent</a><br/>
<a href="/posts/linear-regression/">Linear Regression</a><br/>
<a href="/posts/ridge-regression/">Ridge Regression (L2 Regularization)</a><br/>
<a href="/posts/lasso-regression/">Lasso Regression (L1 Regularization)</a><br/><br/>

## End Quote

>  "Machine Learning is going to result in a real revolution." <b>- Greg Papadopoulos</b>