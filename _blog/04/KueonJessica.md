---
title: "Interesting times..."
author: "Jessica Kueon
topic: "04"
layout: post
root: ../../../
---




1. Describe what intervals, durations, periods, and instants are, and give one example for each that shows why we need these distinctions.

- Intervals: The paper says intervals, durations and periods have the same purpose, which is describing timespans. The simplest one would be the intervals. Ex: 06/17/1989 ~ 02/10/2019. If we calculate the length of time between the intervals, that would create an duration. 


- Durations: Length of time in an interval. Useful when it comes to calculating speeds, rates, or lifetimes. EX: 47 minutes


- Periods: Duration with larger units. Ex: 29 years and 3 months


- Instants: A specific moment in time. Good example would be June 17th, 1989. This could be created by parsing a date in to R. It tells us when the period occurs, which allows us to calculate its exact length in seconds.





2. The `ggplot2` package works seamlessy with lubridate. Find a data set with dates and/or times, use lubridate to work with the dates/times, then plot a time-related aspect of the data and describe it.  

- I will use "nycflights13" dataset, a dataset on Airline on-time data for all flights departing NYC in 2013.


{% highlight r %}
library(tidyverse)
library(nycflights13)
library(lubridate)
flights %>%
  select (year, month,day, hour, minute, arr_time)
{% endhighlight %}



{% highlight text %}
## # A tibble: 336,776 x 6
##     year month   day  hour minute arr_time
##    <int> <int> <int> <dbl>  <dbl>    <int>
##  1  2013     1     1     5     15      830
##  2  2013     1     1     5     29      850
##  3  2013     1     1     5     40      923
##  4  2013     1     1     5     45     1004
##  5  2013     1     1     6      0      812
##  6  2013     1     1     5     58      740
##  7  2013     1     1     6      0      913
##  8  2013     1     1     6      0      709
##  9  2013     1     1     6      0      838
## 10  2013     1     1     6      0      753
## # ... with 336,766 more rows
{% endhighlight %}



{% highlight r %}
flights %>%
  select(year, month, day, hour, minute) %>%
  mutate(departure = make_datetime(year, month,day, hour, minute)
        )
{% endhighlight %}



{% highlight text %}
## # A tibble: 336,776 x 6
##     year month   day  hour minute departure          
##    <int> <int> <int> <dbl>  <dbl> <dttm>             
##  1  2013     1     1     5     15 2013-01-01 05:15:00
##  2  2013     1     1     5     29 2013-01-01 05:29:00
##  3  2013     1     1     5     40 2013-01-01 05:40:00
##  4  2013     1     1     5     45 2013-01-01 05:45:00
##  5  2013     1     1     6      0 2013-01-01 06:00:00
##  6  2013     1     1     5     58 2013-01-01 05:58:00
##  7  2013     1     1     6      0 2013-01-01 06:00:00
##  8  2013     1     1     6      0 2013-01-01 06:00:00
##  9  2013     1     1     6      0 2013-01-01 06:00:00
## 10  2013     1     1     6      0 2013-01-01 06:00:00
## # ... with 336,766 more rows
{% endhighlight %}



{% highlight r %}
make_datetime_100 <-  function(year, month, day, time){
  make_datetime(year, month, day, time %/% 100, time %% 100)
}
flights_dt <-  flights %>%
  filter(!is.na(dep_time), !is.na(arr_time)) %>%
  mutate(
    dep_time = make_datetime_100(year, month, day, dep_time),
    arr_time = make_datetime_100(year, month, day, arr_time),
    sched_dep_time = make_datetime_100(year, month, day, sched_dep_time),
    sched_arr_time = make_datetime_100(year, month, day, sched_arr_time)
  ) 
flights_dt %>%
  select(origin, dest, ends_with("delay"), ends_with("time"))
{% endhighlight %}



{% highlight text %}
## # A tibble: 328,063 x 9
##    origin dest  dep_delay arr_delay dep_time            sched_dep_time     
##    <chr>  <chr>     <dbl>     <dbl> <dttm>              <dttm>             
##  1 EWR    IAH           2        11 2013-01-01 05:17:00 2013-01-01 05:15:00
##  2 LGA    IAH           4        20 2013-01-01 05:33:00 2013-01-01 05:29:00
##  3 JFK    MIA           2        33 2013-01-01 05:42:00 2013-01-01 05:40:00
##  4 JFK    BQN          -1       -18 2013-01-01 05:44:00 2013-01-01 05:45:00
##  5 LGA    ATL          -6       -25 2013-01-01 05:54:00 2013-01-01 06:00:00
##  6 EWR    ORD          -4        12 2013-01-01 05:54:00 2013-01-01 05:58:00
##  7 EWR    FLL          -5        19 2013-01-01 05:55:00 2013-01-01 06:00:00
##  8 LGA    IAD          -3       -14 2013-01-01 05:57:00 2013-01-01 06:00:00
##  9 JFK    MCO          -3        -8 2013-01-01 05:57:00 2013-01-01 06:00:00
## 10 LGA    ORD          -2         8 2013-01-01 05:58:00 2013-01-01 06:00:00
## # ... with 328,053 more rows, and 3 more variables: arr_time <dttm>,
## #   sched_arr_time <dttm>, air_time <dbl>
{% endhighlight %}



{% highlight r %}
## Visualizing a time series!

flights_dt %>%
filter(dep_time < ymd(20130102)) %>%
  ggplot(aes(dep_time)) +
  geom_freqpoly(binwidth = 600)
{% endhighlight %}

![center](../figure/04/KueonJessica/unnamed-chunk-1-1.png)

