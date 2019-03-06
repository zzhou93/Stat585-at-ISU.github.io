---
title: "All that legal stuff..."
author: "Yones Khaledian"
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

  -As far as I can check the modification in advance, I am okay that other people modify my work.

2. Are you and your collaborators fine with other people making a profit from those derivations?

  -No, I definitely disagree with this statement. 

3. Who is responsible if your software does not do what it promises to do?

  -I think that the creator and author both are responsible. 


Write a blog post addressing the following questions: 

1. **Under what license does R operate?**

R works under an open source, like GPL-2 or BSD. 

2. **Answer the three questions listed above for the licenses: MIT, GPL-3,  LGPL-3, and CC-0. Note that some of the questions might not be answered with a simple yes/no. In that case, go into more detail, but do not just copy the terms of the license.**
MIT:
1. Are you and your collaborators fine with other people modifying your work and then sharing the modified work?

Yes. The others can modify the work, and distribute the code.   

2. Are you and your collaborators fine with other people making a profit from those derivations?

Yes, people can modify and sell it. 

3. Who is responsible if your software does not do what it promises to do?

Under this license, there is no any warranty. So, nobody is responsible to any liability.  

GPL-3:
1. Are you and your collaborators fine with other people modifying your work and then sharing the modified work?

Everyone can copy and distribute, but nobody is allowed to modify it. 

2. Are you and your collaborators fine with other people making a profit from those derivations?
There is no any patent claim if anybody wants to sell it. 

3. Who is responsible if your software does not do what it promises to do?

Under this license, there is a limited liability.   

LGPL-3:
1. Are you and your collaborators fine with other people modifying your work and then sharing the modified work?

Any developer can modify it, but they should distribute modified version under the same LGPL license. 

2. Are you and your collaborators fine with other people making a profit from those derivations?

It is permissive to sell. 

3. Who is responsible if your software does not do what it promises to do?

The modifiers are responsible to any changes that they make. 

CC-0:

1. Are you and your collaborators fine with other people modifying your work and then sharing the modified work?

There is no limitation to modify or distribute the wok. 

2. Are you and your collaborators fine with other people making a profit from those derivations?

It depends on the specific Creative Commons (CC) license to be used commercially or not. 
3. Who is responsible if your software does not do what it promises to do?

The modifiers are responsible to any changes that they make. 


3. **Assume that you are in the process of making a package for your own graduate work. Describe considerations that come into play in deciding on a license. In case you are not quite at that stage in your graduate studies yet, come up with a likely scenario. Describe it and discuss.**


I prefer to use the license that allow people to modify my codes, but I prefer to check it before publicizing it. In doing so, I will be responsible it the code does not work properly. I don’t mind if anybody sell my codes. However, anybody sells it, I would not be responsible if codes work or not. 
