---
title: "Interesting times..."
author: "Yones Khaledian"
topic: "04"
layout: post
root: ../../../
---


## Background:

Dates and times can be difficult to work with. Watch [this video](https://www.youtube.com/watch?v=-5wpm-gesOY) to appreciate all of the fun scenarios that date/time libraries have to accommodate. 

Luckily, the `lubridate` package makes working with dates and times in R pretty straightforward. The package has been described in the paper [Working with date and time](http://www.jstatsoft.org/v40/i03/) by Garrett Grolemund and Hadley Wickham, an updated version of an intro to lubridate can be found in chapter 16 of [R for Data Science](https://r4ds.had.co.nz/dates-and-times.html). Read one of the two sources.

Write a blog post addressing the questions:


- Describe what intervals, durations, periods, and instants are, and give one example for each that shows why we need these distinctions.

Interval () makes an interval object that specified start and end dates. If the start date happens before the end date, the interval is positive, otherwise, it is negative. For example, I plan to go to a conference in Europe during the summer. In the same time, I plan to visit a friend in the US. I can check whether my plans overlapped or not. Or, I shift the start and end dates of my plans. Also, adjust my second plan (visiting the friend) based on the attending the conference. 

Duration() provides mathematically precise results. For example, we can find 90 days equal with how many weeks and seconds.  Also, we can add a number of days to a specific day/days to a period. 
Period() creates a period object with an specific value. For example, I can calculate how long I will be in the conference. 
Instants is an specific moment in time. There some common date-time objects s (e.g, POSIXct, POSIXlt,
and Date objects). 


- The `ggplot2` package works seamlessy with lubridate. Find a data set with dates and/or times, use lubridate to work with the dates/times, then plot a time-related aspect of the data and describe it.  




{% highlight r %}
library(lubridate)

### Interval
plan1_conference <- interval(ymd(20190601, arr="Arrive"), ymd(20190606, lea="leave"))
{% endhighlight %}



{% highlight text %}
## Warning: 1 failed to parse.
{% endhighlight %}



{% highlight text %}
## Warning: 1 failed to parse.
{% endhighlight %}



{% highlight r %}
plan2_friend <- interval(ymd(20190601, arr="Arrive"), ymd(20190615, lea="leave"))
{% endhighlight %}



{% highlight text %}
## Warning: 1 failed to parse.
{% endhighlight %}



{% highlight text %}
## Warning: 1 failed to parse.
{% endhighlight %}



{% highlight r %}
# checking overlap
int_overlaps(plan1_conference,plan2_friend)
{% endhighlight %}



{% highlight text %}
## [1] TRUE   NA
{% endhighlight %}



{% highlight r %}
### Duration 
duration(90, "seconds")
{% endhighlight %}



{% highlight text %}
## [1] "90s (~1.5 minutes)"
{% endhighlight %}



{% highlight r %}
duration(day = 90)
{% endhighlight %}



{% highlight text %}
## [1] "7776000s (~12.86 weeks)"
{% endhighlight %}



{% highlight r %}
# leap year
leap_year(2013) 
{% endhighlight %}



{% highlight text %}
## [1] FALSE
{% endhighlight %}



{% highlight r %}
ymd(20190201) + dyears(2)
{% endhighlight %}



{% highlight text %}
## [1] "2021-01-31"
{% endhighlight %}



{% highlight r %}
### Period
minutes(2)
{% endhighlight %}



{% highlight text %}
## [1] "2M 0S"
{% endhighlight %}



{% highlight r %}
plan1_conference / minutes(1)
{% endhighlight %}



{% highlight text %}
## [1] 7200   NA
{% endhighlight %}



{% highlight r %}
plan1_conference / days(1)
{% endhighlight %}



{% highlight text %}
## [1]  5 NA
{% endhighlight %}



{% highlight r %}
### Instant 
is.instant(as.Date("2019-08-03"))
{% endhighlight %}



{% highlight text %}
## [1] TRUE
{% endhighlight %}


{% highlight r %}
library(tidyverse)
library(ggplot2)
library(nycflights13)


# Arbitrary rainfall  
weather <- read.csv("~/weather.csv")
{% endhighlight %}



{% highlight text %}
## Warning in file(file, "rt"): cannot open file '/Users/heike/weather.csv':
## No such file or directory
{% endhighlight %}



{% highlight text %}
## Error in file(file, "rt"): cannot open the connection
{% endhighlight %}



{% highlight r %}
weather_date <- weather %>% 
  mutate(data = make_datetime(year, month, day))

date <- ymd(20171015,20171115,20171215,20180115,20180215,20180315,
           20180415,20180515,20180615,20180715,20180815,20180915)

Temp <- c(10,12,1,13,16,18,15,25,20,32,22,12)
  
weather_df <- data.frame(Temp,date)
{% endhighlight %}


{% highlight r %}
# Plot 
ggplot(weather_df,aes(x = date,y = Temp)) +
  geom_point(colour = "blue") +
  geom_smooth(colour = "red",size = 1)+
  scale_y_continuous(limits = c(5,30), breaks = seq(5,30,5)) +
  ggtitle ("Average Temperature") +
  xlab("Date") +  ylab ("Average Temperature ( ºC )")
{% endhighlight %}



{% highlight text %}
## `geom_smooth()` using method = 'loess' and formula 'y ~ x'
{% endhighlight %}



{% highlight text %}
## Warning: Removed 2 rows containing non-finite values (stat_smooth).
{% endhighlight %}



{% highlight text %}
## Warning: Removed 2 rows containing missing values (geom_point).
{% endhighlight %}

![center](../figure/04/KhaledianYones/plot-1.png)

