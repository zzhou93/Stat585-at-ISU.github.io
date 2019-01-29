---
title: "Blog 2: Split apply combine ..."
author: "Miranda Tilton"
topic: "02"
layout: post
root: ../../../
---


{% highlight r %}
library(magrittr)
library(tidyverse)
{% endhighlight %}

1. **Which (base R) functions do you know that support the split-apply-combine strategy? In your opinion, are these sufficient - state why or why not?**. 

Base R has a number of functions that support the split-apply-combine strategy: split(), apply() (and others in the apply family, such as lapply(), sapply(), etc.), and aggregate() are probably the most relevant examples. The apply() family allows functions to be applied over groups of data, but these functions are typically simple, named functions and only one is applied at a time. The aggregate() and sweep() functions allow summary statistics to be computed using groups in a data frame, but again only accepts one summary function per call to the aggregate() function.

In general, I do believe that base R functions and graphics are "sufficient" in many ways. That is, they usually get the job done in one way or another. However, they are often not the easiest or most elegant solution, especially for complex or novel tasks (such as highly specific graphics), and other packages (like dplyr) provide functions that offer more flexibility and readability. 

2. **Using a dataset of your choice, show (by including the split-apply-combine command(s) in your answer) how you can use the split-apply-combine strategy for a part of the data analysis.**

For my short analysis, I will use the midwest dataset included in ggplot2, which provides demographic information for five midwestern states: Illinois, Indiana, Michigan, Ohio, and Wisconsin. The number of counties reporting for each state can is in the table below (found by grouping by state and applying a count function).


{% highlight r %}
midwest <- ggplot2::midwest
head(midwest)
{% endhighlight %}



{% highlight text %}
## # A tibble: 6 x 28
##     PID county state  area poptotal popdensity popwhite popblack
##   <int> <chr>  <chr> <dbl>    <int>      <dbl>    <int>    <int>
## 1   561 ADAMS  IL    0.052    66090      1271.    63917     1702
## 2   562 ALEXA… IL    0.014    10626       759      7054     3496
## 3   563 BOND   IL    0.022    14991       681.    14477      429
## 4   564 BOONE  IL    0.017    30806      1812.    29344      127
## 5   565 BROWN  IL    0.018     5836       324.     5264      547
## 6   566 BUREAU IL    0.05     35688       714.    35157       50
## # ... with 20 more variables: popamerindian <int>, popasian <int>,
## #   popother <int>, percwhite <dbl>, percblack <dbl>, percamerindan <dbl>,
## #   percasian <dbl>, percother <dbl>, popadults <int>, perchsd <dbl>,
## #   percollege <dbl>, percprof <dbl>, poppovertyknown <int>,
## #   percpovertyknown <dbl>, percbelowpoverty <dbl>,
## #   percchildbelowpovert <dbl>, percadultpoverty <dbl>,
## #   percelderlypoverty <dbl>, inmetro <int>, category <chr>
{% endhighlight %}



{% highlight r %}
midwest %>% group_by(state) %>%
  summarize(n = n())
{% endhighlight %}



{% highlight text %}
## # A tibble: 5 x 2
##   state     n
##   <chr> <int>
## 1 IL      102
## 2 IN       92
## 3 MI       83
## 4 OH       88
## 5 WI       72
{% endhighlight %}

The midwest is anecdotally infamous for its subtle perpetuation of racial prejudice through systemic injustice, such as unequal opportunity to housing (especially in suburbs) and more physical segregation of living areas. In the plot below, I examine the populations of each state by the proportion of each race recorded in the data (i.e., white, black, Asian, American Indian, and other). There are data reported for each county, so We split the dataset by state to create five main subgroups. We then apply a sum across the populations of each race and combine using gather() for plotting. The resulting plot below shows Illinois as the largest state by population and Wisconsin as the smallest, but also that the proportion of non-white individuals is smallest in Wisconsin. Indiana is also small, and it appears that Illinois has the largest proportion of non-white individuals.


{% highlight r %}
midwest %>%
  group_by(state) %>%
  summarise(white = sum(popwhite),
            black = sum(popblack),
            amerindian = sum(popamerindian),
            asian = sum(popasian),
            other = sum(popother)) %>%
  gather(key = race,
         value = quantity, 
         white, black, amerindian, asian, other) %>%
  ggplot() + 
  geom_col(aes(x = state, y = quantity, fill = fct_inorder(race)),
                      position = position_stack(reverse = T)) +
  labs(fill = "race")
{% endhighlight %}

![center](../figure/blog-2019/02/TiltonMiranda-unnamed-chunk-3-1.png)

To see whether there truly is disparity between race affluence, we compute the correlation between percent of non-white individuals in a state and the percent of people living in poverty, using the county-wise data within each state. We use group_by() to split and summarise() to apply the correlation function, and then display the output as one combined table to compare values. Ohio shows no correlation between race and poverty, but the other four states show decidedly positive correlations. Interestingly, Wisconsin has the largest correlation between non-white population and poverty of the states reported, and the correlation larger by quite a significant margin.


{% highlight r %}
midwest %>%
  mutate(perc_nonwhite = percblack + percamerindan + percasian + percother) %>%
  group_by(state) %>% 
  summarise(cor_pov_race = cor(percbelowpoverty, perc_nonwhite))
{% endhighlight %}



{% highlight text %}
## # A tibble: 5 x 2
##   state cor_pov_race
##   <chr>        <dbl>
## 1 IL          0.327 
## 2 IN          0.201 
## 3 MI          0.152 
## 4 OH         -0.0211
## 5 WI          0.800
{% endhighlight %}

This analysis does not claim to represent any absolute truth about the midwest or its residents, as it is purely observational and I have not explored any other covariates that may further inform the relationship above. However, it does provide strong motivation for further exploration and suggests that there is much progress to be made with supporting people of color in the midwest.
