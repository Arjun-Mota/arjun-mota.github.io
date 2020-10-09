---
title: Polynomial Regression - Algorithm Intuition
author: Arjun Mota
date: 2020-09-03 18:20:00 +0530
image: /assets/img/sample/polynomial_regression_cover.png
social_card: /assets/img/social_card/polynomial_regression.png
summary: Polynomial regression algorithm explanation, usecases, diagrams and formulas used in development.
categories: [Artificial Intelligence, Algorithm Intuition]
tags: [regression, machine-learning, supervised-machine-learning]
math: true
toc: true
---

## Background

### Brief

In the Linear Regression, we try to find a coefficient(s) to make a straight line that covers all of our data point such that we can get an accurate prediction on the new data, but what if your data is non-linear?<br/><br/>


In that case, Polynomial Regression comes into the picture. It is developed to deal with non-linear data by finding a coefficient(s) to draw a curvy line to cover all of the data points on a graph. Let’s see where we can use it and how it works.

## Use Cases
The use cases would not be any different than linear regression as it is entirely dependent on types of data and not on the specific use case.

### Examples

• Predicting the temperature of a day<br/>
• Predicting the number of products to be sold<br/>
• Predicting the expenses<br/>
• Predicting a growth rate<br/>
• Predicting the price of a house<br/>

## Intuition

### Example > Predicting The Temperature of a Day

Consider that we want to predict the temperature of a day by the distance of the place from the sea. As per this data, we assume that as you go far from the sea warmer it gets.<br/>

This is not the only factor affects the temperature, there are other factors like latitude, altitude, humidity, cloud cover, etc., also affects but for understanding this concept we are taking this example with one factor only.<br/><br/>


Let’s look at the math behind Polynomial Regression before understanding the temperature prediction with Polynomial regression.

## Math Behind

In polynomial regression, to form a curvy line we need to apply certain exponent to our existing data and that exponent is called a degree. The degree will be our model parameter in the form of an integer value while implementing Polynomial Regression with a programming language like Python. So, if we apply a degree of n where n is an integer number then our equation would be like:

<span class="centered_equation">
\$\$
y=m_{1} x+m_{2} x^{2}+m_{3} x^{3}+\ldots+m_{d} x^{d} + b
\$\$
<span>

Here, <span class="equation_variables">y</span> = dependent variable that we want to predict (temperature),<br/>

<span class="equation_variables">b</span> = bias term/intercept (model parameter)<br/>

<span class="equation_variables">m</span> = slope, weight or coefficient,<br/>

<span class="equation_variables">x</span> = our input feature (e.g. distance from a sea) remains constant (model parameter), the same value will be squared, cubed, etc, based on the given degree,<br/>

<span class="equation_variables">d</span> = (integer) degree for polynomial equation (model parameter).<br/>

```terminal
Note*: x represents only 1 feature here.
During matrix computations far below, we have used multiple features.
```

As you can see it is just like the Linear Regression, if you do not know the Linear Regression then check this out first: <a href="/posts/linear-regression">Linear Regression - Algorithm Intuition.</a> It will help you understand this algorithm.<br/><br/>

### Explanation > Polynomial Regression

Remember that the model parameter degree will be an integer number and it should be chosen wisely as higher the number, more complex our model will be. There is no such method that I know to choose the right number, but you can experiment with different numbers to find an appropriate one.<br/> <br/>

In Python language, when you implement PolynomialFeatures from Sklearn library with say degree 3 for two features <span class="inline_equation">x</span> and <span class="inline_equation">y</span> then it does not only use <span class="inline_equation">\\(x^{2}, x^{3}, y^{2}, y^{3}\\)</span> but also generate an array of features with <span class="inline_equation">\\(x*y,  x^{2} * y, x * y^{2} \\)</span> like computations. Array with Polynomial Features contains <span class="inline_equation">\\(\begin{equation}\frac{(n\ +\ d) !}{d ! \ *\  n !}\end{equation}\\)</span> features where n is the number of features, ! sign is for factorial like <span class="inline_equation">\\( 5! = 5 * 4 * 3 * 2 * 1 \\)</span> and <span class="inline_equation">d</span> is degree. Just imagine how many combinations of features will be there in that array?<br/><br/>

Now coming back to our equation, the question is how to solve it?<br/>

To solve these kinds of equations through programming, we need to do some matrix computations. Following are some matrices used in modern algorithms for computations of polynomial regression:<br/>

