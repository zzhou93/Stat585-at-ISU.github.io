---
title: "Split apply combine"
author: "Jing zhao"
topic: "02"
layout: post
root: ../../../
---


1.**Which (base R) functions do you know that support the split-apply-combine strategy? In your opinion, are these sufficient - state why or why not?**. 

The base function support split-apply-combine includes apply(), sapply(), tapply(), aggregate().They are not sufficient when the data structure is complicated with multiple factors.

2. **Using a dataset of your choice, show (by including the split-apply-combine command(s) in your answer) how you can use the split-apply-combine strategy for a part of the data analysis.**

I choose the Titanic dataset as an example to explore the replationship between class and survived status.


{% highlight r %}
data("mtcars")
library(tidyverse)
car<-mtcars %>% select(mpg,cyl,qsec) %>% group_by(cyl) %>% summarise(mpg=median(mpg),qsec=mean(qsec))
{% endhighlight %}



{% highlight text %}
## Error in select(., mpg, cyl, qsec): unused arguments (mpg, cyl, qsec)
{% endhighlight %}



{% highlight r %}
car
{% endhighlight %}



{% highlight text %}
## Error in eval(expr, envir, enclos): object 'car' not found
{% endhighlight %}
