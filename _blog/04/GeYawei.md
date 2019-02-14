---
title: "Interesting times..."
author: "Yawei Ge"
topic: "04"
layout: post
root: ../../../
---



**1. Describe what intervals, durations, periods, and instants are, and give one example for each that shows why we need these distinctions.**

The "duration" is an exact number of seconds;

The "period"" is a time span denoted by human units, i.e, year, month, day, etc; 

The "interval" is a "period" with a specified starting point and/or ending point.

###Duration

When we are calulating with time span for scientic purpose, or pure mathematical calculation which doesn't contain any human units within the process, we need "duration", for it is consistent in transforming year and day, i.e, 1 year = 365 days, and has consistent unit as second, which is more predictable in this case.


{% highlight r %}
#duration
ddays(1)
{% endhighlight %}



{% highlight text %}
## [1] "86400s (~1 days)"
{% endhighlight %}



{% highlight r %}
2*dyears(1)
{% endhighlight %}



{% highlight text %}
## [1] "63072000s (~2 years)"
{% endhighlight %}



{% highlight r %}
dweeks(1) - dseconds(10000)
{% endhighlight %}



{% highlight text %}
## Note: method with signature 'Duration#ANY' chosen for function '-',
##  target signature 'Duration#Duration'.
##  "ANY#Duration" would also be valid
{% endhighlight %}



{% highlight text %}
## [1] "594800s (~6.88 days)"
{% endhighlight %}

###Period

However, if we are doing data analysis and transforming date and time with human units, we want to explictly know what date/time our data points represent, we will need "period"" to do that. 


{% highlight r %}
#period
days(3) + hours(4) + seconds(10)
{% endhighlight %}



{% highlight text %}
## [1] "3d 4H 0M 10S"
{% endhighlight %}



{% highlight r %}
3*(years(4) + months(3))
{% endhighlight %}



{% highlight text %}
## [1] "12y 9m 0d 0H 0M 0S"
{% endhighlight %}

###Interval

And if we have to take into consideration about leap year and DST etc, we must specify a particular starting point or ending point and use "interval" in this case.


{% highlight r %}
#interval
today() %--% (today() + years(5))
{% endhighlight %}



{% highlight text %}
## [1] 2019-02-13 UTC--2024-02-13 UTC
{% endhighlight %}



{% highlight r %}
(today() %--% (today() + years(5))) / days(1)/365
{% endhighlight %}



{% highlight text %}
## [1] 5.00274
{% endhighlight %}



{% highlight r %}
#because of leap year, not exact 5
{% endhighlight %}

Whenever possible, use the simplest one that satisfying your purpose.

**2. The ggplot2 package works seamlessy with lubridate. Find a data set with dates and/or times, use lubridate to work with the dates/times, then plot a time-related aspect of the data and describe it.**

###Average sales of houses in TX, 2013

We can see from the following plot that there is a clear seasonal trend in the year. From January, the lowest point, the sales go up all the way until May and stay at the peak(more than twice in sales compared to the lowest point) until August and then go down again. So we may need to take this into consideration when doing analysis with house sales using this dataset.


{% highlight r %}
data("txhousing")
head(txhousing)
{% endhighlight %}



{% highlight text %}
## # A tibble: 6 x 9
##   city     year month sales   volume median listings inventory  date
##   <chr>   <int> <int> <dbl>    <dbl>  <dbl>    <dbl>     <dbl> <dbl>
## 1 Abilene  2000     1    72  5380000  71400      701       6.3 2000 
## 2 Abilene  2000     2    98  6505000  58700      746       6.6 2000.
## 3 Abilene  2000     3   130  9285000  58100      784       6.8 2000.
## 4 Abilene  2000     4    98  9730000  68600      785       6.9 2000.
## 5 Abilene  2000     5   141 10590000  67300      794       6.8 2000.
## 6 Abilene  2000     6   156 13910000  66900      780       6.6 2000.
{% endhighlight %}



{% highlight r %}
txhousing <- txhousing %>%
  mutate(new_date = make_date(year, month))

txhousing %>%
  filter(!is.na(volume), year == 2013) %>%
  group_by(new_date) %>%
  mutate(avg_volume = mean(volume)) %>%
  ggplot(aes(x = new_date, y = avg_volume)) + 
  geom_line()
{% endhighlight %}

![center](../figure/04/GeYawei/unnamed-chunk-5-1.png)
