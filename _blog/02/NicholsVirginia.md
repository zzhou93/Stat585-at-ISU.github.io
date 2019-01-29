---
title: "Split apply combine ..."
author: "Virginia Nichols"
topic: "02"
layout: post
root: ../../../
---

## What do I think of base R?
1. **Which (base R) functions do you know that support the split-apply-combine strategy? In your opinion, are these sufficient - state why or why not?**. 

subset, the family of apply functions, merge
WHile these are probably sufficient (they get the job done), I don't think they 
are desirable. I myself struggled to utilize these functions, but have found
the tidyverse functions intuitive and require less googling on my part. 

## Show me things.
2. **Using a dataset of your choice, show (by including the split-apply-combine command(s) in your answer) how you can use the split-apply-combine strategy for a part of the data analysis.**

Let's use the iris data set. Load the tidyverse!

{% highlight r %}
library(tidyverse)
iris <- as_tibble(iris)
head(iris)
{% endhighlight %}



{% highlight text %}
## # A tibble: 6 x 5
##   Sepal.Length Sepal.Width Petal.Length Petal.Width Species
##          <dbl>       <dbl>        <dbl>       <dbl> <fct>  
## 1          5.1         3.5          1.4         0.2 setosa 
## 2          4.9         3            1.4         0.2 setosa 
## 3          4.7         3.2          1.3         0.2 setosa 
## 4          4.6         3.1          1.5         0.2 setosa 
## 5          5           3.6          1.4         0.2 setosa 
## 6          5.4         3.9          1.7         0.4 setosa
{% endhighlight %}

What if I want to know the mean sepal length for each species?

Let's use the tidyverse for a simple example:


{% highlight r %}
iris %>%
  group_by(Species) %>% #--split
  summarise(meanSL = mean(Sepal.Length, na.rm = T)) #--apply and combine
{% endhighlight %}



{% highlight text %}
## # A tibble: 3 x 2
##   Species    meanSL
##   <fct>       <dbl>
## 1 setosa       5.01
## 2 versicolor   5.94
## 3 virginica    6.59
{% endhighlight %}

Now do the same thing in base R. First we have to figure out what the values of Species might be:


{% highlight r %}
str(iris)
{% endhighlight %}



{% highlight text %}
## Classes 'tbl_df', 'tbl' and 'data.frame':	150 obs. of  5 variables:
##  $ Sepal.Length: num  5.1 4.9 4.7 4.6 5 5.4 4.6 5 4.4 4.9 ...
##  $ Sepal.Width : num  3.5 3 3.2 3.1 3.6 3.9 3.4 3.4 2.9 3.1 ...
##  $ Petal.Length: num  1.4 1.4 1.3 1.5 1.4 1.7 1.4 1.5 1.4 1.5 ...
##  $ Petal.Width : num  0.2 0.2 0.2 0.2 0.2 0.4 0.3 0.2 0.2 0.1 ...
##  $ Species     : Factor w/ 3 levels "setosa","versicolor",..: 1 1 1 1 1 1 1 1 1 1 ...
{% endhighlight %}
Now make a subset of data for each species:

{% highlight r %}
iris1 <- subset(iris, Species == "setosa")
iris2 <- subset(iris, Species == "versicolor")
iris3 <- subset(iris, Species == "virginica")
{% endhighlight %}
Now calculate the mean in each subest

{% highlight r %}
iris1.mean <- mean(iris1$Sepal.Length)
iris2.mean <- mean(iris2$Sepal.Length)
iris3.mean <- mean(iris3$Sepal.Length)
{% endhighlight %}
Now combine the information

{% highlight r %}
iris.means <- data.frame( species = c("setosa", "versicolor", "virginica"),
                          meanSL = c(iris1.mean, iris2.mean, iris3.mean))
iris.means
{% endhighlight %}



{% highlight text %}
##      species meanSL
## 1     setosa  5.006
## 2 versicolor  5.936
## 3  virginica  6.588
{% endhighlight %}
Yuck. Thanks Hadley Wickham!
