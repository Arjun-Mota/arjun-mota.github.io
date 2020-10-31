---
title: Mean Absolute Error (MAE) - Evaluation Metrics
author: Arjun Mota
date: 2020-08-19 16:50:00 +0530
image: /assets/img/sample/mean_absolute_error.png
social_card: /assets/img/social_card/mean_absolute_error.png
summary: Machine learning model evaluation metric MAE (mean absolute error) explanation, formula and usecases of it.
categories: [Artificial Intelligence, Evaluation Metrics]
tags: [machine-learning, evaluation-metrics, mean-abolute-error, machine-learning-glossary, regression-evaluation-metrics]
math: true
toc: true
---

## Brief

Mean absolute error is one of the evaluation metrics used in measuring the accuracy of a model. As its name says it calculates an error with an absolute figure which means a positive number. Let's see the formula and understand it.

## Formula

<span class="centered_equation">
\begin{equation}
\mathrm{MAE}= \frac{1}{\mathrm{n}} \sum_{\mathrm{j}=1}^{\mathrm{n}} \left| \mathrm{y}_{\mathrm{j}}-\mathrm{\hat y} _ {\mathrm{j}}\right|
\end{equation}
</span>

## Explanation

Here, <span class="inline_equation">\\( \sum \\)</span> = symbol for doing addition of values,<br/>
<span class="equation_variables">n = </span> number of records,<br/>
<span class="equation_variables">j = </span> record index starting from 1 (first record),<br/>
<span class="equation_variables">y = </span> actual record from our testing data,<br/>
<span class="inline_equation">\\( \mathrm{\hat y} \\)</span> = predicted value of y record from a model,<br/>
<span class="equation_variables">|   |</span> = pipes for converting floating point value to absolute value<br/>

So, this formula will calculate the sum of absolute differences between the actual value <span class="equation_variables">y</span> and predicted value <span class="inline_equation">\\( \mathrm{\hat y} \\)</span> (yhat) for all records and divide them by <span class="equation_variables">n</span> the number of records.

## Example

Let's look at one example for better understanding:

|Actual Value|Predicted Value|Difference|
|-:|--:|-:--|
|10.3|12.5|-2.2|
|25.7|22.1|3.6|
|15.8|11.2|4.6|

if we calculate the summation of absolute differences, it would be like:<br/>
<span class="inline_equation">\\( 2.2 + 3.6 + 4.6 = 10.4\\)</span>
<br/><br/>
10.4 is our sum of absolute differences. Remember -2.2 will become 2.2 when we take an absolute value. | | (pipes) in our formula are meant for that.<br/>
Now, we will divide 10.4 by 3 which is the number of records in this case:
<br/><br/><span class="inline_equation">\\( 10.4 / 3 = 3.67\\)</span><br/><br/>
3.67 is our MAE (Mean Absolute Error).
<br/>
That's it! You are done with the MAE (Mean Absolute Error).