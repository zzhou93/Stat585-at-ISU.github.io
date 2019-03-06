---
title: "All that legal stuff..."
author: "Firstname Lastname"
topic: "07"
layout: post
root: ../../../
---

## Background:

The `DESCRIPTION` file of a package contains the package's meta information. Most of the fields in this file are quite straight forward: author, version number, and a short package description. When you call `library(help="<package name>")` for  package `<package name>` you can see the contents of the `DESCRIPTION` file for that package (and some parts of the `NAMESPACE` file).

Read through the chapter on [metadata](http://r-pkgs.had.co.nz/description.html) from Wickham's book on R packages. 

Here, we want to focus on the use of licenses in R packages.
There are several important aspects to consider when choosing a license for your work. 
Three of the main questions to answer are: 

1. Are you and your collaborators fine with other people modifying your work and then sharing the modified work?

2. Are you and your collaborators fine with other people making a profit from those derivations?

3. Who is responsible if your software does not do what it promises to do?


Write a blog post addressing the following questions: 

1. **Under what license does R operate?**
R operates under three licenses: MIT, which lets people use and distribute your code permissively, GPL-2 or GPL-3 which codes are usually distributed with a bundle in GPL, and CC0 which is very free to use and the author do not have the right to restrict the code distribution and modification. 

2. **Answer the three questions listed above for the licenses: MIT, GPL-3,  LGPL-3, and CC-0. Note that some of the questions might not be answered with a simple yes/no. In that case, go into more detail, but do not just copy the terms of the license.**
MIT 1. yes
    2. no
    3. the author and collaborators that are listed in the DESCRIPTION file 

GPL-3 1. yes
      2. yes 
      3. only until the last author who made the last modification of the code, and went on licensing it
 
LGPL-3  1. yes
        2. yes
        3. only until the last author who made last modification of the code, and went on licensing it

CC0 - 1. no 
3. **Assume that you are in the process of making a package for your own graduate work. Describe considerations that come into play in deciding on a license. In case you are not quite at that stage in your graduate studies yet, come up with a likely scenario. Describe it and discuss.**
In my graduate work, I deal with plant disease progression data. A progression data across time interval likely to include a sort of modeling of the dataset, thus a complex model with multiple parameters that is specific to my plant disease I work with, soybean sudden death syndrome might be created. In which case, the considerations that I may have to think about are my position as a masters student that is very temporary, I might be able to choose from giving the code credits to my lab PI, or even ISU if it brings any higher credibility. However, if I know the package is sort of a more complex and can be more widely used, and if it somehow generates some revenue, I may want to heavily consider to put my name only in it if it was exclusively developed by me. 
