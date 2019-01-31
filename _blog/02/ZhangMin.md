---
title: "Split-apply-combine..."
author: "Min Zhang"
topic: "02"
layout: post
root: ../../../
---

The `plyr` package has by now been replaced by other, even faster packages, but the idea of *Split, apply, combine* is as relevant as ever.

Read the paper [The Split-Apply-Combine Strategy for Data Analysis](https://www.jstatsoft.org/article/view/v040i01) by Hadley Wickham.


Write a blog post addressing the questions: 

1. **Which (base R) functions do you know that support the split-apply-combine strategy? In your opinion, are these sufficient - state why or why not?**. 

Base R functions that support split-apply-combine strategy include `aggregate()` and `apply()` family. They are not sufficient compared with `dplyr` package, due to readability and number of functions to apply. 

2. **Using a dataset of your choice, show (by including the split-apply-combine command(s) in your answer) how you can use the split-apply-combine strategy for a part of the data analysis.**

The dataset I use for illustration is `mtcars`. The task is to obtain the mean mpg (miles per gallon) and its variance. 



**a. with `aggregate()`**

{% highlight r %}
aggregate(mtcars[, "mpg"], list(cyl = mtcars$cyl), mean)
{% endhighlight %}



{% highlight text %}
##   cyl        x
## 1   4 26.66364
## 2   6 19.74286
## 3   8 15.10000
{% endhighlight %}



{% highlight r %}
aggregate(mtcars[, "mpg"], list(cyl = mtcars$cyl), var)
{% endhighlight %}



{% highlight text %}
##   cyl         x
## 1   4 20.338545
## 2   6  2.112857
## 3   8  6.553846
{% endhighlight %}

**b. with `dplyr`** It's easier to read thanks to the %>% operator, and I can do multiple commands in one `summarise()`.

{% highlight r %}
mtcars %>% group_by(cyl) %>% 
  summarise(mpg.mean = mean(mpg), mpg.var = var(mpg))
{% endhighlight %}



{% highlight text %}
## # A tibble: 3 x 3
##     cyl mpg.mean mpg.var
##   <dbl>    <dbl>   <dbl>
## 1     4     26.7   20.3 
## 2     6     19.7    2.11
## 3     8     15.1    6.55
{% endhighlight %}

