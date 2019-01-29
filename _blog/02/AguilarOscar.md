---
title: "Split apply combine ..."
author: "Oscar Aguilar"
topic: "02"
layout: post
root: ../../../
---

## Background:

The `plyr` package has by now been replaced by other, even faster packages, but the idea of *Split, apply, combine* is as relevant as ever.

Read the paper [The Split-Apply-Combine Strategy for Data Analysis](https://www.jstatsoft.org/article/view/v040i01) by Hadley Wickham.


Write a blog post addressing the questions: 

1. **Which (base R) functions do you know that support the split-apply-combine strategy? In your opinion, are these sufficient - state why or why not?**. 

There are some base `R` functions that support the split-apply-combine strategy such as `subset()`, `split()`, `by()`, `apply()`, `sapply()`, `lapply()`, `tapply()`, `aggregate()`, `rbind()`, and `cbind()`. These functions can tackle any task  as `plyr`. However, in some scenarios, these functions can take slow down your program when they are using in big loops.

My personal opinion is that the base `R` function mentioned in the previous paragraph are sufficient because they get the job done. On the other hand, from the computing time, it's better to use function from `plyr` such as `ddply`. Also, these function are more intuite, which makes your code easier to read/follow when share with others. 



2. **Using a dataset of your choice, show (by including the split-apply-combine command(s) in your answer) how you can use the split-apply-combine strategy for a part of the data analysis.**



I'm going to use the data set called `airquality` from the dataset `R` package. This data set contains information related to daily air quality measurements in New York from May to September in 1973. We first print the first six observation of the data set.


{% highlight r %}
data("airquality")
airquality %>% head()
{% endhighlight %}



{% highlight text %}
##   Ozone Solar.R Wind Temp Month Day
## 1    41     190  7.4   67     5   1
## 2    36     118  8.0   72     5   2
## 3    12     149 12.6   74     5   3
## 4    18     313 11.5   62     5   4
## 5    NA      NA 14.3   56     5   5
## 6    28      NA 14.9   66     5   6
{% endhighlight %}

Note that value 5 in `Month` represents observations associated to May. Also, the values 1 to 31 in `Day` represents the day of the month. A common question is to compare the average temperatues during those months.  


{% highlight r %}
airquality %>% 
  group_by(Month) %>%
    summarise(ave_temperature = mean(Temp, na.rm = T))
{% endhighlight %}



{% highlight text %}
## # A tibble: 5 x 2
##   Month ave_temperature
##   <int>           <dbl>
## 1     5            65.5
## 2     6            79.1
## 3     7            83.9
## 4     8            84.0
## 5     9            76.9
{% endhighlight %}

From the above output, July and August are the months with the highest average temperatures. Next, we would like to know what day had the highest and lowest temperature during those two months. 


{% highlight r %}
airquality %>% 
  filter(Month %in% c(7, 8)) %>%
    group_by(Month) %>%
      summarise(min_temp = min(Temp, na.rm = T), 
                max_temp = max(Temp, na.rm = T))
{% endhighlight %}



{% highlight text %}
## # A tibble: 2 x 3
##   Month min_temp max_temp
##   <int>    <int>    <int>
## 1     7       73       92
## 2     8       72       97
{% endhighlight %}

Another question that one may have is: what is the relationship between wind and temperature. 


{% highlight r %}
airquality %>% ggplot(aes(x = Wind, y = Temp)) + geom_point() + geom_smooth()
{% endhighlight %}

![center](../figure/02/AguilarOscar/unnamed-chunk-4-1.png)

From the above graph, as overall, there is a negative relationship between wind and temperature.

