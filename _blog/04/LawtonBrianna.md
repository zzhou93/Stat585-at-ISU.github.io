---
title: "Blog#4: Interesting times..."
author: "Brianna Lawton"
topic: "04"
layout: post
root: ../../../
---

{% highlight r %}
library(dplyr)
library(tidyverse)
library(lubridate)
library(ggplot2)
{% endhighlight %}

## Q1:Describe what intervals, durations, periods, and instants are, and give one example for each that shows why we need these distinctions.

Lubridate comes in handy when dealing with data that includes dates and times. Lubridate allows arithmetic xxx to take place yielding both relative and exact units in the output using the following objects. 

Instants are specific moments in time. For example if you want to know the current time and date in your time zone use:

{% highlight r %}
start_2019 <- ymd_hms("2019-01-01 12:00:00")

date <- now()
date
{% endhighlight %}



{% highlight text %}
## [1] "2019-02-15 12:13:29 CST"
{% endhighlight %}
* The following classes represent ways of analyzing different timespans.

Durations record timespan measured in an exact number of seconds.Durations are good for estimating large timespans in seconds that we as humans may not know or use to seeing commonly by outputting the numbe rof seconds followed by parenthesis of the estimated length in days or weeks or year.
For example, if you want to know how many seconds in a certain number of minutes or how many weeks is a certain number of seconds:

{% highlight r %}
duration(60)
{% endhighlight %}



{% highlight text %}
## [1] "60s (~1 minutes)"
{% endhighlight %}



{% highlight r %}
dweeks(1) + ddays(6) + dhours(2) + dminutes(1.5) + dseconds(3)
{% endhighlight %}



{% highlight text %}
## [1] "1130493s (~1.87 weeks)"
{% endhighlight %}

Intervals are the most simple method of recording timespans.Intervals represent a start and end point or two specific intstants.Intervals are durations with a starting point that makes it precise so you can determine exactly how long the interval is. Intervals are not too useful for date-time calculations.
For example, if you want to know the amount of time difference between years in units days:

{% highlight r %}
start_2019 <- ymd_hms("2019-01-08 12:00:00")
start_2019
{% endhighlight %}



{% highlight text %}
## [1] "2019-01-08 12:00:00 UTC"
{% endhighlight %}



{% highlight r %}
start_2018 <- ymd_hms("2018-05-05 12:00:00")
start_2018
{% endhighlight %}



{% highlight text %}
## [1] "2018-05-05 12:00:00 UTC"
{% endhighlight %}



{% highlight r %}
span <- start_2019 - start_2018
span
{% endhighlight %}



{% highlight text %}
## Time difference of 248 days
{% endhighlight %}
Periods are non-exact timespans that output a length of units that vary over time depending on when it begins. Periods are good for recording timespans in units larger than seconds like minutes or months.Periods represent "human" units like minutes, hours, days, weeks, and months-timespans with no fixed length in seconds. Periods can accurately model clock times without knowing when events like leap second or leap days  or DST changes occur.
For example, if you want to know what year and date will it be in the next 3 years:


{% highlight r %}
start_2019 + years(3)
{% endhighlight %}



{% highlight text %}
## [1] "2022-01-08 12:00:00 UTC"
{% endhighlight %}



{% highlight r %}
#vs.
start_2019 + dyears(3)
{% endhighlight %}



{% highlight text %}
## [1] "2022-01-07 12:00:00 UTC"
{% endhighlight %}

## Q2:The `ggplot2` package works seamlessy with lubridate. Find a data set with dates and/or times, use lubridate to work with the dates/times, then plot a time-related aspect of the data and describe it.  

{% highlight r %}
#dataset from the U.S. Geological Survey that includes information about worldwide earthquakes
earthquakes <- read.csv("http://www.hofroe.net/data/earthquakes.csv")
#View(earthquakes)
#str(earthquakes)

#determining the time frame that the data was collected
earthquakes$Date <- lubridate::ymd(earthquakes$Date)
#displays the timespan (max & min ) that the data was collected
summary(earthquakes$Date)
{% endhighlight %}



{% highlight text %}
##         Min.      1st Qu.       Median         Mean      3rd Qu. 
## "2012-09-05" "2012-09-13" "2012-09-21" "2012-09-20" "2012-09-27" 
##         Max. 
## "2012-10-05"
{% endhighlight %}



{% highlight r %}
#the plot displays the number of earthquakes that occured per date and their average magnitudes and the country or state where most of the earthquakes occured
earthquake.test <- earthquakes %>% group_by(Date) %>% summarise(
  n = n(),
  mg = mean(Magnitude),
  Country = names(sort(table(Country), decreasing = T))[10]
)
{% endhighlight %}



{% highlight text %}
## Error: This function should not be called directly
{% endhighlight %}



{% highlight r %}
earthquake.test
{% endhighlight %}



{% highlight text %}
## Error in eval(expr, envir, enclos): object 'earthquake.test' not found
{% endhighlight %}



{% highlight r %}
earthquake.test %>% 
  ggplot(aes(x = Date, y = n, colour=Country, size=mg)) + geom_point()
{% endhighlight %}



{% highlight text %}
## Error in eval(lhs, parent, parent): object 'earthquake.test' not found
{% endhighlight %}


