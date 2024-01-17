---
title: Logistic Regression - Algorithm Intuition
author: Arjun Mota
date: 2020-10-19 18:30:00 +0530
image: /assets/img/sample/logistic_regression_cover.png
social_card: /assets/img/social_card/logistic_regression.png
summary: Logistic regression algorithm explanation, use-cases, diagrams, and formulas used in development.
categories: [Artificial Intelligence, Algorithm Intuition]
tags: [classification, regression, machine-learning, supervised-machine-learning]
math: true
toc: true
---

## Background

### Brief

Logistic regression is one of the very first and popular algorithms for classification tasks. It is also a supervised machine learning algorithm meaning we need some actual outputs with input to learn from. Logistic regression is a probabilistic algorithm as it will give the final output based on the probability of a certain output from 0 to 1. Logistic regression uses a sigmoid function to do that.<br/>

Logistic regression has two major types: Binary Logistic Regression and Multinomial Logistic Regression. We will look at all these aspects of logistic regression in this article. Let us first understand some use cases of the logistic regression.

## Use Cases

Logistic regression is mostly used in classification tasks where we need to classify between two output either Yes or No, True or False, 0 or 1, etc. Though, we can use multinomial logistic regression for more than two outputs.

### Examples

•   Predicting whether a certain team from a cricket match will win or lose<br/>
•   Predicting whether tomorrow will rain or not<br/>
•   Predicting whether a patient is positive or negative by infection<br/>
•   Predicting whether a user will click on the link or not<br/>
•   Predicting which player out of many will score the most goals in a football match

## Intuition

### Example > Prediting Whether a Certain Team From a Cricket Match Will Win or Lose

Let us consider that we want to predict that in a One Day International (ODI) cricket match between India and Australia at Wankhede Stadium, Mumbai whether India will win or lose. Several factors are affecting the result of a match like atmosphere on the match day, pitch condition, toss result, playing XI, past performance of players against Australia at the same stadium and elsewhere, the current performance of players, etc.<br/>

Let us understand how the logistic regression works in this kind of use case.

### Math Behind

Logistic regression also takes a weighted sum of input features along with bias term just like Linear regression, but it will give us a probability. So to convert the weighted sum to probability it uses a sigmoid function which outputs a value between 0 to 1 indicating probability from 0 to 100%.<br/>

Let us first understand the below formula for finding probabilities for output types.

### Probability Estimation

<span class="centered_equation">
\$\$
\hat{p}=\sigma\left(b_{1} x_{1}+b_{2} x_{2} \ldots . . b_{n} x_{k}+b_{0}\right)
\$\$
</span>

Here, <span class="inline_equation">\\( \hat{p} = \\) </span>(p hat) probability of output types (true/false, yes/no, win/lose)<br/>
<span class="inline_equation">\\( \sigma = \\) </span>sigmoid function<br/>
<span class="inline_equation">b = </span>bias term and coefficients<br/>
<span class="inline_equation">x = </span>input features<br/>

As discussed earlier, the weighted sum of input features along with bias term passed to the sigmoid function to get a probability.<br/>

Let us understand the sigmoid function now.

### Probability Estimation > Sigmoid Function

<span class="centered_equation">
\$\$
\sigma(t)=\frac{1}{1+\exp (-t)}
\$\$
</span>

Here, <span class="inline_equation">\\( \sigma(t) = \\) </span>sigmoid output of t input<br/>
<span class="inline_equation">t = </span>weighted sum of input features with bias term as explained in earlier equation \\( \left(b_{1} x_{1}+b_{2} x_{2} \ldots . . b_{n} x_{k}+b_{0}\right) \\)<br/>
<span class="inline_equation">\\( \exp = \\) </span>exponential function<br/>

This sigmoid function will give us an output between 0 and 1.

### Probability Estimation > Output

After getting probabilities, output will be converted to 0 or 1 based on the following calculation:<br/>

<span class="centered_equation">
\$\$
\hat{y}=\begin{cases}
0  \text { if } \hat{p} < 0.5 \\ \cr
1  \text { if } \hat{p} \geq 0.5 \\ \cr
\end{cases}
\$\$
</span>

if the probability is less than 0.5 than it is considered as 0 or false or lose, etc, and<br/>
if the probability is greater than or equal to 0.5 than it is considered as 1 or true or win etc;<br/>

This would be our final output from the logistic regression algorithm.<br/>

