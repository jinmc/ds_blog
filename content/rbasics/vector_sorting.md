---
title: "Vector sorting"
date: 2020-03-15T16:39:05-04:00
draft: false
tags: ["RBasics", "RBasics_wk2"]
summary: "sort(), order(), rank(), max, min functions"
---

<h2>
Sorting
</h2>

<p>
Sorting is probably the most important thing in data science. 
There are a few functions that are available in sorting.
sort() function sorts the elements as increasing order.
But more useful function is order(x) instead of sort(x).
We want to get indexes of the vector as sorted because we can use indexes to get information from other vectors.
Also, rank would give you the rank of that element.
</p>

```
x <- c(31, 4, 15, 92, 65)
x
sort(x)    # puts elements in order 
# 4 15 31 65 92

index <- order(x)    # returns index that will put x in order
x[index]    # rearranging by this index puts elements in order
order(x) 
# 2 3 1 5 4

murders$state[1:10]
murders$abb[1:10]

index <- order(murders$total)
murders$abb[index]    # order abbreviations by total murders

max(murders$total)    # highest number of total murders
i_max <- which.max(murders$total)    # index with highest number of murders
murders$state[i_max]    # state name with highest number of total murders

x <- c(31, 4, 15, 92, 65)
x
rank(x)    # returns ranks (smallest to largest)
# 3 1 2 5 4
```

<p>
Also, is.na function is a useful function as it makes vector 0 or 1, 
and we can use sum() to get the sum of vectors. which.min, which.max tells the index of highest and lowest value.
</p>

<h2>Vector arithmetics</h2>

<p>
We can use addition and multiplication, division as a whole.
</p>

```
heights <- c(70, 65, 60) # height in inches
heights * 2.54 # inches to cm   
heights - 65 # subtract everything with mean 


# The name of the state with the maximum population is found by doing the following
murders$state[which.max(murders$population)]

# how to obtain the murder rate
murder_rate <- murders$total / murders$population * 100000

# ordering the states by murder rate, in decreasing order
murders$state[order(murder_rate, decreasing=TRUE)]
```
