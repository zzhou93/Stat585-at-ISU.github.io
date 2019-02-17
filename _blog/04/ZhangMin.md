---
title: "Interesting times..."
author: "Min Zhang"
topic: "04"
layout: post
root: ../../../
---


## Background:

Dates and times can be difficult to work with. Watch [this video](https://www.youtube.com/watch?v=-5wpm-gesOY) to appreciate all of the fun scenarios that date/time libraries have to accommodate. 

Luckily, the `lubridate` package makes working with dates and times in R pretty straightforward. The package has been described in the paper [Working with date and time](http://www.jstatsoft.org/v40/i03/) by Garrett Grolemund and Hadley Wickham, an updated version of an intro to lubridate can be found in chapter 16 of [R for Data Science](https://r4ds.had.co.nz/dates-and-times.html). Read one of the two sources.

Write a blog post addressing the questions:


- Describe what intervals, durations, periods, and instants are, and give one example for each that shows why we need these distinctions.

1. Instant: an instant is a specific moment in time. E.g. We need it to represent a specific time point, which can be a day or some exact time point. 

2. Interval: an interval is a span of time that occurs between two specific instants. E.g. We can calculate the exact length of any unit of time that occurs during the interval. 

3. Duration: if we record the time span in seconds, it will have an exact length since seconds always have the same length. We call such time spans durations. E.g. Get the precise length of a time interval, which may not be easily understood when the time interval is quite long. 

4. Period: periods record a time span in units larger than seconds, such as years, months, weeks, days, hours and minutes. E.g. We can use periods to accurately model clock times without knowing when events such as leap days occur. And the length of the time span will depend on when it begins.  

- The `ggplot2` package works seamlessy with lubridate. Find a data set with dates and/or times, use lubridate to work with the dates/times, then plot a time-related aspect of the data and describe it.  

The dataset I use `airquality` is the daily air quality measurements in New York, May to September in year 1973. The variable `Ozone` is the mean ozone in parts per billion from 1300 to 1500 hours at Roosevelt Island.


{% highlight r %}
library("lubridate")
library("dplyr")
library("ggplot2")
library("tidyr")
{% endhighlight %}


{% highlight r %}
dat <- airquality
dat <- dat %>% mutate(Date = paste0(Month, "-", Day, "-", 1973)) %>% 
  mutate(Date = mdy(Date))

dat2 <- dat %>% select(Date, Ozone, Wind, Temp) %>% 
  gather(., "Measurement", "Value", -Date)
{% endhighlight %}



{% highlight text %}
## Error in select(., Date, Ozone, Wind, Temp): unused arguments (Date, Ozone, Wind, Temp)
{% endhighlight %}



{% highlight r %}
ggplot(dat2, aes(x = Date, y = Value, colour = Measurement)) + 
  geom_line() +
  stat_smooth() +
  theme_classic()
{% endhighlight %}



{% highlight text %}
## Error in ggplot(dat2, aes(x = Date, y = Value, colour = Measurement)): object 'dat2' not found
{% endhighlight %}

There are 37 missing values of ozone in the dataset. As can be seen from the plot, maximum daily temperature climbed up from May to mid-August and dropped down afterwards. Mean ozone tended to have similar pattern as maximum daily temperature. And the average wind speed remained pretty stable. 
