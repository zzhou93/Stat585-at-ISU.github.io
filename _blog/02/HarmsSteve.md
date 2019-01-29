---
title: "Blog Number Two: Split-apply-combine"
author: "Steve Harms"
root: ../../../
layout: post
topic: '02'
---

1. **Which (base R) functions do you know that support the split-apply-combine strategy? In your opinion, are these sufficient - state why or why not?**. 
While there are probably many functions in base R that can use or apply part/all of the split-apply-combine strategy internally -such as with(), aggregate(), replicate(), sweep(), table(), some of the plotting functions, and I'm sure many of the functions that take data frames and arrays as inputs- the obvious answer here is the apply() family of functions as outlined by Hadley in the paper. The apply functions all split the data along a margin or variable, apply a function, then combine it back into a similar format for output. While these functions effectively apply the split-apply-combine paradigm, they don't necessarily allow us to control what the output will look like. This can cause trouble if our desired combined output has different dimension or format from the input, because some functions in R handle vectors differently from arrays or data frames or lists. We then need some additional lines of code to keep track of our formats and lengths, which complicates matters and makes generalization to other problems more difficult. The *ply functions in the plyr package help us control our results by clearly specifying the input/output format we want and allowing for an easy specification of the dimensions we want to split the data along.

2. **Using a dataset of your choice, show (by including the split-apply-combine command(s) in your answer) how you can use the split-apply-combine strategy for a part of the data analysis.**

A simple example using the "iris" dataset: We can look at the relationship between Sepal Length and Sepal Width for each species in two ways, with only a few commands and using the split-apply-combine method.
Using base R:


{% highlight r %}
iris %>% split(Species) %>% lapply(lm, formula=Sepal.Length~Sepal.Width) %>% lapply(coef)
{% endhighlight %}



{% highlight text %}
## $setosa
## (Intercept) Sepal.Width 
##   2.6390012   0.6904897 
## 
## $versicolor
## (Intercept) Sepal.Width 
##   3.5397347   0.8650777 
## 
## $virginica
## (Intercept) Sepal.Width 
##   3.9068365   0.9015345
{% endhighlight %}

Using plyr functions:

{% highlight r %}
iris %>% dlply(.variables=.(Species), .fun=lm, formula=Sepal.Length~Sepal.Width) %>% ldply(.fun=coef)
{% endhighlight %}



{% highlight text %}
##      Species (Intercept) Sepal.Width
## 1     setosa    2.639001   0.6904897
## 2 versicolor    3.539735   0.8650777
## 3  virginica    3.906836   0.9015345
{% endhighlight %}

In both cases we take the iris data, then split the dataset by species in to a list with 3 dataframes, one for each species. Then we estimate a simple linear regression on each dataframe, which outputs a list with 3 results from the lm() function. Then we get the intercept and regression coefficient from each list. Note that using lapply automatically gives a list of 3 coefficient pairs, but using ldply() we can get a 3x2 dataframe without any extra lines. Also note that the plyr functions get us to the end in 2 commands vs. 3 for the apply() functions.
