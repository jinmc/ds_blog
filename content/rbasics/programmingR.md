---
title: "Basic Programming in R"
date: 2020-03-23T23:45:08-04:00
draft: false
tags: ["RBasics", "RBasics_wk4"]
summary: "Conditionals, loops, and functions"
---

<h2>Conditionals</h2>

<p>
Like any other programming, R has conditionals, the if and else statemenets.
It would be so frustrating if it didn't have. One unique function R has is the ifelse function, which does the same thing as if else statement but making it in one line. It is also useful because it works on vectors! Also, any(), and all() will return either true or false if any of the element is true or all of the element are true or not.
</p>

```
if (boolean) {
    print("true")
} else {
    print("false")
}

# the ifelse() function works similarly to an if-else conditional
a <- 0
ifelse(a > 0, 1/a, NA)

# the ifelse() function is particularly useful on vectors
a <- c(0,1,2,-4,5)
result <- ifelse(a > 0, 1/a, NA)

# the ifelse() function is also helpful for replacing missing values
data(na_example)
no_nas <- ifelse(is.na(na_example), 0, na_example) 
sum(is.na(no_nas))

# the any() and all() functions evaluate logical vectors
z <- c(TRUE, TRUE, FALSE)
any(z) # TRUE
all(z) # FALSE
```

<h2>functions</h2>

<p>
We can define functions to repeat or reuse code, just like other programming languages, also.
We can define them by arrow function and function() syntax. Also, one thing to note is that the variables defined inside the function only matters in the function scope itself. We can also have more than one parameters and set default values as well.
</p>

```
# example of defining a function to compute the average of a vector x
avg <- function(x){
  s <- sum(x)
  n <- length(x)
  s/n
}

# functions can have multiple arguments as well as default values
avg <- function(x, arithmetic = TRUE){
  n <- length(x)
  ifelse(arithmetic, sum(x)/n, prod(x)^(1/n))
}
```

<h2>For loops</h2>

<p>The syntax is for (n in [some_range]) {} . We can use this to populate vectors, as example.</p>

```
# creating a function that computes the sum of integers 1 through n
compute_s_n <- function(n){
  x <- 1:n
  sum(x)
}

# a very simple for-loop
for(i in 1:5){
  print(i)
}

# a for-loop for our summation
m <- 25
s_n <- vector(length = m) # create an empty vector
for(n in 1:m){
  s_n[n] <- compute_s_n(n)
}

# creating a plot for our summation function
n <- 1:m
plot(n, s_n)

# a table of values comparing our function to the summation formula
head(data.frame(s_n = s_n, formula = n*(n+1)/2))

# overlaying our function with the summation formula
plot(n, s_n)
lines(n, n*(n+1)/2)
```