---
title: "All that legal stuff..."
author: "Xiyuan Sun"
topic: "07"
layout: post
root: ../../../
---
Read through the chapter on [metadata](http://r-pkgs.had.co.nz/description.html) from Wickham's book on R packages. 

Here, we want to focus on the use of licenses in R packages.

There are several important aspects to consider when choosing a license for your work. 
Three of the main questions to answer are: 

1. Are you and your collaborators fine with other people modifying your work and then sharing the modified work?

2. Are you and your collaborators fine with other people making a profit from those derivations?

3. Who is responsible if your software does not do what it promises to do?


Write a blog post addressing the following questions: 

1. **Under what license does R operate?**

This software is distributed under the terms of the GNU General Public License, either Version 2, June 1991 or Version 3, June 2007.Version 3 of the license can be displayed by RShowDoc("GPL-3").

A small number of files (the API header files listed in R_DOC_DIR/COPYRIGHTS) are distributed under the LESSER GNU GENERAL PUBLIC LICENSE, version 2.1 or later.This can be displayed by RShowDoc("LGPL-2.1"), or obtained at the URI given. Version 3 of the license can be displayed by RShowDoc("LGPL-3").



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
      It says users can deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software.

  3. Who is responsible if your software does not do what it promises to do?
    
      The license states that "there is no warranty for this free software," which means that it is not the author's responsibility to fix any issues.
      
  **LGPL-3:**
  
  1. Are you and your collaborators fine with other people modifying your work and then sharing the modified work?
  
    The LGPL is similar to the GPL, but does not require that all components of the derivative work be released. Instead, it requires source code release of only those components that are modifications of the original.

  2. Are you and your collaborators fine with other people making a profit from those derivations?
  
    The license states that derivative works can be used to make a profit.

  3. Who is responsible if your software does not do what it promises to do?
  
    The authors of the original work are not liable if the software does not do what it promises.
  
  **CC-0:**
  
  1. Are you and your collaborators fine with other people modifying your work and then sharing the modified work?
  
    Anyone can do anything with the original work.

  2. Are you and your collaborators fine with other people making a profit from those derivations?
  
    Anyone can use the original or derivative works for making a profit.

  3. Who is responsible if your software does not do what it promises to do?
  
    The authors of the original work are not liable if the software does not do what it promises.


3. **Assume that you are in the process of making a package for your own graduate work. Describe considerations that come into play in deciding on a license. In case you are not quite at that stage in your graduate studies yet, come up with a likely scenario. Describe it and discuss.**
It depends on what I plan to use my package for. 

If I would share source codes to further a field rather than make a profit, then the GPL-3 license would be the optimal license to work with. 

If I plan on using my work in a future job at a company that prefers keeping its work private, then I would likely use something like the LGPL-3 or MIT license.
