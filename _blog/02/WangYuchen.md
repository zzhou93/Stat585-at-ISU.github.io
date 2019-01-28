---
title: "Split apply combine ..."
author: "Yuchen Wang"
topic: "02"
layout: post
root: ../../../
---


Write a blog post addressing the questions: 

1. **Which (base R) functions do you know that support the split-apply-combine strategy? In your opinion, are these sufficient - state why or why not?**. 
apply(), tapply(), sapply(), split(), rbind(), cbind(), and so on.
They are more sufficient than doing everything through loops, but they still need some loops to deal with complex data set.

2. **Using a dataset of your choice, show (by including the split-apply-combine command(s) in your answer) how you can use the split-apply-combine strategy for a part of the data analysis.**

I choose the date set "mpg" and explore the relationship between year and class.


{% highlight r %}
library(tidyverse)
library(ggplot2)
data<-data.frame(mpg)
freq<- data %>% 
  group_by(year) %>% 
  count(class)
{% endhighlight %}



{% highlight text %}
## Error in UseMethod("as.quoted"): no applicable method for 'as.quoted' applied to an object of class "function"
{% endhighlight %}



{% highlight r %}
freq$year <- freq$year %>% factor()
{% endhighlight %}



{% highlight text %}
## Error in `$<-.data.frame`(`*tmp*`, year, value = structure(integer(0), .Label = character(0), class = "factor")): replacement has 0 rows, data has 1
{% endhighlight %}



{% highlight r %}
freq %>% ggplot(aes(x=year, y=n, fill=class))+
  geom_bar(stat="identity",position="dodge")
{% endhighlight %}



{% highlight text %}
## Don't know how to automatically pick scale for object of type function. Defaulting to continuous.
## Don't know how to automatically pick scale for object of type function. Defaulting to continuous.
## Don't know how to automatically pick scale for object of type function. Defaulting to continuous.
{% endhighlight %}



{% highlight text %}
## Error: Columns `x`, `y`, `fill` must be 1d atomic vectors or lists
## [90mCall `rlang::last_error()` to see a backtrace[39m
{% endhighlight %}

![center](../figure/blog-2019/02/WangYuchen-unnamed-chunk-1-1.png)



