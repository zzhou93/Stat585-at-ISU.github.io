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
freq$year <- freq$year %>% factor()
freq %>% ggplot(aes(x=year, y=n, fill=class))+
  geom_bar(stat="identity",position="dodge")
{% endhighlight %}

![center](../figure/blog-2019/02/WangYuchen-unnamed-chunk-1-1.png)



