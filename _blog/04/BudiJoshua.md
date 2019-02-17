---
title: "Interesting times..."
author: "Joshua Budi"
topic: "04"
layout: post
root: ../../../
---


## Background:


Write a blog post addressing the questions:


- Describe what intervals, durations, periods, and instants are, and give one example for each that shows why we need these distinctions.

instant is the specific moment of time that is being identified. It could be in a form of date, time, and date-time, and within the date it can be specified down to the day, month, year or within the time it can be specified down to the hour, minute, and seconds.

durations is a class object that returns a span of time that is always represented as seconds units. It emphasizes uniform pipeline to work with through simplifying duration measures down to seconds. Seconds is about the smallest time unit that people will be mostly concerned with. When the desired duration of interest is in chunks of minutes, hours, or such, it is much easier to convert them to these bigger units later on. 

periods is using days and month to work with which is more intuitive to people than seconds. 

intervals is used when working with calculation involving periods or duration units. Therefore, it will ask us to identify a specific starting point of time and the interval it is interested in. 

 





- The `ggplot2` package works seamlessy with lubridate. Find a data set with dates and/or times, use lubridate to work with the dates/times, then plot a time-related aspect of the data and describe it.  

Body temperature of beavers



{% highlight r %}
library(lubridate)
library(hms)

head(beav1)
beav1t <- formatC(beav1$time, flag=0, width=4)
beav1t
beav1$time <- strptime(as.character(beav1t), format="%H%M")
beav1$time <- as.hms(beav1$time)
unique(beav1$day)
beav1$day<- as_date(beav1$day)
beav1$datetime <- paste(beav1$day,beav1$time)
beav1$datetime <- as_datetime(beav1$datetime)
{% endhighlight %}
Temperature of beaver body recorded using telemetry every 10 minutes 

{% highlight r %}
ggplot(beav1,aes(datetime,temp, group=1))+
  geom_line()
{% endhighlight %}

![center](../figure/04/BudiJoshua/unnamed-chunk-3-1.png)
