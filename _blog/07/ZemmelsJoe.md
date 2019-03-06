---
title: "All that legal stuff..."
author: "Joe Zemmels"
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

  R operates under the GNU General Public License, version 3 (GPL-3).

2. **Answer the three questions listed above for the licenses: MIT, GPL-3,  LGPL-3, and CC-0. Note that some of the questions might not be answered with a simple yes/no. In that case, go into more detail, but do not just copy the terms of the license.**

  **MIT:**
  
  1. Are you and your collaborators fine with other people modifying your work and then sharing the modified work?
  
    This license states that anyone can do essentially anything with the work, as long as they include the license along with code.
      
  2. Are you and your collaborators fine with other people making a profit from those derivations?
  
    The license states that anyone can make a profit with derivatives of the original work, as long as they include the license along with their changes.

  3. Who is responsible if your software does not do what it promises to do?
  
    No one is responsible if the software does not work. The authors or copyright holders are not liable if their software does not do what it promises.
  
  **GPL-3:**
  
  1. Are you and your collaborators fine with other people modifying your work and then sharing the modified work?
    
      The GPL-3 license states that anyone can modify the work as long as they release the source code for everything that uses the original work, state their source, and document the changes they have made.

  2. Are you and your collaborators fine with other people making a profit from those derivations?
    
      The GPL-3 license states that distributors of software under the patent can charge for them if they wish.

  3. Who is responsible if your software does not do what it promises to do?
    
      It does not appear that anyone is responsible if software does not do what it promises to do. The license states that "there is no warranty for this free software," which I interpret to mean that it is not the author's responsibility to fix any issues that arise when others use their software.
  
  **LGPL-3:**
  
  1. Are you and your collaborators fine with other people modifying your work and then sharing the modified work?
  
    The LGPL is similar to the GPL, but does not require that all components of the derivative work be released. Instead, it requires source code release of only those components that are modifications of the original (like a library).

  2. Are you and your collaborators fine with other people making a profit from those derivations?
  
    The license states that derivative works can be used to make a profit.

  3. Who is responsible if your software does not do what it promises to do?
  
    The authors or copywrite holders of the original work are not liable if the software does not do what it promises.
  
  **CC-0:**
  
  1. Are you and your collaborators fine with other people modifying your work and then sharing the modified work?
  
    Under the Creative Common license, anyone can do anything with the original work.

  2. Are you and your collaborators fine with other people making a profit from those derivations?
  
    Anyone can use the original or derivative works for making a profit.

  3. Who is responsible if your software does not do what it promises to do?
  
    The authors or copywrite holders of the original work are not liable if the software does not do what it promises.

3. **Assume that you are in the process of making a package for your own graduate work. Describe considerations that come into play in deciding on a license. In case you are not quite at that stage in your graduate studies yet, come up with a likely scenario. Describe it and discuss.**

  One factor that could go into deciding on a license is the amount of credit that I would want for any derivative works. The GPL-3 license seems to be the most restrictive in that it requires disclosure of the original source and inclusion of the original work in any distribution. A GPL-3 licensed work also requires that the source code of any derivative works also be published freely. There's a good chance that companies hoping to make a profit with the software that they develop would steer away from such terms, so another consideration to make is the amount of transparency I would like evolutions of my work to have. I suppose if my intent is to further my field of study and openly communicate my results rather than make a profit, then the GPL-3 license would be the optimal license to work with. However, if, for example, I plan on using my work in a future job at a company/institution that prefers keeping its work proprietary, then I would likely use something less restrictive like the LGPL-3 or MIT license.
