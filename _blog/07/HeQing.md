---
title: "All that legal stuff..."
author: "Qing He"
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
GNU General Public License


2. **Answer the three questions listed above for the licenses: MIT, GPL-3,  LGPL-3, and CC-0. Note that some of the questions might not be answered with a simple yes/no. In that case, go into more detail, but do not just copy the terms of the license.**
  1. Are you and your collaborators fine with other people modifying your work and then sharing the modified work?
MIT, desitribute with MIT license, modified version do not have to be "open source".
GPL-3: destribute code in a bundle and license it under GPL-3.
LGPL-3: modified version need to be under LGLP-3.
CC-0:Ok to share and modify, not restrictions about what license should be used. 

  2. Are you and your collaborators fine with other people making a profit from those derivations?
yes for all license listed above allow user to make profit from derivations. 

  3. Who is responsible if your software does not do what it promises to do?
Author is not responsible if software do not work as promised under all licenses listed above. 

3. **Assume that you are in the process of making a package for your own graduate work. Describe considerations that come into play in deciding on a license. In case you are not quite at that stage in your graduate studies yet, come up with a likely scenario. Describe it and discuss.**
None of the license above have too much restrictions, as long as the derivations using the same license, and CC0 doesn't even have this restriction. So, if I want to publish a package with only data in it, CC0 is a good choice. In my case, I am working a package that used to process Raman spectrum efficently, I hope the modified version of these codes are also open to the public, so other people and I can know what's the possible way to make the codes more effient. So GPL-3 and LGPL-3 licenses are more appropriate. 
