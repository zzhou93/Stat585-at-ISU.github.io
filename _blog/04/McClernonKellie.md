---
title: "Blog Post 4: Interesting times"
author: "Kellie McClernon"
topic: "04"
layout: post
root: ../../../
---


## Background:

Dates and times can be difficult to work with. Watch [this video](https://www.youtube.com/watch?v=-5wpm-gesOY) to appreciate all of the fun scenarios that date/time libraries have to accommodate. 

Luckily, the `lubridate` package makes working with dates and times in R pretty straightforward. The package has been described in the paper [Working with date and time](http://www.jstatsoft.org/v40/i03/) by Garrett Grolemund and Hadley Wickham, an updated version of an intro to lubridate can be found in chapter 16 of [R for Data Science](https://r4ds.had.co.nz/dates-and-times.html). Read one of the two sources.

Write a blog post addressing the questions:  

- Describe what intervals, durations, periods, and instants are, and give one example for each that shows why we need these distinctions.  

Instants are one date or date/time point, e.g. July 4, 1776. Intervals are the difference between two instants. Intervals have a definite start and end point, whereas durations and periods do not. Durations and periods are hence simply spans of time without reference to a specific point in history. Durations are timespans in seconds, while periods can have larger units such as days, months, etc.  

For example, the bicentennial anniversity of the United States was on July 4, 1976; this is an **instant**. The 200 years between July 4, 1776 and July 4, 1976 is an instance of an **interval**, an interval of 200 years. On the other hand, 200 years is a **period**. But due to the complication of leap years and daylight savings time, it is difficult to say how many days there are in any given 200 year time period.  This confusion leads to the construction of a **duration**.

On March 11, 2018 at 2:00 AM, Ames Iowa switched from Central Standard Time to Central Daylight Savings Time. Therefore, a **period** of 3 hours starting at 1:00 AM on March 11 2018 ended at 4:00 AM, but a **duration** of 3 hours (10800 seconds) would have ended at 5:00 AM. Durations give us a way to establish the passage of time regardless of constructions such as timezones, daylight savings, and others. Periods give us time spans in familiar units that adjust for the idiosyncrasies we naturally deal with in recorded time (e.g. timezones, etc.). (Notice the timezone stamp changes below.)  


{% highlight r %}
library(lubridate)

(day <- ymd_hm(201803110100, tz = "America/Chicago")) # start time
{% endhighlight %}



{% highlight text %}
## [1] "2018-03-11 01:00:00 CST"
{% endhighlight %}



{% highlight r %}
day + hours(3) # + period of 3 hours
{% endhighlight %}



{% highlight text %}
## [1] "2018-03-11 04:00:00 CDT"
{% endhighlight %}



{% highlight r %}
day + dhours(3) # + duration of 3 hours
{% endhighlight %}



{% highlight text %}
## [1] "2018-03-11 05:00:00 CDT"
{% endhighlight %}

- The `ggplot2` package works seamlessy with lubridate. Find a data set with dates and/or times, use lubridate to work with the dates/times, then plot a time-related aspect of the data and describe it.  

We can use the `lubridate` package to convert the time-series data set containing average monthly temperatures in Nottingham Castle from 1920-1939 into a data frame. Using the period function for months, we create a date variable for month and year starting from January 1920. Using `ggplot2` and `dplyr`, we graph the average monthly temperature across all 19 years of the data set. However, we want the label of the months on the x-axis, so we can specify the label option in the month extraction function from `lubridate`.


{% highlight r %}
library(tidyverse)
library(lubridate)

notting_temp <- data.frame(temp = nottem, day = ymd("1920-01-01") + months(0:239)) %>%
  mutate(year = year(day), month = month(day, label = TRUE))

notting_temp %>% group_by(month) %>% summarise(avg_temp = mean(temp)) %>%
  ggplot(aes(month, avg_temp)) + geom_point(size = 3) + ylab("Average Temperature (F)")
{% endhighlight %}



{% highlight text %}
## Error: Column `x` must be a 1d atomic vector or a list
{% endhighlight %}

![center](../figure/04/McClernonKellie/getdata-1.png)

As expected, the graph shows us a rise in temperature during the summer months and a decline in the winter. Compared to the US Midwest, which experiences temperature differences from winter to summer as large as 110 degrees, the castle stays a relatively constant mild temperature. Stone is a suprisingly good temperature regulator.
