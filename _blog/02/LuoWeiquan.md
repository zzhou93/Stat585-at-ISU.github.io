---
title: "Split-apply-combine..."
author: "Weiquan Luo"
topic: "02"
layout: post
root: ../../../
---

1. **Which (base R) functions do you know that support the split-apply-combine strategy? In your opinion, are these sufficient - state why or why not?**. 

List of base R functions supporting the split-apply-combine strategy:
aggregate(), subset(), split(), apply(), tapply(), sapply(), cbind(), and rbind()

For simple operation on simple datasets, it is sufficient. However, loop will be required if the data set is complicate, and the operation is not easily applied with those base functions. 

2. **Using a dataset of your choice, show (by including the split-apply-combine command(s) in your answer) how you can use the split-apply-combine strategy for a part of the data analysis.**


{% highlight r %}
library(tidyverse)
library(nycflights13)
library(plyr)
{% endhighlight %}


{% highlight r %}
library(nycflights13)
library(tidyverse)
library(plyr)
#View(flights)
flights.reduce <- flights %>% # group by attribute
  group_by(dest) %>% # Find all groups bigger than a threshold
  filter(n() > 365) %>% # Find all instances bigger than zero
  filter(arr_delay > 0) %>% # Standardize to compute per group metrics:
  mutate(prop_delay = arr_delay / sum(arr_delay)) %>%
  select(year:day, dest, arr_delay, prop_delay, carrier, distance) %>% 
  ungroup()
{% endhighlight %}



{% highlight text %}
## Error in select(., year:day, dest, arr_delay, prop_delay, carrier, distance): unused arguments (year:day, dest, arr_delay, prop_delay, carrier, distance)
{% endhighlight %}



{% highlight r %}
# find the carrier whose flights have  correlation between distance and  arrivaling delaty 
model <- function(df){
  lm(distance ~ prop_delay, data = df)
}
flight.model <- dlply(flights.reduce, .(carrier), model)
{% endhighlight %}



{% highlight text %}
## Error in eval.quoted(.variables, data): object 'flights.reduce' not found
{% endhighlight %}



{% highlight r %}
rsq <- function(x) summary(x)$r.squared
flight.model.coefs <- ldply(flight.model, function(x) c(coef(x), rsquare=rsq(x)))
{% endhighlight %}



{% highlight text %}
## Error in ldply(flight.model, function(x) c(coef(x), rsquare = rsq(x))): object 'flight.model' not found
{% endhighlight %}



{% highlight r %}
names(flight.model.coefs)[2:3] <- c("intercept", "slope")
{% endhighlight %}



{% highlight text %}
## Error in names(flight.model.coefs)[2:3] <- c("intercept", "slope"): object 'flight.model.coefs' not found
{% endhighlight %}



{% highlight r %}
subset(flight.model.coefs, rsquare > 0.4)$carrier
{% endhighlight %}



{% highlight text %}
## Error in subset(flight.model.coefs, rsquare > 0.4): object 'flight.model.coefs' not found
{% endhighlight %}