<span class="centered_equation">
\$\$ y = \\pmatrix{
y_{1} \\cr
y_{2} \\cr
y_{3} \\cr
\\vdots \\cr
y_{n} \\cr
} \$\$
</span>

<span class="centered_equation">
\$\$ b = \\pmatrix{
b_{0} \\cr
b_{1} \\cr
b_{2} \\cr
\\vdots \\cr
b_{n} \\cr
} \$\$
</span>

<span class="centered_equation">
\$\$ x = \\pmatrix{
1 & x_{11} & x_{12}^2 & \\ldots & x_{1k}^d \\cr
1 & x_{21} & x_{22}^2 & \\ldots & x_{2k}^d \\cr
\\vdots & \\vdots & \\vdots & \\ldots & \vdots \\cr
\\vdots & \\vdots & \\vdots & \\ldots & \vdots \\cr
1 & x_{n1} & x_{n2}^2 & \\ldots & x_{nk}^d \\cr
} \$\$
</span>
In above matrix, n is the number of records, k is the number of features and d is the degree.<br/>
Here, 
<span class="centered_equation">
\$\$
y = x * b
\$\$
</span>
because b contains <span class="inline_equation">\\(
b_{0}
\\) </span> as bias term with all coefficients. In the very first equation, we have mentioned m1, m2, ... here they are presented as b1, b2, ... and given y is a matrix of all predicted values that we will have after doing this computations. x has 1's in the first column that will be scores of each record of our dataset, and rest are all the records with squared and cubed forms depends on a given degree. We have n as the number of records and d as the degree in this matrix.

### Cost Function > Polynomial Regression

Below mentioned equation is used for finding coefficients:<br/>
<span class="centered_equation">
\$\$ b=\left(x^{T} x\right)^{-1} x^{T} y \$\$
</span>

here <span class="inline_equation">\\( x^{T}\\) </span> is transpose matrix of x,
<span class="inline_equation">\\( \left(x^{T} x\right)^{-1}\\) </span> is inverse of <span class="inline_equation">\\( \left(x^{T} x\right)\\) </span> matrix.<br/>

By performing these computations, we will get a curvy line on a graph that covers most of our data through our coefficients and bias term, just like below in the diagram.<br/>
We have finished with the math behind polynomial regression.<br/>

Now, its time to look at visually how it covers non-linear temperature data on a graph.<br/>

## Diagram

<img src="/assets/img/sample/polynomial_regression_diagram.png" alt="Polynomial regression diagram">

## Explanation > Diagram

As we can see in the diagram, there are two regression lines. To clarify the difference between linear and polynomial regression, I have kept both of them on the graph. Given temperature on the y-axis and distance from sea on the x-axis, we can clearly see polynomial works well in this situation. The linear regression line is unable to cover all the data points and when we apply polynomial regression to this data then we get a better regression line that covers most of the data points that will give a better prediction than linear regression.

## Linear Vs. Polynomial Regression

The difference between linear regression and polynomial regression equations is that in polynomial regression we are using exponents to add more data to our model to form a curvy line. The degree would be the variable with the highest number of exponent in our equation like for 2 there would be some variable squared, and cubed for 3rd degree and so on.<br/>

## Conclusion

### Common Questions

You might be having several questions right now.<br/><br/>
⦿ Like when to use this algorithm?<br/>

⦿ How to measure its accuracy?<br/>

⦿ How to deal with all the calculations?<br/>


### Answers

Well, in order to use this algorithm first we need to understand the relationship between variables, like the above diagram shows between temperature and distance from sea. If they are in non-linear pattern then you can try polynomial regression, though there are far more powerful algorithms available now. I will be covering them in future articles.<br/>

For accuracy, you can use the same evaluation metrics as Linear regression like <a href="/posts/mean-squared-error/">mean squared error [MSE]</a>, <a href="/posts/root-mean-squared-error/">rooted mean square error [RMSE],</a> etc. Here is the link for evaluation metrics that I have covered so far: <a href="/tags/evaluation-metrics/">Evaluation Metrics.</a><br/>

You do not have to worry about the implementation because, in modern programming languages, almost everything has been done for us. In Python, all the calculations are already implemented, you just have to pass your data and some model parameters. Your model will be trained on that data and parameters, then you can test its accuracy and optimize it before predict with the new data.<br/><br/>

## End Quote

> “Predicting the future isn’t magic, it’s artificial intelligence.” ~ <b>Dave Waters</b>