---
title: "Data Wrangling and Basic Plotting"
date: 2020-03-23T21:53:43-04:00
draft: false
tags: ["RBasics", "RBasics_wk3"]
summary: "Using Dplyr package - mutate(), filter() and select(), and pipe %>%, plotting with histogram and boxplot"
---
<h2>
Data Wrangling with Dplyr package
</h2>

<p>
Data wrangling, or munging, is to transform the mapping data to another form of data 
so that we can use it with ease. So to say, it is a process of cleaning enriching raw data.
We can use below functions for data wrangling.
</p>

<ul>
<li>mutate() - we can add new column, or change existing one</li>
<li>filter() - filter the data by subsetting rows</li>
<li>select() - subset the data by subsetting columns</li>
<li>pipe operattor, %>% - perform a series of action by chaining them together</li>
</ul>

```
# installing and loading the dplyr package
install.packages("dplyr")
library(dplyr)

# adding a column with mutate called rate
library(dslabs)
data("murders")

head(murders) # shows top 10 
murders <- mutate(murders, rate = total / population * 100000)

# subsetting with filter
filter(murders, rate <= 0.71)

# selecting columns with select
new_table <- select(murders, state, region, rate)

# using the pipe
murders %>% select(state, region, rate) %>% filter(rate <= 0.71)
```

<h2>Creating Data Frames</h2>

<p>
We can create data frames using data.frame function. Note that data framew in default 
turns characters to factors, so we should include stringsAsFactors = FALSE at last. In the example, to make names as a character, we include this element.
</p>
```
# creating a data frame with stringAsFactors = FALSE
grades <- data.frame(names = c("John", "Juan", "Jean", "Yao"), 
                     exam_1 = c(95, 80, 90, 85), 
                     exam_2 = c(90, 85, 85, 90),
                     stringsAsFactors = FALSE)
```

<h2>Basic Plotting</h2>

<p>By plotting data, we can quickly see what's going on, and realize the importance of the situation. R lets you to draw plots with simple syntax.</p>

<ul>
<li>plot() - simple scatterplot</li>
<li>hist() - makes a histogram that gives graphical summary about the general summary</li>
<li>boxplot() - provides a compact summary of a distribution than histogram and more useful for comparing distributions</li>
</ul>

```
# a simple scatterplot of total murders versus population
x <- murders$population /10^6
y <- murders$total
plot(x, y)

# a histogram of murder rates
hist(murders$rate)

# boxplots of murder rates by region
boxplot(rate~region, data = murders)
```