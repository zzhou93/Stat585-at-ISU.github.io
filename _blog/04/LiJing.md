---
title: "Interesting times..."
author: "Jing Li"
topic: "04"
layout: post
root: ../../../
---


## Background:

Dates and times can be difficult to work with. Watch [this video](https://www.youtube.com/watch?v=-5wpm-gesOY) to appreciate all of the fun scenarios that date/time libraries have to accommodate. 

Luckily, the `lubridate` package makes working with dates and times in R pretty straightforward. The package has been described in the paper [Working with date and time](http://www.jstatsoft.org/v40/i03/) by Garrett Grolemund and Hadley Wickham, an updated version of an intro to lubridate can be found in chapter 16 of [R for Data Science](https://r4ds.had.co.nz/dates-and-times.html). Read one of the two sources.

Write a blog post addressing the questions:


- Describe what intervals, durations, periods, and instants are, and give one example for each that shows why we need these distinctions.

Interval means from starting to ending point. e.g. From 1 am to 2 am. It should include two points.
Duration means an exact number of seconds. e.g. The duration from 1 am to 2 am is 3600s. Duration only use unit as second.
Period means units for human read. e.g. The period from 1 am to 2 am is 1 hour. The unit for period could be hour, week, month. It doesn't like durattion, which only use second.
Instant means the exact time. e.g. 2019-02-08 20:00:00. It's only one point.
It is important to distinguish between these things because when we use different functions in the lubridate package with same input, might got different result.


- The `ggplot2` package works seamlessy with lubridate. Find a data set with dates and/or times, use lubridate to work with the dates/times, then plot a time-related aspect of the data and describe it.  


{% highlight r %}
rain <- read.csv("https://ndownloader.figshare.com/files/7283285", header = T, na.strings = 999.99)
rain %>% 
  mutate(DATE=as.Date(DATE, format = "%m/%d/%y")) %>%
  mutate(month=month(DATE)) %>%
  group_by(month,YEAR) %>%
  summarise(max_rain = sum(DAILY_PRECIP, na.rm = T)) %>%
  mutate(month2=as.Date(paste0("2019-",month,"-01"),"%Y-%m-%d")) %>%
  ggplot(aes(x=month2,y=max_rain)) +
  geom_bar(stat = "identity", fill="pink") + 
  facet_wrap(~YEAR, ncol=3) +
  labs(title = "Monthly precipitation from 2003 to 2013 in Boulder, Colorado",
       x = "Month", y= "Precipitation (inches") + 
  scale_x_date(date_labels = "%b")
{% endhighlight %}



{% highlight text %}
## Error in paste0("2019-", month, "-01"): cannot coerce type 'closure' to vector of type 'character'
{% endhighlight %}
This plot shows the monthly precipitation from Jan-2003 to Dec-2013 at Boulder, Colorado. It seems the precipitation has large difference for each year. The amount in winter and summer are lower than spring and fall.
