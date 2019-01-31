---
title: "Split-apply-combine..."
author: "Jing Hou"
output: pdf_document
root: ../../../
layout: post
topic: '02'
---
1. **Which (base R) functions do you know that support the split-apply-combine strategy? In your opinion, are these sufficient - state why or why not?**. 

There are some base R functions that support the split-apply-combine strategy, such as split, aggregate, apply, lapply, mapply, rbind. In my opinion, these functions are sufficient because they can complete the job with nested loops. However, as mentioned in Hadley Wickham's paper, the code will be shorter and the work will be more efficient by using the plyr package.

2. **Using a dataset of your choice, show (by including the split-apply-combine command(s) in your answer) how you can use the split-apply-combine strategy for a part of the data analysis.**
 
 I choose one of the R build-in data sets: "PlantGrowth".

{% highlight r %}
# using base function
attach(PlantGrowth)
{% endhighlight %}



{% highlight text %}
## The following object is masked from chickwts:
## 
##     weight
{% endhighlight %}



{% highlight r %}
tapply(weight, group, mean)
{% endhighlight %}



{% highlight text %}
##  ctrl  trt1  trt2 
## 5.032 4.661 5.526
{% endhighlight %}



{% highlight r %}
tapply(weight, group, sd)
{% endhighlight %}



{% highlight text %}
##      ctrl      trt1      trt2 
## 0.5830914 0.7936757 0.4425733
{% endhighlight %}



{% highlight r %}
# using "plyr"
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
ddply(PlantGrowth, .(group), summarise, mean = mean(weight), sd = sd(weight))
{% endhighlight %}



{% highlight text %}
##   group  mean        sd
## 1  ctrl 5.032 0.5830914
## 2  trt1 4.661 0.7936757
## 3  trt2 5.526 0.4425733
{% endhighlight %}
