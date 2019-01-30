
---
title: "Split-apply-combine..."
author: "Firstname Lastname"
topic: "02"
layout: post
root: ../../../
---

## Background:

## Prompt:


The `plyr` package has by now been replaced by other, even faster packages, but the idea of *Split, apply, combine* is as relevant as ever.

Read the paper [The Split-Apply-Combine Strategy for Data Analysis](https://www.jstatsoft.org/article/view/v040i01) by Hadley Wickham.


Write a blog post addressing the questions: 

1. **Which (base R) functions do you know that support the split-apply-combine strategy? In your opinion, are these sufficient - state why or why not?**. 

It includes aggregate, apply, lapply, sapply, mapply, tapply, by, replicate etc. 

I think they are not sufficient. Though these functions can support the split-apply-combine strategy, the syntax is inconsistent and often causes confusion.

2. **Using a dataset of your choice, show (by including the split-apply-combine command(s) in your answer) how you can use the split-apply-combine strategy for a part of the data analysis.**

With the dataset 'airquality', we can:


{% highlight r %}
#calculate the colume mean
apply(airquality,2,FUN=function(x){mean(x,na.rm=1)})
{% endhighlight %}



{% highlight text %}
##      Ozone    Solar.R       Wind       Temp      Month        Day 
##  42.129310 185.931507   9.957516  77.882353   6.993464  15.803922
{% endhighlight %}



{% highlight r %}
#find the colume max
apply(airquality,2,FUN=function(x){max(x,na.rm=1)})
{% endhighlight %}



{% highlight text %}
##   Ozone Solar.R    Wind    Temp   Month     Day 
##   168.0   334.0    20.7    97.0     9.0    31.0
{% endhighlight %}



{% highlight r %}
#find the colume min
apply(airquality,2,FUN=function(x){min(x,na.rm=1)})
{% endhighlight %}



{% highlight text %}
##   Ozone Solar.R    Wind    Temp   Month     Day 
##     1.0     7.0     1.7    56.0     5.0     1.0
{% endhighlight %}
