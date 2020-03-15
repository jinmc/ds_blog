---
title: "R_Intro"
date: 2020-03-15T12:03:24-04:00
draft: false
summary: "About R and RStudio"
tags: ["RBasics", "wk1"]
---
<h2>
What is R and R Studio?
</h2>
<p>
R was developed by statisticians and data analysts. It is free and open source, has capability to save scripts, and many resources for learning, and easy for developers to share software implementations.
</p>
<p>
We can us install package scripts and library function.
</p>

```
# installing the dslabs package
install.packages("dslabs")
# loading the dslabs package into the R session
library(dslabs)
# to install two packages at the same time
install.packages(c("tidyverse", "dslabs")） 
```

<h2>
Objects in R
</h2>

<ul>
<li>We can assign by <- </li>
<li>We can type the variable name or use print() function</li>
<li>Objects are stored in names, it can be variables, or functions</li>
<li>ls() shows the names of object</li>
</ul>

```
a <- 1
b <- 1
c <- -1
# solving the quadratic equation
(-b + sqrt(b^2 - 4*a*c))/(2*a)
```

<h2>Data Types</h2>

<ul>
<li>class() help us determine the type of object</li>
<li>Data frames can be thought as tables with rows representing observations and columns representing different variables</li>
<li>To access data from columns of a data frame, we use dollar symbols, $, which is called the accessor</li>
<li>A vector is an object consisting of several entries such as logical, character, numeric (one vector has one type only)</li>
<li>We use quotes to distinguish b/w variable names and character strings</li>
<li>Factors are useful for storing categorical data, & more memory eficient than storing characters.
EX) levels(murders$region)</li>
<li>What is the difference b/w factors and vectors? - factors have levels(chars) Also can have duplicates!, vectors have logical, numeric, character, ...</li>
</ul>

```
# determining that the murders dataset is of the "data frame" class
class(murders)
# finding out more about the structure of the object
str(murders)
# showing the first 6 lines of the dataset
head(murders)

# using the accessor operator to obtain the population column
murders$population
# displaying the variable names in the murders dataset
names(murders)
# determining how many entries are in a vector
pop <- murders$population
length(pop)
# vectors can be of class numeric and character
class(pop)
class(murders$state)s

# factors are another type of class
class(murders$region)
# obtaining the levels of a factor
levels(murders$region)
```