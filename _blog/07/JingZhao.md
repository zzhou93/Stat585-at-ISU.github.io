---
title: "All that legal stuff..."
author: "Jing Zhao"
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
    R use GPL-3.
2. **Answer the three questions listed above for the licenses: MIT, GPL-3,  LGPL-3, and CC-0. Note that some of the questions might not be answered with a simple yes/no. In that case, go into more detail, but do not just copy the terms of the license.**

*MIT*: 
MIT is a simple and permissive license. 
Anyone can freely use or distrubute the code as long as the license must be distributed with the code. 
Therefore, it is ok for other people modifying our work and sharing their work. It is also fine if others making a profit from the derications. But nobody is responsible if their software does not do what it promises.

*GPL-3*: 
This means that anyone who distributes your code in a bundle must license the whole bundle in a GPL-compatible way. Additionally, anyone who distributes modified versions of your code (derivative works) must also make the source code available
Anyone could distribute or modify the software as long as they have description of the modification. 
Therefore, it is ok that others modifying our work, sharing their modificated work, or using for commercial. But no one responsible their software does not do what it promises.

*LGPL-3*: 
The LGPL is similar to the GPL, but does not require that all components of the derivative work be released. Instead, it requires source code release of only those components that are modifications.
So it is ok that others modify our work, sharing their modificated work, and using for commercial. No one must to be responsible if their software does not do what it promises.

*CC-0*: 
The software or pacakges can be used by anyone for any purpose under this license. So it is ok that others modify our work, share their modificated work, or use for making profit. No one must to be responsible if their software does not do what it promises.


3. **Assume that you are in the process of making a package for your own graduate work. Describe considerations that come into play in deciding on a license. In case you are not quite at that stage in your graduate studies yet, come up with a likely scenario. Describe it and discuss.**

I remember that I did my MS thesis for consequence of wrong assumption of repeated measure analysis. Thousands of datasets with different variance covariance structure settings were simulated and were tried to do the repeated measure analysis in R. Till the last step, I need to identify the treatment effect at individual time point. This can be done easily using slice in SAS, but I could not find similar package in R. So, I plan to write a package corresponding for the function of slice in SAS. The goal of my package is to help reseracher to easily do the simple effect analysis from repeated measure analysis in R. Considering license, I may think to use GPL-3. User could copy, distribute, and modify the software as long as they have description of the modification. 
