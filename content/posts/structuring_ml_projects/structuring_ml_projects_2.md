---
title: "Structuring_ml_projects_2"
date: 2021-09-25T15:24:15+09:00
draft: false
---

## Error Analysis

Look at dev Examples to evaluate ideas.(ex. cat classifier)
Should you try to make your cat classifer do better on dogs?

Error analysis : 
* Get 100 mislabeled dev set examples
* Count up how many are dogs

---
## Cleaning up incorrectly labeled data

Evaluate multiple ideas in parallel(ideas)
* Fix pictures of dogs being recognized as cats
* Fix great cats being misrecognized
* Improve performance on blurry images

---
## Correcting incorrectly labeled data

Deep Learning algorithms are quite robust to random errors in the training set(But systematic error we should fix!)

We can also track Incorrectly labeled when doing Error Analysis!

|                         | Case 1      | Case 2      |
| ------  | ----------- | ----------- |
| Overall Dev set error   | 10%          | 2%        |
| Error due to incorrect labels | 0.6%     | 0.6%          |
| Other causes                  | 9.4%       | 1.4%         | 

not very important in Case 1, but important in Case 2!

---

## Correcting incorrect dev/test set examples
* Apply same process to your dev & test sets to make sure they come from the same distribution
* Consider examining examples your algorithm got right as well as one it got wrong
* Train & dev/test data may now come from slightly different distributions

---
## Build your first system quickly, then iterate
Lots of optimization, error anlysis can be done...

people usually overthink rather than underthink!

---

## Mismatched Training and Dev/test set
Training and testing on different distributions

200k -> data from elsewhere  
10k -> data to target

We can add everything, divide as train/dev/test, but better way is to use   
10k only in dev/test 2.5k, 2.5k  
put the rest (200k + 5k) in training  
-> reason: If we add everything, we can target the wrong destination!

---
## Bias & Variance with Mismatched Data Distributions

Let's say human error is almost 0%  
Training error ... 1%  
Dev error ... 10%

We introduce Training-dev set:  
Same distribution as training set, but not used for training

Training error ... 1%  
Training-dev error ... 9%   
Dev error : 10%

We have variance problem  

If we have training error ... 1%  
training-dev error ... 9%  
dev error ... 10% 

then we have data mismatch problem!

More general Formulation:  
Even dev/test is better than training error, it may be because of data mismatch, and it might be a good thing (We should know all errors of each distribution human level, error on training, training-dev, Dev/test)

---

## Addressing data mismatch

* Carry out manual error analysis to try to understand difference between training and dev/test sets
* Make training data more similar; or collect more data similar to dev/test sets

---

## Transfer Learning

Use cat-classifier for X-ray images by changing only the last layers ->  
Initialize the last weights only, and retrain them

If we have enough data, we can retrain entire layers, or we can retrain last layer only

> When can we use transfer learning?
* Task A and B has same input
* You hav ea lot more data for Task A than Task B
* Low level features from A could be helpful for learning B

---

## Multi-task Learning

Ex) Simplified autonomous driving example (learn several things at once!)

Unlinke softmax activation, one image can have multiple label

> When multi-task learning makes sense

* Training on a set of tasks that could benefit from having shared lower-level features
* Usually: Amount of data you have for each task is quite similar
* Can train big enough neural network to do well on all the tasks

In general, transfer learning is used much more often than multi-task learning. One area multi-task learning is used well is computer vision objected detection.

---

## What is End-to-end Deep Learning?
(traditional)
audio -> feature -> Phonemes -> words -> transcript  
(end to end)
audio -> transcript

But we need more data! (3000h vs 100,000h)

Machine Transition
(traditional) English -> text analysis -> ... -> French
(end to end) English -> French

In sum, to do end-to-end deep learning, we need lots of data!

---

## Whether to use End-to-End Deep Learning?

Pros and Cons of end-to-end deep learning

Pros: let the data speak
less hand-desgning of components needed

Cons: May need large amount of data
Excludes potentially useful hand-desinged components

Applying end-to-end deep learning

Key question : Do you have sufficient data to learn a function of the complexity needed to map x to y?

Ex) Autonomous driving

image -> cars/pedestrian -> motion planning -> route -> steering

This is better than jus having end-to-end right away!