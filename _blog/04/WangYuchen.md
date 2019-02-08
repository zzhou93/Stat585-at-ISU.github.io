---
title: "Interesting times..."
author: "Yuchen Wang"
topic: "04"
layout: post
root: ../../../
---

- Describe what intervals, durations, periods, and instants are, and give one example for each that shows why we need these distinctions.
-Instant: a specific time

{% highlight r %}
library(lubridate)
library(tidyverse)
example_instant <- ymd_hms("2019-01-01 18:00:00")
is.instant(example_instant)
{% endhighlight %}



{% highlight text %}
## [1] TRUE
{% endhighlight %}

-Intervals: the time between two specific times.

{% highlight r %}
example_interval <- ymd_hms("2019-02-01 17:00:00") - ymd_hms("2019-01-01 18:00:00")
example_instant + example_interval
{% endhighlight %}



{% highlight text %}
## [1] "2019-02-01 17:00:00 UTC"
{% endhighlight %}

-Durations: time span (interval) in specific unit "seconds".

{% highlight r %}
example_duration <- as.duration(example_interval)
example_duration
{% endhighlight %}



{% highlight text %}
## [1] "2674800s (~4.42 weeks)"
{% endhighlight %}

-Periods: time span (interval) in other units which are larger than seconds.

{% highlight r %}
example_period <- as.period(example_interval)
example_period
{% endhighlight %}



{% highlight text %}
## [1] "30d 23H 0M 0S"
{% endhighlight %}


- The `ggplot2` package works seamlessy with lubridate. Find a data set with dates and/or times, use lubridate to work with the dates/times, then plot a time-related aspect of the data and describe it.  

{% highlight r %}
ames_weather <- read_csv("https://raw.githubusercontent.com/Stat585-at-ISU/materials-2019/master/data/Ames_weather_2017-2018.csv")
{% endhighlight %}



{% highlight text %}
## Parsed with column specification:
## cols(
##   date = col_date(format = ""),
##   time = col_character(),
##   icon = col_integer(),
##   wind = col_integer(),
##   temp_low = col_integer(),
##   temp_high = col_integer(),
##   weather = col_character()
## )
{% endhighlight %}



{% highlight r %}
ames_weather <- ames_weather %>%
  na.omit() %>%
  mutate(date = ymd(date),
         year = year(date),
         month = month(date),
         day = day(date))

ames_18 <-ames_weather %>%
  filter(year == 2018) %>%
  filter(weather == "Clear.") %>% 
  group_by(month) %>%
  summarize(
        count = n(),
        mean_wind = mean (wind))
ames_18 %>%
  ggplot(aes(x=as.factor(month),y=mean_wind,size = count,color = count)) + geom_point(position = "dodge") + labs (title = "Clear Days in 2018", x = "Month", y = "MeanWind" ) 
{% endhighlight %}



{% highlight text %}
## Warning: Width not defined. Set with `position_dodge(width = ?)`
{% endhighlight %}

![center](../figure/04/WangYuchen/unnamed-chunk-5-1.png)
It looks like there is no relationship between the mean wind speed and the amount of clear days in every month.

