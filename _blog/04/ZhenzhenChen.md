---
title: "Interesting times..."
author: "Zhenzhen Chen"
topic: "04"
layout: post
root: ../../../
---


Write a blog post addressing the questions:


- Describe what intervals, durations, periods, and instants are, and give one example for each that shows why we need these distinctions.

Intervals, durations, periods, and instants are the four time related objecteds in lubridate.

Instants shows you a specific moment in time, for example,

{% highlight r %}
library(lubridate)
tim <- now()
tim
{% endhighlight %}



{% highlight text %}
## [1] "2019-02-13 23:23:38 CST"
{% endhighlight %}



{% highlight r %}
is.instant(tim)
{% endhighlight %}



{% highlight text %}
## [1] TRUE
{% endhighlight %}

Intervals is the simplest one to shows a timespan. It can tell you exact the length of time. For example, since we already know the instants, we can calculate the interval between two or more instants. 

{% highlight r %}
tim1 <- now()
tim2 <- ymd_hms("2019.2.14 12:00:00")
sp   <- tim2 - tim1
sp
{% endhighlight %}



{% highlight text %}
## Time difference of 6.60607 hours
{% endhighlight %}
Duration is fixed, it isn't change. We have exact length for each seconds, since duration is measured in seconds. 

{% highlight r %}
dseconds(50)
{% endhighlight %}



{% highlight text %}
## [1] "50s"
{% endhighlight %}



{% highlight r %}
dminutes(50)
{% endhighlight %}



{% highlight text %}
## [1] "3000s (~50 minutes)"
{% endhighlight %}



{% highlight r %}
ddays(2)
{% endhighlight %}



{% highlight text %}
## [1] "172800s (~2 days)"
{% endhighlight %}
Since we already know interval, we can also added and subtracted interval to duration, for example,

{% highlight r %}
now() + ddays(108)
{% endhighlight %}



{% highlight text %}
## [1] "2019-06-02 00:23:38 CDT"
{% endhighlight %}



{% highlight r %}
tim2 - dyears(1)
{% endhighlight %}



{% highlight text %}
## [1] "2018-02-14 12:00:00 UTC"
{% endhighlight %}
Periods records a timespan that larger than the unit in seconds, for example, miuntes, days, months, years. Period not like duration, it is no longer has invariable length. Be specific,

{% highlight r %}
years(1)
{% endhighlight %}



{% highlight text %}
## [1] "1y 0m 0d 0H 0M 0S"
{% endhighlight %}



{% highlight r %}
months(2)
{% endhighlight %}



{% highlight text %}
## [1] "2m 0d 0H 0M 0S"
{% endhighlight %}



{% highlight r %}
years(1) + months(2)
{% endhighlight %}



{% highlight text %}
## [1] "1y 2m 0d 0H 0M 0S"
{% endhighlight %}
We can added instants, intervals, and period to one period, but we can not added duration. The following last line shows error messgae, since we add period to duration. 

{% highlight r %}
years(1) + tim2
{% endhighlight %}



{% highlight text %}
## [1] "2020-02-14 12:00:00 UTC"
{% endhighlight %}



{% highlight r %}
years(1) + dminutes(1)
{% endhighlight %}



{% highlight text %}
## Error in years(1) + dminutes(1): Arithmetic operators undefined for 'Period' and 'Duration' classes:
##   convert one to numeric or a matching time-span class.
{% endhighlight %}


- The `ggplot2` package works seamlessy with lubridate. Find a data set with dates and/or times, use lubridate to work with the dates/times, then plot a time-related aspect of the data and describe it. 

The data set I found is R buil-din dataset which calls "Death". It recorded the monthly deaths from bronchitis, emphysema, and asthma in the United Kingdom from 1974-1979. 

{% highlight r %}
library(lubridate)
library(ggplot2)
library(tidyverse)
##install.packages(ggfortify)
##install.packages(zoo)
library(ggfortify)
{% endhighlight %}



{% highlight text %}
## Error in library(ggfortify): there is no package called 'ggfortify'
{% endhighlight %}



{% highlight r %}
library(zoo)

data1 <- fortify(deaths)
{% endhighlight %}



{% highlight text %}
## Error: `data` must be a data frame, or other object coercible by `fortify()`, not an S3 object with class ts
{% endhighlight %}



{% highlight r %}
data1 %>%
  mutate(yearmd = ymd(Index), month = month(Index)) %>%
  ggplot( aes(x = yearmd, y = Data)) + 
  geom_line() + 
  geom_smooth(method = "auto")+
  xlab("Year") +
  ylab("Death") + 
  theme_bw()
{% endhighlight %}



{% highlight text %}
## Error in eval(lhs, parent, parent): object 'data1' not found
{% endhighlight %}
Based on the result, we can tell these five years(from 1974 to 1979), the death number from these lung diseases has decreased. However, for each year, we can also see that Jan and Feb are the two months which has the highest death occurrence. May and Jun have the lowest death occurrence because of lung diseases. 

