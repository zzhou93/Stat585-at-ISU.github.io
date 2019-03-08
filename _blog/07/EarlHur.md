---
title: "All that legal stuff..."
author: "Earl Hur"
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

    According to the R website, https://www.r-project.org/Licenses/, *R as a package is licensed under GPL-2 | GPL-3*

2. **Answer the three questions listed above for the licenses: MIT, GPL-3,  LGPL-3, and CC-0. Note that some of the questions might not be answered with a simple yes/no. In that case, go into more detail, but do not just copy the terms of the license.**

      For MIT:
      
      The MIT license gives permission to anyone to modify and share the work. It also allows to make profit as we could sell the copie of the software as long as they included the license with any changes. No one is responsible for the software performance. Neither the authors nor the copy writers are liable for this according to the license.
      
      For GPL-3:
      
      This license also gives permission to anyone to modify and share the work. It states that as long as the sources are attached with all the changes and its original code. It is up to the distributors to charge for using their software without any restrictions. Like the MIT liscense, fixing the code error is not the author or copywriter's responsibility.
  
      For LGPL-3:
      
      LGPL-3 is quite similar to GPL-3 as it allows any modification or distribution of the work. However, this license only requires the source to be aligned with the modification of the original. It also allows to make a profit. Again, neither the author nor the copywriters are responsible for the performance of the software.
  
      For CC-0:
      
      This license states anyone can make modification and make profit. Like the above license, the authors and copywriters do not have responsibility for the performance of the software.

3. **Assume that you are in the process of making a package for your own graduate work. Describe considerations that come into play in deciding on a license. In case you are not quite at that stage in your graduate studies yet, come up with a likely scenario. Describe it and discuss.**

      I have not built any packages yet in my graduate work. If I want to make packages with functions that I want others to be contributed freely and make improvement, I would choose less restrictive license, such as CC-0 or LGPL-3. Using these licenses will allow others to change my functions and also myself to learn from other's contribution. Even though I believe it does not really matter for what license I should choose to make a profit, I would choose GPL-3, which is less restrictive in selling the copies of the work, (in case I want to make money out of my software). 
