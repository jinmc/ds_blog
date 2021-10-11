---
title: "Model_application"
date: 2021-10-03T19:01:36+09:00
draft: false
tags: ["cnn"]
---

## Why CNN?

Inputs can be really big! For example, 1000 x 1000 becomes million.  
To handle this, We introduce convlutions.

---

## Edge Detection example

- Vertical edge Detection

example filter

1  | 0 |  -1  
1  | 0 |  -1  
1  | 0 |  -1  

Other filters such as sobel filer and scharr filter,  
but we can also learn the filter by back propagation!

___

## Padiing

Why do we using padding?

If we have 6x6 image and 3x3 filter, the output becomes 4x4.  
It becomes keep getting smaller!

Also, the pixels in the middle is used much more than pixels in the outer image!

- "valid" convolution => no padding
- "same" convolution => Pad so that output size is the same as the input size

equation : 
n + 2p - f + 1 = n

so, p = (f-1) / 2

---

## Strided Convolutions

Skip pixels when doing convolution!  
Default will be stride 1, and we skip 2 pixels will be stride = 2, both horizontal and vertically.

for example : (1, 1), (1, 3), .. (3, 1), ..

---

## Convolutions on RGB images

As RGB has 3 channels, and filters also should have same number of channels.

We can also have several filters, and the number of filters becomes the number of channels.

---

## Number of parameters in one layer

If you have 10 filters that are 3x3x3 in one layer of a neural network, how many parameters does that layer have?

-> 280 parameters ((3x3x3 + 1) x 10 )

---

## Pooling layer

Pooling has no parameters to learn! Hyperparameter has Filter size and stride!

If max-pooling in 3D, max-pooling is done independently on each of the channels.

There is also average-pooling, but max-pooling is used much more!

---

## Why Convolutions?

If we roll out every nodes, there are too much nodes!  
But if we use convolution, the parameters reduce significantly!

### Parameter Sharing

A feature detector (such as vertical edge detector) that's useful in one part of the image is probably useful in another part of the image

### Sparsity of Connections

In each layer, each output value depends only on a value of inputs



