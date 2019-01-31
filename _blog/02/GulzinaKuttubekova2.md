---
title: "Split-apply-combine..."
author: "Gulzina Kuttubekova"
topic: "02"
layout: post
root: ../../../
---


1. **Which (base R) functions do you know that support the split-apply-combine strategy? In your opinion, are these sufficient - state why or why not?**

  The most popular and mostly used (at least by me) R functions which support this strategy are “apply” family: apply(), lapply(), tapply() and mapply(), split(), rbind() and cbind(). The reasons I would prefer using those functions are the simple syntax and readability, compared to the “for” loops or any loops in R. The main advantage, of course, is the speed of these functions and a significant decrease in the runtime of code, where those functions are used. 
However, taking into account the nature of a “big data”, apply() family might be insufficient and slow in some cases. For that reason, we will have to dig more deeply and try to refine the code/program in a lower-level programming language like C. Moreover, it is not easy to go from 2D array to 3D array. Hence, depending on a case, one may prefer to use functions from “plyr” family which also support the split-apply-combine strategy.



2. **Using a dataset of your choice, show (by including the split-apply-combine command(s) in your answer) how you can use the split-apply-combine strategy for a part of the data analysis.**

  I will use the dataset "chickwts" from the R Datasets package. 

From the preliminary analysis we see that chickens were fed by 6 diet types: {casein, horsebean, meatmeal, linseed, soybean and sunflower}  

{% highlight r %}
chickwts %>% str()
{% endhighlight %}



{% highlight text %}
## 'data.frame':	71 obs. of  2 variables:
##  $ weight: num  179 160 136 227 217 168 108 124 143 140 ...
##  $ feed  : Factor w/ 6 levels "casein","horsebean",..: 2 2 2 2 2 2 2 2 2 2 ...
{% endhighlight %}



{% highlight r %}
chickwts %>% head()
{% endhighlight %}



{% highlight text %}
##   weight      feed
## 1    179 horsebean
## 2    160 horsebean
## 3    136 horsebean
## 4    227 horsebean
## 5    217 horsebean
## 6    168 horsebean
{% endhighlight %}
  
  Simple summary statistics on chicken weights for different diet types is given as follows:

{% highlight r %}
tapply(chickwts$weight, chickwts$feed, summary)
{% endhighlight %}



{% highlight text %}
## $casein
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##   216.0   277.2   342.0   323.6   370.8   404.0 
## 
## $horsebean
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##   108.0   137.0   151.5   160.2   176.2   227.0 
## 
## $linseed
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##   141.0   178.0   221.0   218.8   257.8   309.0 
## 
## $meatmeal
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##   153.0   249.5   263.0   276.9   320.0   380.0 
## 
## $soybean
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##   158.0   206.8   248.0   246.4   270.0   329.0 
## 
## $sunflower
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##   226.0   312.8   328.0   328.9   340.2   423.0
{% endhighlight %}
  Sunflower and casein diet seems to be the most succesful diet with the highest mean weights of 328.9 and 323.6 grams. Chickens in a group with horsebean diet have the smallest mean weight: 160.2. 
  
 We can get the same summary statistics using other functions from this family as well:

{% highlight r %}
chicks <- split(chickwts$weight, chickwts$feed)
# since the resulting chicks is an array, we can use lapply()
lapply(chicks, summary)
{% endhighlight %}



{% highlight text %}
## $casein
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##   216.0   277.2   342.0   323.6   370.8   404.0 
## 
## $horsebean
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##   108.0   137.0   151.5   160.2   176.2   227.0 
## 
## $linseed
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##   141.0   178.0   221.0   218.8   257.8   309.0 
## 
## $meatmeal
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##   153.0   249.5   263.0   276.9   320.0   380.0 
## 
## $soybean
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##   158.0   206.8   248.0   246.4   270.0   329.0 
## 
## $sunflower
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##   226.0   312.8   328.0   328.9   340.2   423.0
{% endhighlight %}
  
  
  
  
  
  
  
  
  
  
  
  
  
  
