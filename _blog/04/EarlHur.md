---
title: "Ethics and Reproducibility"
author: "Earl Hur"
root: ../../../
layout: post
topic: '04'
---


{% highlight r %}
library(tidyverse)
library(ggplot2)
library(plotly)
library(googledrive)
library(lubridate)
myurl <- "https://docs.google.com/spreadsheets/d/e/2PACX-1vQhHBTlMFNLDYQi72CLe9l8YTwMFk_TmbYDyeQkO7CxUTvHXYdqS26TguHn-Nfqxtd1a2GXlWC9cK2E/pub?gid=0&single=true&output=csv"
terror <- read.csv(url(myurl))
{% endhighlight %}

1. **Describe what intervals, durations, periods, and instants are, and give one example for each that shows why we need these distinctions.**. 

Instant is the exact time point such as the moment right now. Intervals are the span between starting and ending point of times. In order to define an interval, the starting and ending points should be defined at first. An example for this is *the time that I spent for cooking my lunch yesterday.*. For duration and periods, however, there is no need to defind starting and ending instants. These two concepts are defined as the length of times which are not bounded by instants. Duration measures by seconds and periods measures minutes, hours or else that are larger than seconds. The example of the duration or period is *how fast can you run for a marathon*. In this example, there is no starting and ending instants. Sometimes we want to use the length of two exact times and other times we may want to use just a time period that is measured by seconds, minutes, etc. This distinction is important in dealing with time and dates especially for dealing with time span. 

2. **The ggplot2 package works seamlessy with lubridate. Find a data set with dates and/or times, use lubridate to work with the dates/times, then plot a time-related aspect of the data and describe it.**

My two years of research had been focused on modelling the number of terrorist attacks. Below data were just a subset of terrorist incidences from 1970 to 2014. The dataset contains information about when and where the terrorist attacks perpetuated and also what type of attack the terrorists used for the incidences. Here, I am going to use data for incidences from 2010 to 2014 only. Below bar chart shows the number of monthly terrorist attacks. That is, the vertical bars represent the number of terrorist attacks that happened in the specific year and month that are coded with *floor_date* function. Each of the bars are stacked with different colors that represent the type of attacks. By this plot, we can see the monthly trends of the number of terrorist attacks and the types of attacks at the same time. In order to show the exact information, *ggplotly* was used to show the attack type, the number of attacks with the corresponding attack type and the year and month information from each bars.


{% highlight r %}
ter_Date <- ymd(paste(terror$iyear, terror$imonth, terror$iday, sep = "-"))
terror$Date <- ter_Date

p_terror <- terror %>% 
  group_by(month=lubridate::floor_date(Date, "month"), attacktype1_txt) %>%
  summarise(count=length(attacktype1_txt)) %>%
  ggplot(aes(month, count, fill=attacktype1_txt)) +
  geom_bar(stat = "identity",
           aes(text=(paste("Attack Type: ", attacktype1_txt,
                           "<br>Count: ", count,
                           "<br>Year: ", year(month),
                           "<br>Month: ", month(month, label = TRUE))))) +
  labs(x = "Months from 2010 to 2014", y = "Number of Attacks", 
       title = "Number of Attacks from 2010 to 2014") +
  guides(fill=guide_legend(title="Attack Type")) + 
  theme_light() +
  theme()
  
ggplotly(p_terror, tooltip = "text")
{% endhighlight %}



{% highlight text %}
## Error in paste("Attack Type: ", attacktype1_txt, "<br>Count: ", count, : object 'attacktype1_txt' not found
{% endhighlight %}

