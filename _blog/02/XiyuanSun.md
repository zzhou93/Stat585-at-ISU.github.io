---
title: "Split apply combine ..."
author: "Xiyuan Sun"
topic: "02"
layout: post
root: ../../../
---

1. **Which (base R) functions do you know that support the split-apply-combine strategy? In your opinion, are these sufficient - state why or why not?**. 

According to Hadley's paper, in base R, we can tackle this problem with nested loops, or with the apply family of functions. The main disadvantages of the loops is that there is a lot of book-keeping code: the size of the array is hard coded in multiple places and we need to create the output structures before filing them with data. The apply functions simplify the task, but there is not a straightforward way to go from the 2d array of models to the 3d array of residuals. 


2. **Using a dataset of your choice, show (by including the split-apply-combine command(s) in your answer) how you can use the split-apply-combine strategy for a part of the data analysis.**


{% highlight r %}
library(plyr)
{% endhighlight %}



{% highlight text %}
## -------------------------------------------------------------------------
{% endhighlight %}



{% highlight text %}
## You have loaded plyr after dplyr - this is likely to cause problems.
## If you need functions from both plyr and dplyr, please load plyr first, then dplyr:
## library(plyr); library(dplyr)
{% endhighlight %}



{% highlight text %}
## -------------------------------------------------------------------------
{% endhighlight %}



{% highlight text %}
## 
## Attaching package: 'plyr'
{% endhighlight %}



{% highlight text %}
## The following objects are masked from 'package:plotly':
## 
##     arrange, mutate, rename, summarise
{% endhighlight %}



{% highlight text %}
## The following object is masked from 'package:maps':
## 
##     ozone
{% endhighlight %}



{% highlight text %}
## The following object is masked from 'package:lubridate':
## 
##     here
{% endhighlight %}



{% highlight text %}
## The following objects are masked from 'package:dplyr':
## 
##     arrange, count, desc, failwith, id, mutate, rename, summarise,
##     summarize
{% endhighlight %}



{% highlight text %}
## The following object is masked from 'package:purrr':
## 
##     compact
{% endhighlight %}



{% highlight r %}
library(MASS)
{% endhighlight %}



{% highlight text %}
## 
## Attaching package: 'MASS'
{% endhighlight %}



{% highlight text %}
## The following object is masked from 'package:plotly':
## 
##     select
{% endhighlight %}



{% highlight text %}
## The following object is masked from 'package:dplyr':
## 
##     select
{% endhighlight %}



{% highlight r %}
library(dplyr)
library(ggplot2)

#make up the data
v1 = c('Yellow','Black','Blue','Red','Yellow','Black','Blue',
        'Red','Yellow','Black','Blue','Red','Yellow','Black',
       'Blue','Red','Blue','Red')

v2 = c(100000,150000,80000,90000,200000,145000,120000,
      300000,250000,200000,160000,90000,90100,150000,
      142000,130000,400000,350000)

v3 = c(100,150,820,920,230,120,70,250,250,110,130,860,980,300,150,170,230,280)

v4 = c('type A','type A','type A','type A','type A','type A','type A',
        'type A','type A','type B','type B','type B','type B','type B',
       'type B','type B','type B','type B')

sales_data<-data.frame(cbind(v1,v2,v3,v4))
colnames(sales_data)<-c("color","sales","transactions","product")
sales_data$sales <- as.numeric(sales_data$sales)
sales_data$transactions <- as.numeric(sales_data$transactions)

print(sales_data)
{% endhighlight %}



{% highlight text %}
##     color sales transactions product
## 1  Yellow     7            1  type A
## 2   Black     5            5  type A
## 3    Blue    13           12  type A
## 4     Red    14           14  type A
## 5  Yellow     9            7  type A
## 6   Black     4            3  type A
## 7    Blue     1           11  type A
## 8     Red    11            8  type A
## 9  Yellow     8            8  type A
## 10  Black     9            2  type B
## 11   Blue     6            4  type B
## 12    Red    14           13  type B
## 13 Yellow    15           15  type B
## 14  Black     5           10  type B
## 15   Blue     3            5  type B
## 16    Red     2            6  type B
## 17   Blue    12            7  type B
## 18    Red    10            9  type B
{% endhighlight %}



{% highlight r %}
#step1: split the data into groups based on some criteria (use the column or a combination of columns to split the data into groups)
#group by color
#step2: apply a function to each group independently (aggregate, transform, or filter the data in this step)
#step3: combine the results into a datastructure
sales_data%>%
  group_by(color)%>%
  summarise(totalSales = sum(sales),medianTrans=median(transactions),count=n())
{% endhighlight %}



{% highlight text %}
## Error: This function should not be called directly
## [90mCall `rlang::last_error()` to see a backtrace[39m
{% endhighlight %}








