---
title: "Split apply combine ..."
author: "Qing He"
topic: "02"
layout: post
root: ../../../
---

## Background:

The `plyr` package has by now been replaced by other, even faster packages, but the idea of *Split, apply, combine* is as relevant as ever.

Read the paper [The Split-Apply-Combine Strategy for Data Analysis](https://www.jstatsoft.org/article/view/v040i01) by Hadley Wickham.


Write a blog post addressing the questions: 

1. **Which (base R) functions do you know that support the split-apply-combine strategy? In your opinion, are these sufficient - state why or why not?**. 
Function in apply family, such as vapply sapply lapply and apply, are using the split-apply-combine strategy. They are not sufficient in data analysis. Since they can only process the vectors or the expression objects, data in list need to be manually split and reassamble before and after applying the function to vectors in the list. 

2. **Using a dataset of your choice, show (by including the split-apply-combine command(s) in your answer) how you can use the split-apply-combine strategy for a part of the data analysis.**
Calculate the mean and standard deviation of Petal.Length for each speices 

{% highlight r %}
library(tidyverse)
library(dplyr)

ddply(iris,.(Species),summarise,mean=mean(Petal.Length),sd=sd(Petal.Length))
{% endhighlight %}



{% highlight text %}
##      Species  mean        sd
## 1     setosa 1.462 0.1736640
## 2 versicolor 4.260 0.4699110
## 3  virginica 5.552 0.5518947
{% endhighlight %}


## Instructions:

Update your forked 'blog-2019' repository.

Save a **copy** of this file, replacing "Lastname" and "Firstname" with your own and *leave the original unedited*.

In **your copy**, replace the `title:` and `author:` fields in the YAML above, while leaving the remaining fields intact. Remove the background and the instructions sections and write your blog post! 

Once you are done, **create a pull request** to upload your changes to the original repository. Do not commit the compiled HTML file to the repository.
