---
title: "Blog 2 - Split apply combine"
author: "Lydia English"
topic: "02"
layout: post
root: ../../../
---

Write a blog post addressing the questions: 

1. **Which (base R) functions do you know that support the split-apply-combine strategy? In your opinion, are these sufficient - state why or why not?** 
  
I'm most familiar with the aggregate function in base R since I'm usually working with dataframes. However this function doesn't offer the same fleixbility as the plyr family since it will only work with dataframes or objects that can be coerced into dataframes, therefore it is not a sufficient split-apply-combine function for all data types. Also I believe it doesn't allow the user to apply multiple functions to the dataframe simultanesouly. 

2. **Using a dataset of your choice, show (by including the split-apply-combine command(s) in your answer) how you can use the split-apply-combine strategy for a part of the data analysis.**

I will be using msleep from ggplot2 for my example, which is a dataframe of sleep data for a variety of different mammals. 


{% highlight r %}
library(tidyverse)
data("msleep")
{% endhighlight %}

We can use a split-apply-combine strategy to examine whether the average amount of sleep differs between feeding clades. 


{% highlight r %}
msleep %>%
  group_by(vore)%>%
  dplyr::summarize(avg_sleep = mean(sleep_total), 
            count = n())
{% endhighlight %}



{% highlight text %}
## # A tibble: 5 x 3
##   vore    avg_sleep count
##   <chr>       <dbl> <int>
## 1 carni       10.4     19
## 2 herbi        9.51    32
## 3 insecti     14.9      5
## 4 omni        10.9     20
## 5 <NA>        10.2      7
{% endhighlight %}

Looks like insectivores get the highest average sleep but they also have a very small sample size. 

Theoretically faceting is another way to split-apply-combine since we are applying the same graph to different groups. Seems like the strongest relationship between body weight and total hours of sleep is in the herbivores. 



{% highlight r %}
msleep %>%
  ggplot(aes(x = sleep_total, y = bodywt))+
  geom_point()+
  facet_wrap( ~ vore)+
  scale_y_continuous(trans='log2')+
  ylab("Body Weight (log2 transformed)")+
  xlab("total sleep")
{% endhighlight %}

![center](../figure/blog-2019/02/EnglishLydia-unnamed-chunk-3-1.png)

