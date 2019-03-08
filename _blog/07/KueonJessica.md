---
title: "All that legal stuff..."
author: "Firstname Lastname"
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

R is licensed under GPL-2 or GPL-3. Some are distributed under LGPL-2.1. 

2. **Answer the three questions listed above for the licenses: MIT, GPL-3,  LGPL-3, and CC-0. Note that some of the questions might not be answered with a simple yes/no. In that case, go into more detail, but do not just copy the terms of the license.**

a. MIT
1. Are you and your collaborators fine with other people modifying your work and then sharing the modified work?

Yes. as long as we provide the copyright and license notices in our work.

2. Are you and your collaborators fine with other people making a profit from those derivations?

Yes. as long as they provide the copyright and license notices in their work.

3. Who is responsible if your software does not do what it promises to do?

No one. No one is liable in any case.

b. GPL-3

1. Are you and your collaborators fine with other people modifying your work and then sharing the modified work?

Yes. we can copy, modify, distribute the software as long as we include the copyright and license notices. It is also ok to work for commercial purposes.

2. Are you and your collaborators fine with other people making a profit from those derivations?

Yes. they can copy, modify, distribute the software as long as they include the copyright and license notices. 
It is also ok to work for commercial purposes.

3. Who is responsible if your software does not do what it promises to do?

R is a free software, so no one is liable in any case.
 

c. LGPL-3

1. Are you and your collaborators fine with other people modifying your work and then sharing the modified work?

Yes. we can copy, modify, distribute the software as long as we include the copyright and license notices. It is also ok to work for commercial purposes.

2. Are you and your collaborators fine with other people making a profit from those derivations?

Yes. they can copy, modify, distribute the software as long as they include the copyright and license notices. 
It is also ok to work for commercial purposes.

3. Who is responsible if your software does not do what it promises to do?

R is a free software, so no one is liable in any case.


d. CC-0

1. Are you and your collaborators fine with other people modifying your work and then sharing the modified work?

Since it is released to the public domain, so yes. 

2. Are you and your collaborators fine with other people making a profit from those derivations?

Since it is released to the public domain, so yes. 

3. Who is responsible if your software does not do what it promises to do?

R is a free software, so no one is liable in any case.



3. **Assume that you are in the process of making a package for your own graduate work. Describe considerations that come into play in deciding on a license. In case you are not quite at that stage in your graduate studies yet, come up with a likely scenario. Describe it and discuss.**

Let's say I make a R package for a class project. Under GPL2/LGPL, I would disclose my work and original code. If under MIT, it would be more conservative in terms of license and copyright. R users have to be aware that no one is responsible even if my package is defected. 
