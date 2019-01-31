---
title: "Split apply combine ..."
author: "Zerui Zhang"
topic: "02"
layout: post
root: ../../../
---

Write a blog post addressing the questions: 

1. **Which (base R) functions do you know that support the split-apply-combine strategy? In your opinion, are these sufficient - state why or why not?**.

    In `R`, `split`, `apply` family, `aggregate` and user-defined `for` loop deals with the data in a fashion of the split-apply-combine strategy. 
    
    These methods are rather suitable for some small and simple data analysis. However, they are not sufficient when we are faced with complicated data structures and trying to manipulate the input and output with different dimensions and structures. Besides, they are nonreadable and may cause troubles when group working on one task.

2. **Using a dataset of your choice, show (by including the split-apply-combine command(s) in your answer) how you can use the split-apply-combine strategy for a part of the data analysis.**

    
    {% highlight r %}
    library(tidyverse)
    {% endhighlight %}
    
    
    
    {% highlight r %}
    data("USArrests")
    head(USArrests)
    {% endhighlight %}
    
    
    
    {% highlight text %}
    ##            Murder Assault UrbanPop Rape
    ## Alabama      13.2     236       58 21.2
    ## Alaska       10.0     263       48 44.5
    ## Arizona       8.1     294       80 31.0
    ## Arkansas      8.8     190       50 19.5
    ## California    9.0     276       91 40.6
    ## Colorado      7.9     204       78 38.7
    {% endhighlight %}
    
    
    
    {% highlight r %}
    USArrests %>%
      select(UrbanPop, everything()) %>% 
      tibble::rownames_to_column(var = "State") %>% 
      group_by(UrbanPop >= 80) %>% 
      summarise(mean(Murder), var(Murder))
    {% endhighlight %}
    
    
    
    {% highlight text %}
    ## Error in select(., UrbanPop, everything()): unused arguments (UrbanPop, everything())
    {% endhighlight %}
    
    
    First reorder the column of the dataset to put the "UrbanPop" representing percent urban population at the first column to be a somewhat "criteria". Then add a column of the names of the States to prevent the row names from losing after manipulations.
    
    One interesting fact about the USArrests: there seem to be no relationship between whether the population in the urban area is dense or not and the mean number of the homicides.
    
    
    {% highlight r %}
    USArrests %>%
      select(UrbanPop, everything()) %>% 
      tibble::rownames_to_column(var = "State") %>% 
      top_n(5, Murder/UrbanPop)
    {% endhighlight %}
    
    
    
    {% highlight text %}
    ## Error in select(., UrbanPop, everything()): unused arguments (UrbanPop, everything())
    {% endhighlight %}
    
    
    Another interesting fact: the top 5 most "dangerous" states regarding the percentage of murders by urban population percent shows above. (DONT TAKE IT SERIOUSLY)
