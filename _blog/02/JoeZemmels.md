---
title: "Split apply combine ..."
author: "Joe Zemmels"
topic: "02"
layout: post
root: ../../../
---

## Background:

The `plyr` package has by now been replaced by other, even faster packages, but the idea of *Split, apply, combine* is as relevant as ever.

Read the paper [The Split-Apply-Combine Strategy for Data Analysis](https://www.jstatsoft.org/article/view/v040i01) by Hadley Wickham.


Write a blog post addressing the questions: 

1. **Which (base R) functions do you know that support the split-apply-combine strategy? In your opinion, are these sufficient - state why or why not?**. 

As Hadley discusses in the beginning of the paper, there are many base R functions that support the split-apply-combine strategy. For example, the aggregate function works to group data by common values of a factor and generate summary statistics/apply functions for those groups. However, as Hadley explains, a big issue with many of these base R functions is in readability. The group_by/summarise functions in dplyr accomplish the same task, yet are arguably much more readable thanks to the pipe operator and more generalizable. That is, while aggregate can only apply a single named function to grouped data, the summarise function allows for any number of functions to be specified. Further, by breaking up the grouping and function applying actions that aggregate performs into two functions, group_by and summarise, the dplyr functions can be used together to accomplish more tasks. For example, group_by can be used along with ggplot2 to obtain visualizations by group. I would argue that there are many base R functions, like the apply family, that support the split-apply-combine strategy that Hadley discusses. However, functions in the dplyr package accomplish the same types of tasks and are generally easier to understand.

2. **Using a dataset of your choice, show (by including the split-apply-combine command(s) in your answer) how you can use the split-apply-combine strategy for a part of the data analysis.**

The mojo data contains box office numbers for movies through the week of August 31, 2018.


{% highlight r %}
library(tidyverse)
mojo <- classdata::mojo
{% endhighlight %}

Suppose we were interested in seeing how the box office number stack up between different studios over time. This calls for splitting the data using the dplyr group_by function, which will allow us to group box office gross by studio. We can then either combine these numbers using the summarise function or plot the data over time.


{% highlight r %}
mojo %>%
  group_by(Studio) %>%
  summarise(totalGross = sum(`Total Gross`))
{% endhighlight %}



{% highlight text %}
##     totalGross
## 1 1.011704e+12
{% endhighlight %}

As we can see, there are 374 different named studios in the dataset, too many to be very useful for a high-level analysis. To get only, say, the top 5 highest grossing studios, we can use the dplyr top_n function, which will apply a filter to our data based on a weight that we can define. We also need to be careful to remove all rows for each movie except for highest grossing entry, which is presumably the last week that it was in theaters, so as to avoid overrepresenting movies that were in the theaters for a long period of time.


{% highlight r %}
mojo %>%
  group_by(Title) %>%
  top_n(1,`Total Gross`) %>%
  ungroup() %>%
  group_by(Studio) %>%
  summarise(totalGross=sum(`Total Gross`)) %>%
  top_n(5,totalGross) %>%
  ggplot(aes(x=Studio,weight=totalGross,fill=Studio)) + geom_bar()
{% endhighlight %}



{% highlight text %}
## Error in FUN(X[[i]], ...): object 'Studio' not found
{% endhighlight %}

![center](../figure/blog-2019/02/JoeZemmels-unnamed-chunk-3-1.png)

As we can see, the Buena Vista studio, which was the original name for Walt Disney Studio Motion Pictures, has had the highest box office numbers by far. We can drill deeper into Buena Vista movies over time by applying another filter to the dataset.


{% highlight r %}
mojo %>%
  filter(Studio == "BV") %>%
  group_by(Title) %>%
  top_n(1,`Total Gross`) %>%
  ungroup() %>%
  top_n(5,`Total Gross`) %>%
  ggplot(aes(x=Title,weight=`Total Gross`)) + geom_bar() + coord_flip()
{% endhighlight %}

![center](../figure/blog-2019/02/JoeZemmels-unnamed-chunk-4-1.png)

As we can see, dplyr allows easy implementation of the split-apply-combine strategy for data analysis.

## Instructions:

Update your forked 'blog-2019' repository.

Save a **copy** of this file, replacing "Lastname" and "Firstname" with your own and *leave the original unedited*.

In **your copy**, replace the `title:` and `author:` fields in the YAML above, while leaving the remaining fields intact. Remove the background and the instructions sections and write your blog post! 

Once you are done, **create a pull request** to upload your changes to the original repository. Do not commit the compiled HTML file to the repository.
