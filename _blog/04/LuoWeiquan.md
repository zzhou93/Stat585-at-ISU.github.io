---
title: "Interesting times..."
author: "Weiquan Luo"
topic: "04"
layout: post
root: ../../../
---

Describe what intervals, durations, periods, and instants are, and give one example for each that shows why we need these distinctions.

* If you only care about physical time, use a `durations`, which represent an exact number of seconds.(e.g. 15324 second)
* If you need to add human times, use a `periods`, which represent human units like weeks and months.(e.g. 5month 0 day 0 Hour 0 Minutes 13 Seconds)
* If you need to figure out how long a span is in human units, use an `intervals`, which represent a starting and ending point. (e.g. )
* If you need to reference a precise moment of time. is `instants`, which represent a specific time including a date, a time, or a date plus a time (e.g. 2019-01-08 15:37:18 UTC)

The `ggplot2` package works seamlessy with lubridate. Find a data set with dates and/or times, use lubridate to work with the dates/times, then plot a time-related aspect of the data and describe it.  

* I modify the code in chapter 16 of [R for Data Science]. The resulting plot is th the number of weekly schedule departure flights over the yeer.


{% highlight r %}
library(lubridate)
library(tidyverse)
library(nycflights13)
{% endhighlight %}


{% highlight r %}
make_datetime_100 <- function(year, month, day, time) {
  make_datetime(year, month, day, time %/% 100, time %% 100)
}

flights_sdt <- flights %>% 
  filter(!is.na(dep_time), !is.na(arr_time)) %>% 
  mutate(
    dep_time = make_datetime_100(year, month, day, dep_time),
    arr_time = make_datetime_100(year, month, day, arr_time),
    sched_dep_time = make_datetime_100(year, month, day, sched_dep_time),
    sched_arr_time = make_datetime_100(year, month, day, sched_arr_time)
  ) %>%   
  select(origin, dest, ends_with("delay"), ends_with("time"))
{% endhighlight %}



{% highlight text %}
## Error in select(., origin, dest, ends_with("delay"), ends_with("time")): unused arguments (origin, dest, ends_with("delay"), ends_with("time"))
{% endhighlight %}



{% highlight r %}
flights_sdt %>% 
  ggplot(aes(sched_dep_time)) + 
  geom_freqpoly(binwidth = 86400*7)
{% endhighlight %}



{% highlight text %}
## Error in eval(lhs, parent, parent): object 'flights_sdt' not found
{% endhighlight %}
