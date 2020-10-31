---
title: Confusion Matrix and Derived Metrics - Evaluation Metrics
author: Arjun Mota
date: 2020-11-01 01:26:00 +0530
image: /assets/img/sample/confusion_matrix.png
social_card: /assets/img/social_card/confusion_matrix.png
summary: The confusion matrix is an evaluation metric widely popular for classification problems. Evaluation terminologies like true positive, false positive, true negative, false negative, f1-score, etc; are derived from this metric. Some of them are covered in this article.
categories: [Artificial Intelligence, Evaluation Metrics]
tags: [machine-learning, evaluation-metrics, confusion-matrix, classification-report, precision, recall, f1-score, macro-average, micro-average, weighted-average, support, machine-learning-glossary, classification-evaluation-metrics]
math: true
toc: true
---

## Introduction

When it comes to an evaluation of a classification problem, the Confusion Matrix is one of the widely popular evaluation metrics. It is a matrix consist of the status of all the predictions and actual values divided into true positive, false positive, true negative, and false negative. We will see in a moment what all these things are.<br/>

Other than the above-mentioned terms, there are some other derived terms/metrics from the Confusion Matrix. In Python language's Sklearn library following are calculated in the Classification Report. Along with Confusion Matrix, the following derived metrics are covered in this article:

•   F1 Score<br/>
•   Precision<br/>
•   Recall<br/>
•   Support<br/>
•   Micro Average<br/>
•   Macro Average<br/>
•   Weighted Average<br/>

Before going for an example, let's quickly understand these terms one-by-one.

## True Positive

True Positive [TP] is the number of positive predictions that are actually positive means the actual values are positive and predicted is also positive.

POSITIVE -> POSITIVE

## False Positive OR Type 1 Error

False Positive [FP] is a number of positive predictions that are actually negative and model predicted wrongly.

False Positive is also known as Type 1 Error.

NEGATIVE -> POSITIVE

## True Negative

True Negative [TN] is the number of negative predictions that are actually negative and model predicted correctly.

The actual value is negative and the model also predicted negative that is the correct prediction of negative values.

NEGATIVE -> NEGATIVE

## False Negative OR Type 2 Error

False Negative [FN] is a number of negative predictions that are actually positive and model predicted wrongly.

False Negative is also known as Type 2 Error.

POSITIVE -> NEGATIVE

## Precision

Precision is a rate of positive predictions. Out of all the positive predictions how many are actually positive. The value of precision will be a floating-point value between 0 to 1. 1 indicates the best score and 0 for the worst score for positive predictions.<br/> 

Following is the formula for identifying precision:

<span class="centered_equation">
\begin{equation}
\text {Precision}=\frac{T P}{T P+F P}
\end{equation}
</span>

TP = True Positive<br/>
FP - False Positive

## Recall

The recall is also a rate of positive predictions like precision but here from of all actual positives values, how many of them are found positive by model. The value of recall will be a floating-point value between 0 to 1. 1 indicates the best score and 0 for the worst score for actual positive predictions.</br> 

Following is the formula for identifying recall:

<span class="centered_equation">
\begin{equation}
\text {Recall}=\frac{T P}{T P+F N}
\end{equation}
</span>

TP = True Positive<br/>
FN - False Negative

## F1-Score

F1-Score is like a mid-way to precision and recall as it is a weighted average of precision and recall. F1-Score changes based on a contribution by precision and recall.<br/>
Both precision and recall cannot increase or decrease together instead if precision increases then recall decreases and vice versa. F1-Score value is also a floating-point value between 0 to 1.<br/>

When F1-Score is 1 then we can say that contribution of precision and recall is equal.

Following is the formula for identifying f1-score:

<span class="centered_equation">
\begin{equation}
\text {F1-Score}=2 * \frac{Precision * Recall}{Precision + Recall}
\end{equation}
</span>

## Support

