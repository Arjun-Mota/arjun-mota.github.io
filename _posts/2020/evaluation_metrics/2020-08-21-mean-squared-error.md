---
title: Mean Squared Error (MSE) - Evaluation Metrics
author: Arjun Mota
date: 2020-08-21 18:45:00 +0530
image: /assets/img/sample/mean_squared_error.png
social_card: /assets/img/social_card/mean_squared_error.png
summary: Machine learning model evaluation metric MSE (mean squared error) explanation, formula and usecases of it.
categories: [Artificial Intelligence, Evaluation Metrics]
tags: [machine-learning, evaluation-metrics, mean-squared-error, machine-learning-glossary, regression-evaluation-metrics]
math: true
toc: true
---

## Brief

Mean squared error is one of the popular evaluation metrics used in measuring the accuracy of a model. It calculates the sum of squared differences and divides them by the number of records, squaring the number will remove the negative sign. Let's see the formula and understand it.

## Formula

<span class="centered_equation">
\begin{equation}
\mathrm{MSE}= \frac{1}{\mathrm{n}} \sum_{\mathrm{i}=1}^{\mathrm{n}} \left( \mathrm{y}_{\mathrm{i}}-\mathrm{\hat y} _ {\mathrm{i}}\right)^{2}
\end{equation}
</span>

## Explanation

Here, <span class="inline_equation">\\( \sum \\)</span> = symbol for doing addition of values,<br/>
<span class="equation_variables">n = </span> number of records,<br/>
<span class="equation_variables">i = </span> record index starting from 1 (first record),<br/>
<span class="equation_variables">y = </span> actual record from our testing data,<br/>
<span class="inline_equation">\\( \mathrm{\hat y} \\)</span> = predicted value of y record from a model,<br/>

So, this formula will calculate the sum of squared differences between the actual value <span class="equation_variables">y</span> and predicted value <span class="inline_equation">\\( \mathrm{\hat y} \\)</span> (yhat) for all records and divide them by <span class="equation_variables">n</span> the number of records. Remember that it is doing a square of differences between two values to remove negative sign unlike <a href="/posts/mean-absolute-error">Mean Absolute Error (MAE).</a>

## Example

Let's look at one example for better understanding:

|Actual Value|Predicted Value|Difference|
|-:|--:|-:--|
|10.3|12.5|-2.2|
|25.7|22.1|3.6|
|15.8|11.2|4.6|

if we calculate the summation of squared differences, it would be like:
<span class="inline_equation">\\( (-2.2)^2+(3.6)^2+(4.6)^2\\)</span><br/>
<span class="inline_equation">\\( = 4.84 + 12.96 + 21.16 = 38.96\\)</span>
<br/>
38.96 is our sum of differences. Now, we will divide 38.96 by 3 which is the number of records in this case:
<br/><br/><span class="inline_equation">\\( 38.96 / 3 = 12.99\\)</span><br/><br/>
12.99 is our MSE (Mean Squared Error).
<br/>
That's it! You are done with the MSE (Mean Squared Error).