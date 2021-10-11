---
title: "CNN - Case studies"
date: 2021-10-07T19:35:51+09:00
draft: false
tags: ["cnn"]
---

## Why look at case studies?

It is the quickest, easiest way to gain intuition, by writing and read other's code and architecture. We'll see a few networks such as Lenet-5, Alexnet(googleNet), resnet, inception neural network, etc.

---

## Lenet-5 (Classic)

- small parameters - 60k parameters  
- width and height gets smaller as # of channels get bigger  
- Used average pooling when today max pooling is used much more  
- tanh, hyperbolic function was used as activation  
*lecun et al*  

  <img src="{{<baseurl>}}/cnn/case_studies_1.png" alt="case_studies_1" width="600" height="250">

## AlexNet(GoogleNet) 

- Made by engineers in google  
- Similarity with Lenet, but much bigger! (60 Million parameters)  
- Relu was used  

  <img src="{{<baseurl>}}/cnn/case_studies_2.png" alt="case_studies_2" width="600" height="450">

## VGG-16 

- 16 layers, 138 million parameters (pretty large)
- the simplicity of the structure is what makes it appealing
- height and weight decreases while number of channels doubles
- There is also VGG-19 but the performance is similar

  <img src="{{<baseurl>}}/cnn/case_studies_3.png" alt="case_studies_3" width="600" height="450">

---

## Resnet

Resnets are built with residual blocks.  
residual blocks came out to solve the problem of vanishing and exploding gradients.  
Skip Connection, or short cut is used, which refers to a[l] just skipping over a lyer or kind of skipping over almost two layers in order to process information, which allows you to train deeper networks.   

  <img src="{{<baseurl>}}/cnn/case_studies_4.png" alt="case_studies_4" width="700" height="450">
  In plain networks, (without residual networks), training error will go up after reducing!

  <img src="{{<baseurl>}}/cnn/case_studies_5.png" alt="case_studies_5" width="700" height="450">

## Why do Resnets work well?

It's because when activation, it's easy to get the identity matrix, and thus it is easy to stay on the previous error rate.
But if we don't have residual nets, we might just fall to worse situations

  <img src="{{<baseurl>}}/cnn/case_studies_6.png" alt="case_studies_6" width="500" height="200">

Theses are the example when residual nets are composed of to make resnets.

  <img src="{{<baseurl>}}/cnn/case_studies_7.png" alt="case_studies_7" width="700" height="450">

