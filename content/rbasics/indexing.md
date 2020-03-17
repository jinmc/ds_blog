---
title: "Indexing the data"
date: 2020-03-16T13:43:55-04:00
draft: false
tags: ["RBasics", "RBasics_wk3"]
summary: "What is indexing and how do we use it"
---

<h2>What is indexing?</h2>

<p>
In dataframes(tables) there are multiple vectors, and accessing each vectors by other vectors would be done by 
indexing. Indexing is done by using logicals(boolean) and we can use logicals to be operated by logical operators.
Also, logical vectors can be coerced into numeric, so we can easily use sum() function to get the sum of all the true values.
</p>

```
# defining murder rate as before
murder_rate <- murders$total / murders$population * 100000
# creating a logical vector that specifies if the murder rate in that state is less than or equal to 0.71
index <- murder_rate <= 0.71
# determining which states have murder rates less than or equal to 0.71
murders$state[index]
# calculating how many states have a murder rate less than or equal to 0.71
sum(index)

# creating the two logical vectors representing our conditions
west <- murders$region == "West"
safe <- murder_rate <= 1
# defining an index and identifying states with both conditions true
index <- safe & west
murders$state[index]
```

<h2>Indexing functions</h2>

<ul>
<li>which() -> tells us which indexes are true ex)  which(murders$state == "Massachusetts")</li>
<li>match() -> tells us which indices match in the second vector</li>
<li>%in% -> see if first vector elements are in second vector</li>
</ul>

```
x <- c(FALSE, TRUE, FALSE, TRUE, TRUE, FALSE)
which(x)    # returns indices that are TRUE

# to determine the murder rate in Massachusetts we may do the following
index <- which(murders$state == "Massachusetts")
index
murder_rate[index]

# to obtain the indices and subsequent murder rates of New York, Florida, Texas, we do:
index <- match(c("New York", "Florida", "Texas"), murders$state)
index
murders$state[index]
murder_rate[index]

x <- c("a", "b", "c", "d", "e")
y <- c("a", "d", "f")
y %in% x

# to see if Boston, Dakota, and Washington are states
c("Boston", "Dakota", "Washington") %in% murders$state
```