---
title: "Blog Post 7: All that legal stuff"
author: "Kellie McClernon"
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
R is licensed under GPL-3.  

2. **Answer the three questions listed above for the licenses: MIT, GPL-3,  LGPL-3, and CC-0. Note that some of the questions might not be answered with a simple yes/no. In that case, go into more detail, but do not just copy the terms of the license.**  

  * *MIT*
    + This license would allow of modification of work and distribution as long as the modified work contains the original license and copyright information.
    + Other people are free to make a profit from those derivations under this license.
    + You would not hold any liable or be responsible if your software does not do what it promises.
  * *GPL-3*
    + This license would allow of modification of work and distribution as long as the modified work contains the original license and copyright information along with the original and modified source code with stated changes.
    + Other people are free to make a profit from those derivations, but the complete and modified source code must be made publicly available.
    + You would not hold any liablility.
  * *LGPL-3*
    + Used mostly for software libraries, this license would allow of modification of work and distribution as long as the modified work contains the original license and copyright information along with the source code under LGPL-3.
    + Other people are free to make a profit from those derivations. If applications use the your software under this license, the application is not required to provide source code for the complete work (original and modified).
    + You would not hold any liablility.
  * *CC-0*
    + Used mostly for datasets, this license reliqueshes all of your rights to your work so that it is free to be used and distributed by anyone.
    + Other people are allowed to make a profit from your work and any derivations of it.
    + You would not hold any liablility.

3. **Assume that you are in the process of making a package for your own graduate work. Describe considerations that come into play in deciding on a license. In case you are not quite at that stage in your graduate studies yet, come up with a likely scenario. Describe it and discuss.**  

Since all the above licenses allow modification of the code potentially for profit, the main consideration seems to be how I want modifications to be handle. Would I require modifications to the code to be included in the open source file or could the codes - parts or in its entirety - be hidden? If I made my code public, I most likely would want modifications to be clearly documented, which would be then a GPL-3 license. Additionally, if my work builds on existing packages, then I would need to consider the license under which those essential packages are built. I would need to make sure that any distribution of my package (if it is derivative) is in accordance with their licensing.
