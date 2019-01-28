---
title: "Split apply combine ..."
author: "Zahra Khoshmanesh"
topic: "02"
layout: post
root: ../../../
---

In this post, I want to answer the following questions based on the Hadley Wickham paper, "The Split-Apply-Combine Strategy for Data
Analysis" and my experience and underestanding of the subject.

1. **Which (base R) functions do you know that support the split-apply-combine strategy? In your opinion, are these sufficient - state why or why not?**. 
As Hadley Wickham mentioned in the paper, we can use for loop and built in function such as by ,apply and transform functions
to implement our task, here, map and reduce tasks. However, It needs multiple lines code to perform same thing performed in plyr library 
just with a few lines.
Therefore, plyr library cause to have nicer code that easy to read and underestand and also faster code. In my opinion maybe 
the built in functions in R and for loops are sufficient for professional people working for many years , yet, they are not efficient 
and sufficient for beginner having less familiarity with the concept.
2. **Using a dataset of your choice, show (by including the split-apply-combine command(s) in your answer) how you can use the split-apply-combine strategy for a part of the data analysis.**

Let us review some usefull functions in plyr library. We build a dataframe containing 30 different products(here projects in 3 groups) during 2009 to 2018 with different number of failurs.


{% highlight r %}
#first we build a dataset containing projects with failures between 2009 to 2018
df <- data.frame(Project=gl(3,10,labels=c("Interface","Backend","Frontend")),Year=factor(rep(2009:2018,3)),detectedFailures=1:30)
#see the 5 first rows
head(df)
{% endhighlight %}



{% highlight text %}
##     Project Year detectedFailures
## 1 Interface 2009                1
## 2 Interface 2010                2
## 3 Interface 2011                3
## 4 Interface 2012                4
## 5 Interface 2013                5
## 6 Interface 2014                6
{% endhighlight %}



{% highlight r %}
#check the dimension
{% endhighlight %}

We are interested in absolute and relative detectedFailures developments by project over time. 
Therefore, we will add a column to the data frame that shows the failurs divided by the total sum of failurs in each year:

This is called transformation in R and can be done as follows: 
** base R with by,
** ddply of the plyr package,

_by_
we use "by" to split the data for each year and defone a function called fraction to calculate the fraction of detected failures group by year and later will apply the transform function to each subset to calculate the fraction of failure for each project with the following function: fraction <- function(x) x/sum(x). Finally wrap it with using do.call and rbind. 


{% highlight r %}
fraction <- function(x) x/sum(x)
newdf <- do.call("rbind", as.list(by(df, df["Year"], transform, failurerate=fraction(detectedFailures))))
head(newdf)
{% endhighlight %}



{% highlight text %}
##           Project Year detectedFailures failurerate
## 2009.1  Interface 2009                1  0.03030303
## 2009.11   Backend 2009               11  0.33333333
## 2009.21  Frontend 2009               21  0.63636364
## 2010.2  Interface 2010                2  0.05555556
## 2010.12   Backend 2010               12  0.33333333
## 2010.22  Frontend 2010               22  0.61111111
{% endhighlight %}
_ddply_
 let us do it with using ddply from plyr package:

{% highlight r %}
library(plyr)
fraction <- function(x) x/sum(x)
newdf <- ddply(df, "Year", transform, failurerate=fraction(detectedFailures))
head(newdf)
{% endhighlight %}



{% highlight text %}
##     Project Year detectedFailures failurerate
## 1 Interface 2009                1  0.03030303
## 2   Backend 2009               11  0.33333333
## 3  Frontend 2009               21  0.63636364
## 4 Interface 2010                2  0.05555556
## 5   Backend 2010               12  0.33333333
## 6  Frontend 2010               22  0.61111111
{% endhighlight %}
 
As you can see using dplyr package is more readable.
