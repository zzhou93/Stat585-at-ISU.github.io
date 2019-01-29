---
title: "Split apply combine ..."
author: "Jing Li"
topic: "02"
layout: post
root: ../../../
---

## Background:

The `plyr` package has by now been replaced by other, even faster packages, but the idea of *Split, apply, combine* is as relevant as ever.

Read the paper [The Split-Apply-Combine Strategy for Data Analysis](https://www.jstatsoft.org/article/view/v040i01) by Hadley Wickham.


Write a blog post addressing the questions: 

1. **Which (base R) functions do you know that support the split-apply-combine strategy? In your opinion, are these sufficient - state why or why not?**. 

The base function support split-apply-combine includes apply(), sapply(), tapply(), aggregate(), subset(), split(), cbind(), and rbind().They are sufficient to a certain extend, but still need combine with loop for complicated dataset. 

2. **Using a dataset of your choice, show (by including the split-apply-combine command(s) in your answer) how you can use the split-apply-combine strategy for a part of the data analysis.**

I choose the Titanic dataset as an example to explore the replationship between class and survived status.


{% highlight r %}
library(tidyverse)
library(ggplot2)
data("Titanic")
dat <- data.frame(Titanic)
freq <- dat %>% group_by(Class, Survived) %>% summarise(total=sum(Freq))
freq %>% ggplot(aes(x=Class, y=total, fill=Survived))+
  geom_bar(stat="identity",position="dodge")
{% endhighlight %}

![center](.figure/02/LiJing/unnamed-chunk-1-1.png)