Now, let us understand how input feature weights are optimized using a cost function.

### Cost Function > Partial Derivative of Single Feature

<span class="centered_equation">
\$\$
\frac{\partial}{\partial \theta_{j}} \mathrm{J}(\boldsymbol{\theta})=\frac{1}{n} \sum_{i=1}^{n}\left(\sigma\left(\boldsymbol{\theta}^{T} \mathbf{x}^{(i)}\right)-y^{(i)}\right) x_{j}^{(i)}
\$\$
</span>

<span class="inline_equation">\\( \theta_{j} \\)</span> is a weight of a feature.<br/>
<span class="inline_equation">\\( \sum \\)</span> symbol for doing summation.<br/>
<span class="inline_equation">\\( \boldsymbol{n} \\)</span> = number of records or input data's length<br/>
<span class="inline_equation">\\( \sigma \\)</span> = sigmoid function<br/>
<span class="inline_equation">\\( \boldsymbol{\theta}^{T} \\)</span> = transpose of a weight theta<br/>
<span class="inline_equation">\\(  \mathbf{x}^{(i)} \\)</span> = feature value from an input vector<br/>
<span class="inline_equation">\\(  y^{(i)} \\)</span> = actual value of dependent variable from an input vector<br/>
<span class="inline_equation">\\(  x_{j}^{(i)} \\)</span> = feature value from an input vector (for single feature it is same as \\(  x^{(i)} \\) or we can say it is jth feature value from ith input vector)<br/>

The above cost function will give us a partial derivative of a single feature. After calculating for all features we can use them to update existing weights. There is not any formula for calculating all features partial derivatives in one go that I know.<br/>

Refer partial derivative calculations for single and multiple features in batch gradient descent here for better understanding: <a href="/posts/batch-gradient-descent/#partial-derivative-of-a-single-feature--formula">Batch Gradient Descent Partial Derivative Calculations</a><br/>

Once we have all the partial derivatives, we can use them in gradient descent algorithms to find optimum feature weights.<br/>
Refer <a href="/tags/gradient-descent-types/">Gradient Descent Algorithms</a><br/>

That's all for logistic regression, you can now use it in solving your problems.<br/>

Following is an illustration of how sigmoid function outputs 0 or 1 from probabilities.

## Diagram > Sigmoid Function

<img src="/assets/img/sample/logistic_regression_sigmoid_function_diagram.png" alt="Logistic Regression Sigmoid Function Diagram">

### Details

•	As you can see in the diagram, positive t values will have probability greater than or equal to 0.5 and they will become 1 in the final output.<br/>
•	Whereas on the other side negative t values will have probabilities less than 0.5 that will become 0 in the final output.<br/>
•	Sigmoid function gives us the "S" shaped curve.

## Logistic Regression > Things To Remember

•   Now, you know how to use logistic regression, but what about determining the accuracy of the model?<br/>
•   An accuracy of a classification model can be measured with different evaluation metrics.<br/>
•   Some of them are Confusion matrix, ROC curve, F1 Score, etc.<br/>
•   Evaluation metrics are not covered in this article, but they will be available in detail in future articles and will be linked here.<br/>
•   Now, talking about the implementation of logistic regression, the sklearn library of python has already implemented it so you just have to pass some parameters to use that.<br/>
•   It has also an implementation of binary and multinomial logistic regression by changing a few parameters.<br/>
•   Binary logistic regression is the one that we have discussed in this article but multinomial is the one where we have more than 2 output types.<br/>
•   For multinomial logistic regression, softmax function is used that will give a probability for all the output types just like sigmoid function for two output types.<br/>
•   Softmax function will be discussed in a future article and it will be linked here as well.<br/>
•   We can also use polynomial features here in logistic regression for better performance. Check here <a href="/posts/polynomial-regression/">Polynomial Regression</a> for understanding how we can transform normal features to polynomial features.

## Conclusion

•   Logistic regression is easy to implement and does not require huge computation power.<br/>
•   It is easy to interpret therefore used widely in corporate projects.<br/>
•   It works well when the problem is linear and features are correlated to the output variable.<br/>
•   If you want to use non-linear features, then you must transform them.<br/>

That is how the logistic regression works. Try using it with your use cases and see how it behaves.<br/><br/>

## End Quote

> Machine learning is the science of getting computers to learn without being explicitly programmed. <b>– Sebastian Thrun</b>