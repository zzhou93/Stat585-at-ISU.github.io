---
title: "All that legal stuff..."
author: "Yonghui Huo"
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
# When I check the license for my R studio, it shows this software is distributed under the terms of the GNU General Public License, either Version 2, June 1991 or Version 3, June 2007. The terms of version 2 of the license are in a file called COPYING which you should have received with this software and which can be displayed by RShowDoc("COPYING").Version 3 of the license can be displayed by RShowDoc("GPL-3").

2. **Answer the three questions listed above for the licenses: MIT, GPL-3,  LGPL-3, and CC-0. Note that some of the questions might not be answered with a simple yes/no. In that case, go into more detail, but do not just copy the terms of the license.**

# For MIT(1) Yes.Must have the license. (2) Yes. The answer is same for (1). Users can have permssion to use, copy, modify, merge, publish, distribute, and even sublicense of the Software.(3) no one is responsible if software does not do what it promises to do.

# For GPL-3(1)yes, but should include the source code and state the change. (2) Yes.Same to (1). (3) no one, no warranty. Nobody is responsible to any liability.

# For LGPL-3(1) No, but users can convey a copy of the modified version under this License.(2) Yes.Same to (1).(3) The User should take resposibility to the damage they make.

# For CC-0(1) Yes,There is no limitation .(2) Yes.(3) Users are take charge of that.

3. **Assume that you are in the process of making a package for your own graduate work. Describe considerations that come into play in deciding on a license. In case you are not quite at that stage in your graduate studies yet, come up with a likely scenario. Describe it and discuss.**

# Fristly, I will choose license depend on the package I make. If I just want to use my package to do the research on my graduate study, I will choose the GPL-3 license. If I work in a company, LGPL-3 may be the better choose. Besides, I will allow users to copy, modify my package, but I will not take resposible for any change they make. 
