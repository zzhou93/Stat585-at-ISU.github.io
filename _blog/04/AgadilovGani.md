---
title: "Interesting times..."
author: "Gani Agadilov"
output:
  pdf_document: default
  word_document: default
root: ../../../
layout: post
topic: '04'
---

Question 1

- Describe what intervals, durations, periods, and instants are, and give one example for each that shows why we need these distinctions.

From the paper "Dates and Times Made Easy with lubridate" and Chapter 16 of "R for Data Science", some definitions are given for the different type of time formats.

Instant. An instant is a specific moment in time. For instance, February 11th, 2019. There are three types of date/time data that represents an instant type: date, time within the day and date-time.

{% highlight r %}
require(lubridate)
today()
{% endhighlight %}



{% highlight text %}
## [1] "2019-02-13"
{% endhighlight %}



{% highlight r %}
now()
{% endhighlight %}



{% highlight text %}
## [1] "2019-02-13 23:18:57 CST"
{% endhighlight %}



{% highlight r %}
date()
{% endhighlight %}



{% highlight text %}
## [1] "Wed Feb 13 23:18:57 2019"
{% endhighlight %}

Interval. An interval is a span of time that occurs between two specific instants. For example, how many weeks from February 11th in 2019 to February 11th in 2020. Intervals have a starting and ending point.

{% highlight r %}
future1 <- today() + years(1)
(today() %--% future1) /weeks(1)
{% endhighlight %}



{% highlight text %}
## [1] 52.14286
{% endhighlight %}

Duration. If we record the time span in seconds, we will have durations. For instance, duration of 10 minutes is 600s.


{% highlight r %}
dminutes(10)
{% endhighlight %}



{% highlight text %}
## [1] "600s (~10 minutes)"
{% endhighlight %}



{% highlight r %}
age <- today() - ymd(19880704)
age
{% endhighlight %}



{% highlight text %}
## Time difference of 11181 days
{% endhighlight %}



{% highlight r %}
as.duration(age)
{% endhighlight %}



{% highlight text %}
## [1] "966038400s (~30.61 years)"
{% endhighlight %}

Period. Periods record a time span in units larger than seconds, such as years, months, weeks, days, hours, and minutes. For example, period of 5 weeks is 35 days 0 hours 0 minutes 0 seconds.

{% highlight r %}
weeks(5)
{% endhighlight %}



{% highlight text %}
## [1] "35d 0H 0M 0S"
{% endhighlight %}



{% highlight r %}
days(5) + hours(5) + minutes(5)
{% endhighlight %}



{% highlight text %}
## [1] "5d 5H 5M 0S"
{% endhighlight %}

Question 2

- The `ggplot2` package works seamlessy with lubridate. Find a data set with dates and/or times, use lubridate to work with the dates/times, then plot a time-related aspect of the data and describe it.  

I have used the dataset AirPassengers which indicates a number of international airline passengers between 1949 and 1960.  The dataset was given in time series format. By using the fortify command, I changed to the accessible form. In order to see a number of airline users for each day of the week, we add the days of each flight and plot with a number of passengers. There was a clear pattern that all days had the almost same amount of passengers. As we can see from the second plot, there was the seasonality that indicates a maximum amount of the passengers during in July-August months.

{% highlight r %}
library(lubridate)
library(ggplot2)
library(tidyverse)
library(ggfortify)
{% endhighlight %}



{% highlight text %}
## Error in library(ggfortify): there is no package called 'ggfortify'
{% endhighlight %}



{% highlight r %}
data <- fortify(AirPassengers)
{% endhighlight %}



{% highlight text %}
## Error: `data` must be a data frame, or other object coercible by `fortify()`, not an S3 object with class ts
{% endhighlight %}



{% highlight r %}
str(data)
{% endhighlight %}



{% highlight text %}
## Classes 'tbl_df', 'tbl' and 'data.frame':	574 obs. of  7 variables:
##  $ date    : Date, format: "1967-07-01" "1967-08-01" ...
##  $ pce     : num  507 510 516 513 518 ...
##  $ pop     : int  198712 198911 199113 199311 199498 199657 199808 199920 200056 200208 ...
##  $ psavert : num  12.5 12.5 11.7 12.5 12.5 12.1 11.7 12.2 11.6 12.2 ...
##  $ uempmed : num  4.5 4.7 4.6 4.9 4.7 4.8 5.1 4.5 4.1 4.6 ...
##  $ unemploy: int  2944 2945 2958 3143 3066 3018 2878 3001 2877 2709 ...
##  $ year    : num  1967 1967 1967 1967 1967 ...
{% endhighlight %}



{% highlight r %}
data %>% 
  mutate(wday = wday(data$Index, label = TRUE)) %>% 
  ggplot(aes(x = wday)) +
    geom_bar()
{% endhighlight %}



{% highlight text %}
## Warning: Unknown or uninitialised column: 'Index'.
{% endhighlight %}



{% highlight text %}
## Error in as.POSIXlt.default(x, tz = tz(x)): do not know how to convert 'x' to class "POSIXlt"
{% endhighlight %}



{% highlight r %}
data %>%
  ggplot(aes(x = data$Index)) +
  geom_line(aes(y = data$Data), colour = "blue", size = 2)+
  xlab("Flight date") +
  ylab("Number of passengers")+
  theme_bw()
{% endhighlight %}



{% highlight text %}
## Warning: Unknown or uninitialised column: 'Data'.
{% endhighlight %}



{% highlight text %}
## Warning: Unknown or uninitialised column: 'Index'.
{% endhighlight %}



{% highlight text %}
## Warning: Unknown or uninitialised column: 'Data'.
{% endhighlight %}



{% highlight text %}
## Warning: Unknown or uninitialised column: 'Index'.
{% endhighlight %}



{% highlight text %}
## Error: Aesthetics must be either length 1 or the same as the data (574): y, x
{% endhighlight %}

![center](../figure/04/AgadilovGani/unnamed-chunk-5-1.png)

















