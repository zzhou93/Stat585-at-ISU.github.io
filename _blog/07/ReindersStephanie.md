---
title: "All that legal stuff..."
author: "Stephanie Reinders"
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

According to [r-project.org](https://www.r-project.org/Licenses/) R is licensed under GPL-2/GPL-3 as a package.

2. **Answer the three questions listed above for the licenses: MIT, GPL-3,  LGPL-3, and CC-0. Note that some of the questions might not be answered with a simple yes/no. In that case, go into more detail, but do not just copy the terms of the license.**

- MIT:
    1. Modifications: Yes. If I use this license others may modify and distribute my package with the caveat that they must include a copy of the license and copyright notice.
    2. Profit: Yes. If I use this license others may use my package for profit.
    3. Responsibility: Neither I nor other authors or copyright holders are responsible.
- GPL-3:
    1. Modifications: Yes. If I use this license others may modify and distribute my package with the following caveats:
        - They must include a copy of the license and copyright notice.
        - They must distribute their changes under the GPL-3 license.
        - They must make their source code available.
        - They must document their changes.
    2. Profit: Yes. If I use this license others may use my package for profit.
    3. Responsibility: Neither I nor other authors or copyright holders are responsible.
- LGPL-3:
    1. Modifications: Yes. If I use this license others may modify and distribute my package with the following caveats (and the following caveats have a caveat. If software uses my work as a library, the software may be distributed under a different license and without making source code for the software available):
        - They must include a copy of the license and copyright notice.
        - They must distribute their changes under the GPL-3 license.
        - They must make their source code available.
        - They must document their changes.
    2. Profit: Yes. If I use this license others may use my package for profit.
    3. Responsibility: Unless required by law or if we agree in writing, neither I nor other authors or copyright holders are responsible.
- CC-0: 
    1. Modifications: Yes.
    2. Profit: Yes.
    3. Responsibility: Neither I nor other authors or copyright holders are responsible.


3. **Assume that you are in the process of making a package for your own graduate work. Describe considerations that come into play in deciding on a license. In case you are not quite at that stage in your graduate studies yet, come up with a likely scenario. Describe it and discuss.**

I like the idea of releasing my research code under a GPL-3 so that others who would like to use my work would also need to make their source code available. My research is funded by CSAFE so I need to check to see if they have requirements for what license I use.
