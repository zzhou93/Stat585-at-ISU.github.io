---
title: "Split apply combine ..."
author: "Hana Lee"
topic: "02"
layout: post
root: ../../../
---

1. **Which (base R) functions do you know that support the split-apply-combine strategy? In your opinion, are these sufficient - state why or why not?**. 

Oftentimes, I want to calculate the average by a group variable, and then merge the information into my original data set. This is an example where the split-apply-combine strategy is needed. To make it in R, I can use `tapply`, and `merge` functions with some other functions to manipulate the data. I think that those functions are sufficient in that they can help acheive my goals. However, that might not be the best way, considering we can use the package, `tidyverse`, which provides more efficient and intuitive functions.

2. **Using a dataset of your choice, show (by including the split-apply-combine command(s) in your answer) how you can use the split-apply-combine strategy for a part of the data analysis.**

The code is as followings:


{% highlight r %}
head(cars) #The data: `cars`
{% endhighlight %}



{% highlight text %}
##   speed dist
## 1     4    2
## 2     4   10
## 3     7    4
## 4     7   22
## 5     8   16
## 6     9   10
{% endhighlight %}



{% highlight r %}
tmp <- as.data.frame(tapply(cars$dist, cars$speed, mean)) #the process corresponding to "split and apply"
tmp <- cbind.data.frame(tmp, as.numeric(rownames(tmp))) #the beginning of "combine"
colnames(tmp) <- c("avg.stop.distance.by.speed", "speed")
updated.cars <- merge(tmp, cars, by = "speed") #corresponding #the end of "combine"
head(updated.cars) #The part of this result
{% endhighlight %}



{% highlight text %}
##   speed avg.stop.distance.by.speed dist
## 1     4                          6    2
## 2     4                          6   10
## 3     7                         13    4
## 4     7                         13   22
## 5     8                         16   16
## 6     9                         10   10
{% endhighlight %}

This is a hassle 
1. in that I needed to care about the column name used for merging two data sets,
2. in that other than calculating group means, I should care about many things such as the format of data sets, type of variables used for merging
3. if I want to add another variable such as the number of observations each group mean is based on?
