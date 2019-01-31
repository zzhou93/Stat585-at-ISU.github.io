---
title: "Split apply combine ..."
author: "Zhenzhen Chen"
topic: "02"
layout: post
root: ../../../
---


1. **Which (base R) functions do you know that support the split-apply-combine strategy? In your opinion, are these sufficient - state why or why not?**. 

There are some R function that can support the split-apply-combine strategy,such as "split()", "apply()", "tapply()", 
"aggregate()" etc.


2. **Using a dataset of your choice, show (by including the split-apply-combine command(s) in your answer) how you can use the split-apply-combine strategy for a part of the data analysis.**

I accessed a built-in dataset that calls chickwts. 

{% highlight r %}
attach(chickwts)
{% endhighlight %}



{% highlight text %}
## The following object is masked from PlantGrowth (pos = 4):
## 
##     weight
{% endhighlight %}



{% highlight text %}
## The following objects are masked from chickwts (pos = 6):
## 
##     feed, weight
{% endhighlight %}



{% highlight text %}
## The following object is masked from PlantGrowth (pos = 7):
## 
##     weight
{% endhighlight %}



{% highlight text %}
## The following objects are masked from chickwts (pos = 10):
## 
##     feed, weight
{% endhighlight %}



{% highlight text %}
## The following object is masked from PlantGrowth (pos = 11):
## 
##     weight
{% endhighlight %}



{% highlight text %}
## The following objects are masked from chickwts (pos = 13):
## 
##     feed, weight
{% endhighlight %}



{% highlight text %}
## The following object is masked from PlantGrowth (pos = 14):
## 
##     weight
{% endhighlight %}



{% highlight text %}
## The following objects are masked from chickwts (pos = 16):
## 
##     feed, weight
{% endhighlight %}



{% highlight text %}
## The following object is masked from PlantGrowth (pos = 17):
## 
##     weight
{% endhighlight %}



{% highlight text %}
## The following objects are masked from chickwts (pos = 19):
## 
##     feed, weight
{% endhighlight %}



{% highlight r %}
wm <- tapply(weight, feed,  mean) 
wsd <- tapply(weight,  feed, sd)
{% endhighlight %}

If using the `plyr` package,

{% highlight r %}
library(tidyverse); library(plyr);
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
ddply(chickwts, .(feed), summarise, mean = mean(weight), sd = sd(weight))
{% endhighlight %}



{% highlight text %}
##        feed     mean       sd
## 1    casein 323.5833 64.43384
## 2 horsebean 160.2000 38.62584
## 3   linseed 218.7500 52.23570
## 4  meatmeal 276.9091 64.90062
## 5   soybean 246.4286 54.12907
## 6 sunflower 328.9167 48.83638
{% endhighlight %}