Support is simply a count of classification type in input data.<br/>
For example, if there is a classification problem with two classes 'A' and 'B' then the total number of 'A' present in input data is a support value of class A.<br/>
So, if there are 10000 records with class A and 9500 with class B then both of these values are support value of their respective classes.

## Micro Average

Micro Average is an average of true positive, false positive, and false negative while working with a multiclass classification problem.<br/>
Precision, Recall, and F1-Score all have Micro Average. Let's see how it is calculated when we have three classes A, B, and C.<br/>

<span class="text_equation">
\begin{equation}
\text {MA for Precision}=\frac{TP1+TP2+TP3}{TP1+TP2+TP3+FP1+FP2+FP3}
\end{equation}
</span>
<br/>
<span class="text_equation">
\begin{equation}
\text {MA for Recall}=\frac{TP1+TP2+TP3}{TP1+TP2+TP3+FN1+FN2+FN3}
\end{equation}
</span>
<br/>
<span class="text_equation">
\begin{equation}
\text {MA for F1-Score}=\frac{2 * MA\ for\ Precision * MA\ for\ Recall}{MA\ for\ Precision + MA\ for\ Recall}
\end{equation}
</span>

In all three formulas above, TP1, TP2, TP3 represent true positive values of classes A, B, and C respectively and the same goes for false positive and false negative.<br/>
Micro Average of F1-Score is a harmonic mean of micro averages of Precision and Recall.

## Macro Average

Macro Average is very simple. For Precision, it is an average of all the Precision values of multiple classes (i.e. A, B, and C). in the case of Recall also it is an average of all Recall values and the same goes for F1-Score.

For example, the micro average of precision would be an average of precision of classes A, B, and C.

## Weighted Average

Weighted Average is an average measured by considering support values of multiple classes i.e. number of each class in input data.<br/>

For example, we have 3 classes A, B, and C then the formula for the weighted average for precision, recall, and f1-score will be like this:<br/>

Here, Support = S, Precision = P, Recall = R and F1-Score = F1 are used.<br/>

<span class="text_equation">
\begin{equation}
\text {WA for Precision}=\frac{S(A) * P(A) + S(B) * P(B) + S(C) * P(C) }{S(A) + S(B) + S(C)}
\end{equation}
</span>
<br/>
<span class="text_equation">
\begin{equation}
\text {WA for Recall}=\frac{S(A) * R(A) + S(B) * R(B) + S(C) * R(C) }{S(A) + S(B) + S(C)}
\end{equation}
</span>
<br/>
<span class="text_equation">
\begin{equation}
\text {WA for F1-Score}=\frac{S(A) * F1(A) + S(B) * F1(B) + S(C) * F1(C) }{S(A) + S(B) + S(C)}
\end{equation}
</span>

## Example

### Confusion Matrix

A confusion matrix is a matrix with actual and predicted values consist of true positive, false positive, true negative, and false negative counts.<br/>

<img src="/assets/img/sample/confusion_matrix_two_classes_skelton.png" alt="Confusion Matrix Skelton">

<img src="/assets/img/sample/confusion_matrix_example_two_classes.png" alt="Confusion Matrix Example">

### Classification Report

<img src="/assets/img/sample/classification_report_example.png" alt="Linear regression diagram">

⦿ This is the same classification report that Python's Sklearn library generates.<br/>
⦿ In the above diagram, we are dealing with three classes A, B, and C.<br/>
⦿ The total number of records in this example are 92 i.e. total of support values of A, B, and C.<br/>
⦿ The rest of the table is self-explanatory with terms discussed earlier, re-look definitions if required.

## Conclusion

⦿ To compute the confusion matrix and classification report, Python's Sklearn library has already implemented it and you just have to pass your actual and predicted data to it to get the results.<br/>
⦿ There are other ways of evaluating classification problems and those will be covered in future articles.<br/>
⦿  You can find all the classification evaluation metrics here: <a href="/tags/classification-evaluation-metrics">Classification Evaluation Metrics</a><br/><br/>

Check out here article categories for more information: <a href="/tabs/categories/">Article Categories</a><br/>