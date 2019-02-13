---
title: "Interesting times..."
author: "Virginia Nichols"
topic: "04"
layout: post
root: ../../../
---


#Describe what intervals, durations, periods, and instants are, and give one example for each that shows why we need these distinctions.

Interesting.

**Durations** represent exact number of seconds. To convert to larger units, they use a standard convertion rate.  
*How long can I hold my breath?*
I want to know the exact amount of seconds. Whether it is a leap year is irrelevant. 

**Periods** are human units (weeks/months) 
*How many months does it take you to write a paper?*
This is not an exact value, but rather a general value that is best represented in month chunks. 

**Intervals** have a starting and ending point and operate in human units. 
*How long is the spring semester?*
It starts on Jan X and ends on May X. 

#The `ggplot2` package works seamlessy with lubridate. Find a data set with dates and/or times, use lubridate to work with the dates/times, then plot a time-related aspect of the data and describe it.**  

We'll do the typical one - NYC flights. 


{% highlight r %}
dat <- flights
head(flights)
{% endhighlight %}



{% highlight text %}
## # A tibble: 6 x 19
##    year month   day dep_time sched_dep_time dep_delay arr_time
##   <int> <int> <int>    <int>          <int>     <dbl>    <int>
## 1  2013     1     1      517            515         2      830
## 2  2013     1     1      533            529         4      850
## 3  2013     1     1      542            540         2      923
## 4  2013     1     1      544            545        -1     1004
## 5  2013     1     1      554            600        -6      812
## 6  2013     1     1      554            558        -4      740
## # ... with 12 more variables: sched_arr_time <int>, arr_delay <dbl>,
## #   carrier <chr>, flight <int>, tailnum <chr>, origin <chr>, dest <chr>,
## #   air_time <dbl>, distance <dbl>, hour <dbl>, minute <dbl>,
## #   time_hour <dttm>
{% endhighlight %}



{% highlight r %}
names(flights)
{% endhighlight %}



{% highlight text %}
##  [1] "year"           "month"          "day"            "dep_time"      
##  [5] "sched_dep_time" "dep_delay"      "arr_time"       "sched_arr_time"
##  [9] "arr_delay"      "carrier"        "flight"         "tailnum"       
## [13] "origin"         "dest"           "air_time"       "distance"      
## [17] "hour"           "minute"         "time_hour"
{% endhighlight %}

Yuck. It has lots of *date-y* things. Let's see if any origins have become more popular by month


{% highlight r %}
flights %>%
  group_by(month, origin) %>%
  summarise(n = n()) %>%
  ggplot(aes(month, n)) + 
  geom_line(aes(color = origin))
{% endhighlight %}



{% highlight text %}
## Error: This function should not be called directly
{% endhighlight %}

The months are labeled weird, I'd rather have the words. 


{% highlight r %}
flights %>%
  mutate(month2 = month(month, label = T)) %>%
  group_by(month2, origin) %>%
  summarise(n = n()) %>%
  
  ggplot(aes(month2, n)) + 
  geom_point(aes(color = origin))
{% endhighlight %}



{% highlight text %}
## Error: This function should not be called directly
{% endhighlight %}

But now it won't connect them with a line. Oh well. At least they are in the right order. 

