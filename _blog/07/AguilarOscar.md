---
title: "All that legal stuff..."
author: "Oscar Aguilar"
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

  R operates under GPL-2 or GPL-3. See the following [link](https://www.R-project.org/Licenses/).
  
2. **Answer the three questions listed above for the licenses: MIT, GPL-3,  LGPL-3, and CC-0. Note that some of the questions might not be answered with a simple yes/no. In that case, go into more detail, but do not just copy the terms of the license.**

  **MIT**
  1. This license is simple and permissive. It allows others to use and freely distribute your code subject to only one 
     restriction: the license must always be distributed with the code.
  2. The license states that anyone can make profit from code derivations.
  3. The license states that no one is responsible if the software doesn't do what it promises to do.
  
  **GPL-3**
  1. The license states that anyone may copy, modify the software as long as you track the changes/dates in source files.
  2. The license states that distributors of software under the patent can charge for them if they wish.
  3. The license states the following: "there is no warranty for this free software."
  
  **LGPL-3**
  1. The license states that everyone is permitted to copy and distribute verbatim copies of this license document, but  
     changing it is not allowed. 
  2. The license states that derivative works can be used to make a profit.
  3. The license states that the authors of the original work are not liable if the software doesn't do what it promises to do.
     
  **CC-0**
  1. The license states that anyone can do anything with the original work.
  2. The license states that anyone can use the original or derivative works for making a profit.
  3. The license states that the authors of the original work are not liable if the software doesn't do what it promises to do.


3. **Assume that you are in the process of making a package for your own graduate work. Describe considerations that come into play in deciding on a license. In case you are not quite at that stage in your graduate studies yet, come up with a likely scenario. Describe it and discuss.**

My graduate studies have focused on machine learning in math-finance. If I decide to share the code that I wrote for my dissertation I would probably go with MIT or CC-0 license. However, if I decide to use it in industry applications, I would go with GPL-3.

