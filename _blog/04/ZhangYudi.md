---
title: "Interesting times..."
author: "Yudi Zhang"
topic: "04"
layout: post
root: ../../../
---


## Background:

Dates and times can be difficult to work with. Watch [this video](https://www.youtube.com/watch?v=-5wpm-gesOY) to appreciate all of the fun scenarios that date/time libraries have to accommodate. 

Luckily, the `lubridate` package makes working with dates and times in R pretty straightforward. The package has been described in the paper [Working with date and time](http://www.jstatsoft.org/v40/i03/) by Garrett Grolemund and Hadley Wickham, an updated version of an intro to lubridate can be found in chapter 16 of [R for Data Science](https://r4ds.had.co.nz/dates-and-times.html). Read one of the two sources.

Write a blog post addressing the questions:


- Describe what intervals, durations, periods, and instants are, and give one example for each that shows why we need these distinctions.

Durations, an exact number of seconds. Durations always record the time span in seconds. If we want to compute the seconds for two months Feb and Mar, then using Periods would do 31*2*2600, which is wrong, that is when we use duration.
Periods, human units like weeks and months. When there is a leap year, periods can show us what we expected. For example, ymd("2016-01-01") + years(1) is "2017-01-01", but if using durations, it is "2016-12-31".
Intervals, a starting and ending point. Intervals give us a more accurate measurement, e.g. if we want to know number of days in year 2016, Intervals can return 366, not periods.
Instants: a specific instant in time. For example, if a murder happened, the police want to know the exact time, that's when we use instants.

- The `ggplot2` package works seamlessy with lubridate. Find a data set with dates and/or times, use lubridate to work with the dates/times, then plot a time-related aspect of the data and describe it.  
The following dataset contains wind speed and direction at some time in every day in year 2007. Plot the averge wind speed each day in that year.


{% highlight r %}
library(tidyverse)
library(lubridate)
library(rnoaa)

wind <- buoy(dataset = 'cwind', buoyid = 46085)
{% endhighlight %}



{% highlight text %}
## Error: Please install 'ncdf4'
{% endhighlight %}



{% highlight r %}
wind <- wind$data
wind$time <- ymd_hms(wind$time)
wind %>% 
  mutate(date = date(time)) %>% 
  group_by(date) %>% 
  mutate(mean_spd = mean(wind_spd)) %>% 
  ggplot() +
  geom_line(aes(x = date, y = mean_spd)) + 
  ggtitle("Mean Wind Speed per Month in Year 2007") +
  theme_bw() +
  theme(plot.title = element_text(hjust = 0.5))
{% endhighlight %}



{% highlight text %}
## Error in UseMethod("mutate_"): no applicable method for 'mutate_' applied to an object of class "list"
{% endhighlight %}
