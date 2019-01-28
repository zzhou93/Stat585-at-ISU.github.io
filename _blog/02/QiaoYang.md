---
title: "Split apply combine ..."
author: "Yang Qiao"
topic: "02"
layout: post
root: ../../../
---

Write a blog post addressing the questions: 

1. **Which (base R) functions do you know that support the split-apply-combine strategy? In your opinion, are these sufficient - state why or why not?**.

    `split`, `*apply`, `aggregate`. Not sufficient, because they are non-readable and have non-consistent usage.

2. **Using a dataset of your choice, show (by including the split-apply-combine command(s) in your answer) how you can use the split-apply-combine strategy for a part of the data analysis.**

    Calculate the sample mean for each species from the data `iris`.
    
    {% highlight r %}
    aggregate(iris[, -5], list(Species = iris$Species), mean)
    {% endhighlight %}
    
    
    
    {% highlight text %}
    ##      Species Sepal.Length Sepal.Width Petal.Length Petal.Width
    ## 1     setosa        5.006       3.428        1.462       0.246
    ## 2 versicolor        5.936       2.770        4.260       1.326
    ## 3  virginica        6.588       2.974        5.552       2.026
    {% endhighlight %}
