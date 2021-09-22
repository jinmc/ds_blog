---
title: "Structuring_ml_projects"
date: 2021-09-22T14:24:46+09:00
draft: false
tag: ["machine learning"]
---

## Example methods to imrove your model
* Collect more data
* Collect more diverse training set
* Train longer
* Try Adam instead of Gradient Descent
* Try bigger network
* Try smaller network
* Try dropout
* Add L2 regularization
* Network Architecture

---
## Orthogonalization

<p>Orthogonalization means to tune only one thing to achieve one effect! Early stopping is a useful method but it affects both training and dev set performance together so it's not good in the sense of orthogonalization.</p>

<p>Chain of Assumptions in ML</p>
<p>
Fit training set well on Cost function (until human level performance) -> (bigger network, Adam)
</p>

<p>Fit dev set -> (Regularization, bigger training set)</p>

<p>Fit test set -> (Bigger dev set) </p>

<p>Performs well (If not, Change dev set or cost function)</p>

---

## Single Number Evaluation metric

<p>We can get F1 score (Harmonic mean of Precision and Recall) to get Single Number Evaluation. It is important to evaluate the models</p>

---


## Satisficing & Optimizing metrics

<p>
Let's say Accracy and optimization(speed) both matters.
Satisficing -> at least this much
Optimizing -> will optimize this as much as possible
Usually, we have 1 optimizing metric while N-1 satisficing metrics
</p>

---

## Train/Dev/Test Distributions

<p>
Dev/test set should come from the same distribution! Because we don't want to train and pick the wrong model (aim at the wrong direction when we are setting up the dev set!)
</p>

---

## Size of the Dev and Test Sets

<p>
Traditional way of splitting data : 7:3 (no test set), or 6:2:2
but if you have million (lots of) data, 1% of dev(test) set is ok!
</p>

<p>
Test set should be the amount you feel comfortable (have confidence) and sometimes no test set can be ok also
</p>

---

## When to Change Dev/Test Sets & Distributions?

<p>
Let's say we have cat detection model. If we have another matter, we should have anti-porn metric, we should set more weight into datasets!
</p>

---

## Comparing Human level Performance
#### Why Human Level?

<p>
Bayes optimal error -> best possible error
</p>

<p>
It's pretty easy and fast that we can go to human level performance, and often times Bayes error and human level is not that far away! Also, there are some techniques we can use when the performance is below human level performance.
</p>

* Get labeled data from humans
* Gain insight from manual error analysis: Why did a person get this right?
* Better analysis of bias/variance

---

## Avoidable Bias

<p>Example</p>

|         | Case 1      | Case 2      |
| ------  | ----------- | ----------- |
|Humans   | 1%          | 7.5%        |
|Training Error| 8%     | 8%          |
| Dev error | 10%       | 10%         | 

<p>
In the case of Case 1, Avoidable Bias is 7%, when Case 2 has 0.5% of avoidable bias. We can tell which area we should focus on. (Error Analysis)
</p>

<p>
Also, we should keep in mind that the most experienced, team of humans should be regarded as human performance, because however experienced the humans are, it will never be better than Bayes error.
</p>

---

## Surpassing Human-level Performance

<p>
If training error is above human level performance, we can see as bias, but if it's less than human level performance, it's hard to define if it's overfitting, or Bayes error is smaller than the eror.
</p>

> Problems where ML significatly surpasses human-level performance

* Online Advertising
* Product Recommendations
* Loan Approvals
* Logistics (Deliver time)

---

## Improving your model Performance

We have two assumptions of supervised learning

1. You can fit the training set pretty well
1. The training set performance generalizes pretty well to the dev/test set

How to deal with Bias - Bigger Model, Train longer/Better optimization / NN architecture, hyperparameters

How to deal with variance - More data, Regularization(l2), data augmentation
