---
title: "Interesting times..."
author: "Hana Lee"
topic: "04"
layout: post
root: ../../../
---

Write a blog post addressing the questions:


- Describe what intervals, durations, periods, and instants are, and give one example for each that shows why we need these distinctions.

Time spans can be represented by the following classes with `lubridate`: durations, periods, and intervals.

- Durations represent a time span in seconds.
- Periods represent a time span in human units such as in weeks and in months.
- Intervals represent a starting and ending points of a time span.

Let's take look at the examples for the three classes. How old is STAT 585 class of 2019 since its first lecture started?


{% highlight r %}
library(lubridate)
stat.585.begin <- ymd_hms("2019-01-14 16:10:00", tz = "America/Chicago")
stat.585.age <- now(tz = "America/Chicago") - 
                stat.585.begin

(duration <- as.duration(stat.585.age))
{% endhighlight %}



{% highlight text %}
## [1] "2750611.76117706s (~4.55 weeks)"
{% endhighlight %}



{% highlight r %}
(period <- today(tz = "America/Chicago") - date(stat.585.begin))
{% endhighlight %}



{% highlight text %}
## Time difference of 32 days
{% endhighlight %}



{% highlight r %}
(interval <- stat.585.begin %--% now(tz = "America/Chicago"))
{% endhighlight %}



{% highlight text %}
## [1] 2019-01-14 16:10:00 CST--2019-02-15 12:13:31 CST
{% endhighlight %}



{% highlight r %}
interval / ddays(1)
{% endhighlight %}



{% highlight text %}
## [1] 31.83578
{% endhighlight %}



- The `ggplot2` package works seamlessy with lubridate. Find a data set with dates and/or times, use lubridate to work with the dates/times, then plot a time-related aspect of the data and describe it.  


#### Import data

{% highlight r %}
library(tidyverse)
dat.url <- "https://raw.githubusercontent.com/hnlee1428/Initial-stat-585/master/DEXKOUS.csv"
dat <- read.csv(dat.url, header = TRUE)
head(dat)
{% endhighlight %}



{% highlight text %}
##         DATE   DEXKOUS
## 1 2014-02-10 1072.3000
## 2 2014-02-11 1070.8000
## 3 2014-02-12 1062.1400
## 4 2014-02-13 1066.2000
## 5 2014-02-14 1062.9000
## 6 2014-02-17         .
{% endhighlight %}



{% highlight r %}
str(dat)
{% endhighlight %}



{% highlight text %}
## 'data.frame':	1305 obs. of  2 variables:
##  $ DATE   : Factor w/ 1305 levels "2014-02-10","2014-02-11",..: 1 2 3 4 5 6 7 8 9 10 ...
##  $ DEXKOUS: Factor w/ 1187 levels ".","1008.8500",..: 231 214 143 175 147 1 167 163 228 229 ...
{% endhighlight %}

#### Manipulate a variable related to date

{% highlight r %}
d <- dat %>% 
  mutate(DATE = ymd(as.character(DATE)),
         `South Korean Won to One U.S. Dollar` = as.numeric(as.character(DEXKOUS))) %>%
  select(-DEXKOUS)
{% endhighlight %}



{% highlight text %}
## Error in select(., -DEXKOUS): unused argument (-DEXKOUS)
{% endhighlight %}



{% highlight r %}
#warning message doesn't matter
str(d)
{% endhighlight %}



{% highlight text %}
## Error in str(d): object 'd' not found
{% endhighlight %}



{% highlight r %}
head(d)        
{% endhighlight %}



{% highlight text %}
## Error in head(d): object 'd' not found
{% endhighlight %}

#### Plot of South Korean Won to One U.S. Dollar from 2017 to now

{% highlight r %}
d %>%
  filter(ymd(20190213)>DATE & DATE>ymd(20161231)) %>%
  ggplot(aes(x = DATE,
             y = `South Korean Won to One U.S. Dollar`)) +
  geom_line() + geom_point()
{% endhighlight %}



{% highlight text %}
## Error in eval(lhs, parent, parent): object 'd' not found
{% endhighlight %}

It appears that the value of South Korean Won to One U.S.D. was relatively higher from the end of 2017 to June 2018. I remember that I hesitated to exchange Korean Won for my stipend during the time frame since I expected more benefit by the value difference as time goes. However, I missed the chance, and couldn't get the chance again up to now.
