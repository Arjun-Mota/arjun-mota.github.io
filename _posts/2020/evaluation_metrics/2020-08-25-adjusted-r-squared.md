---
title: Adjusted R-Squared (Adjusted R<sup>2</sup>) - Evaluation Metrics
author: Arjun Mota
date: 2020-08-25 22:55:00 +0530
image: /assets/img/sample/adjusted_r_squared.png
social_card: /assets/img/social_card/adjusted_r_squared.png
summary: Machine learning model evaluation metric Adjusted R<sup>2</sup> (adjusted r-squared) explanation, formula and usecases of it.
categories: [Artificial Intelligence, Evaluation Metrics]
tags: [machine-learning, evaluation-metrics, adjusted-r-squared, machine-learning-glossary, regression-evaluation-metrics]
math: true
toc: true
---

## Brief

The Adjusted R-Squared is an evaluation metric that eliminates the limitations of the R-Squared. It tells us how good our regression line fit to our model and how much output varies based on changes in independent variables just like R-Squared but penalizes the number of variables. When you add a new useful variable then Adjusted R-Squared increases, and if the variable is not useful then it will decrease. It will give us a floating-point positive or negative value. It will always be less than or equal to R-Squared value. Let's find out how it works using the following Adjusted R-Squared formula:

## Formula

<span class="centered_equation">
\begin{equation}
R_{a d j}^{2}=1-\left[\frac{\left(1-R^{2}\right)(n-1)}{n-k-1}\right]
\end{equation}
</span>

## Explanation

Here, <span class="equation_variables">\\( R^{2} \\)</span> = R-Squared value,<br/>
<span class="equation_variables">n</span> = number of records in your dataset,<br/>
<span class="equation_variables">k</span> = number of variables added in the model excluding dependent variable.<br/>

•   In the numerator of this formula, we are subtracting R-Squared from 1 and multiplying with number of records n - 1.<br/>
•   Whereas In the denominator, we are subtracting the number of variables k - 1 from the number of records n.<br/>
•   After that we are dividing both values and subtracting it from 1, that gives us the Adjusted R-Squared.<br/><br/>
Let's solve one example:

## Example

Suppose we have a data with R-Squared <span class="equation_variables">\\( R^{2} \\)</span> = 0.73, number of records <span class="equation_variables">n</span> = 87652, number of variables (excluding dependent variable) <span class="equation_variables">k</span> = 34.<br/>

If you want to know how to calculate the R-Squared <span class="equation_variables">\\( R^{2} \\)</span>, then check out here: <a href="/posts/r-squared/">R-Squared</a><br/><br/>
Now, we will put this data into the Adjusted R-Squared formula:

<span class="centered_equation">
\begin{equation}
R_{a d j}^{2}=1-\left[\frac{\left(1-R^{2}\right)(n-1)}{n-k-1}\right]
\end{equation}
</span>

<span class="centered_equation">
\begin{equation}
R_{a d j}^{2}=1-\left[\frac{\left(1 - 0.73\right)(87652-1)}{87652-34-1}\right]
\end{equation}
</span>

<span class="centered_equation">
\begin{equation}
R_{a d j}^{2}=1-\left[\frac{23665.77}{87619}\right]
\end{equation}
</span>

<span class="centered_equation">
\begin{equation}
R_{a d j}^{2}=1-0.27 = 0.73
\end{equation}
</span>


## Conclusion

Here, 0.73 is the Adjusted R-Squared means that our model can fit a regression line such that it can identify 73% of the data correctly with currently added variables. If you add/remove variables and the Adjusted R-Squared increases that means your model is performing better.<br/>

Remember that Adjusted R-Squared can be negative too when your R-Squared is very low or close to 0.<br/><br/>

Check out other<a href="/categories/evaluation-metrics"> Evaluation Metrics.</a><br/>