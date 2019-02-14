---
title: "Blog #4: Interesting times..."
author: "Brianna Lawton"
topic: "04"
layout: post
root: ../../../
---

{% highlight r %}
library(tidyverse)
library(lubridate)
{% endhighlight %}

## Q1:Describe what intervals, durations, periods, and instants are, and give one example for each that shows why we need these distinctions.

Lubridate comes in handy when dealing with data that includes dates and times. Lubridate allows arithmetic xxx to take place yielding both relative and exact units in the output using the following objects. 

Instants are specific moments in time. For example if you want to know the current time and date in your time zone use ...XXXX

{% highlight r %}
start_2019 <- ymd_hms("2019-01-01 12:00:00")

date <- now()
date
{% endhighlight %}



{% highlight text %}
## [1] "2019-02-13 23:21:57 CST"
{% endhighlight %}
* The following classes represent ways of analyzing different timespans.

Durations record timespan measured in an exact number of seconds.Durations are good for estimating large timespans in seconds that we as humans may not know or use to seeing commonly by outputting the numbe rof seconds followed by parenthesis of the estimated length in days or weeks or year.
For example, if you want to know...XXX

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
For example, if you want to know .....XXX

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
For example, if you want to know ...XXX


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

## Instructions:
Update your forked repo of `blog-2019`. 

To make your life easier, create an RStudio project on your local machine that is linked to your github repo. 

Save a **copy** of this file, replacing "Lastname" and "Firstname" with your own and *leave the original unedited*.

In **your copy**, replace the `title:` and `author:` fields in the YAML above, while leaving the remaining fields intact. Remove the background and the instructions sections and write your blog post!

Push the changes from your local machine to your github repo. 

Once you are done, **create a pull request** to upload your changes to the original repository!

