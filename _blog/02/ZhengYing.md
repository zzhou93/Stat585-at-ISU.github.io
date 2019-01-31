---
title: "Split-apply-combine..."
author: "Ying Zheng"
topic: "02"
layout: post
root: ../../../
---




1. **Which (base R) functions do you know that support the split-apply-combine strategy? In your opinion, are these sufficient - state why or why not?**. 


The nested loops, or the built-in apply functions such as split(), lapply(), aggregate() etc. support the split-apply-combine strategy.


In my opnion these are sufficent in the sense of getting a job done. However, the learning curve for base R is steep and the code is hard to read and write, either containing too many extra book-keeping codes, or use arrays which is not flexible as dataframes. The plyr/dplyr will illuminate the key components of the computation and easy to read and write.



2. **Using a dataset of your choice, show (by including the split-apply-combine command(s) in your answer) how you can use the split-apply-combine strategy for a part of the data analysis.**


I will use split-apply-combine strategy to caculate the mean for each species from the data iris

- Step 1: split the data into groups
- Step 2: apply a function, in this case, an aggregation function that computes a mean
- Step 3: combine the results into a new DataFrame.




{% highlight r %}
library("tidyverse")
#head(iris)
irismean <- iris %>%
  group_by(Species) %>%
  summarize(n=n(), SL.mean = mean(Sepal.Length), SW.mean = mean(Sepal.Width), PL.mean = mean(Petal.Length), PW.mean = mean(Petal.Width))


irismean
{% endhighlight %}



{% highlight text %}
## # A tibble: 3 x 6
##   Species        n SL.mean SW.mean PL.mean PW.mean
##   <fct>      <int>   <dbl>   <dbl>   <dbl>   <dbl>
## 1 setosa        50    5.01    3.43    1.46   0.246
## 2 versicolor    50    5.94    2.77    4.26   1.33 
## 3 virginica     50    6.59    2.97    5.55   2.03
{% endhighlight %}


