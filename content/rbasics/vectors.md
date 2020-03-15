---
title: "Vectors in R"
date: 2020-03-15T15:17:22-04:00
draft: false
tags: ["RBasics", "wk2"]
summary: "vector manipulations and syntax"
---

<h2>Basic Vector syntax</h2>

<p>
Vectors are basically columns of table. To make vectors, we can use functions such as concatenate c().
seq() function is useful to generate sequence. 1:5 and seq(1:5) has the same result!
We can access vector by murders$population but also can do murders[['population']] (single bracket won't work!)
</p>

```
# sequence from 1, 2, 3, ... 10
seq(1, 10) # makes a list [1 to 10]
seq(1, 10, 2) # [1, 3, 5, ...9]

# We may create vectors of class numeric or character with the concatenate function
codes <- c(380, 124, 818)
country <- c("italy", "canada", "egypt")

# We can also name the elements of a numeric vector
# Note that the two lines of code below have the same result
codes <- c(italy = 380, canada = 124, egypt = 818)
codes <- c("italy" = 380, "canada" = 124, "egypt" = 818)

# We can also name the elements of a numeric vector using the names() function
codes <- c(380, 124, 818)
country <- c("italy","canada","egypt")
names(codes) <- country

# Using square brackets is useful for subsetting to access specific elements of a vector
codes[2] # will get second element
codes[c(1,3)] # will get first and third
codes[1:2] # will get first and second

# If the entries of a vector are named, they may be accessed by referring to their name
codes["canada"]
codes[c("egypt","italy")]
```

<ul>
<li>identical(a, b) -> function that tells you how many of what you have ~ like duplicates. Good for factors</li>
<li>table(a, b) -> function that tells you how many of what you have ~ like duplicates. Good for factors</li>
</ul>


<h2>Vector Coercion</h2>

<p>
The vector will automatically turn numerics into characters if we make a vector with a string.
as.character() and as.numceric() will turn the vector into other type of vectors.
If you make a character data as.numeric(), it will change the data to NA (not assigned)
</p>

```
x <- c(1, "canada", 3)
```


