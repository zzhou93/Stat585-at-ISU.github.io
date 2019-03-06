---
title: "All that legal stuff..."
author: "Min Zhang"
topic: "07"
layout: post
root: ../../../
---

Read through the chapter on [metadata](http://r-pkgs.had.co.nz/description.html) from Wickham’s book on R packages.

Here, we want to focus on the use of licenses in R packages. There are several important aspects to consider when choosing a license for your work. Three of the main questions to answer are:

(i) Are you and your collaborators fine with other people modifying your work and then sharing the modified work?

(ii) Are you and your collaborators fine with other people making a profit from those derivations?

(iii) Who is responsible if your software does not do what it promises to do?


Q1. **Under what license does R operate?**

GPL-2 or GPL-3

Q2. **Answer the three questions listed above for the licenses: MIT, GPL-3,  LGPL-3, and CC-0. Note that some of the questions might not be answered with a simple yes/no. In that case, go into more detail, but do not just copy the terms of the license.**

MIT:

(i) Yes: no limitation the rights to modify under the condition of including the copyright notice and permission notice. 

(ii) Yes: no limitation the rights to sell copies of the Software under the condition of including the copyright notice and permission notice.

(iii) No one is responsible if the software does not do as promises: the software is provided "as is", without warranty of any kind. 

GPL-3:

(i) Yes, but with responsibilities to respect the freedom of others. 

(ii) Yes, but with responsibilities to respect the freedom of others. 

(iii) No one: as it says there is no warranty for this free software.

LGPL-3:

(i) Yes: with requirement of source code of modifications. 

(ii) Yes.

(iii) No one. 

CC-0:

(i) Yes.

(ii) Yes.

(iii) No one.

Q3. **Assume that you are in the process of making a package for your own graduate work. Describe considerations that come into play in deciding on a license. In case you are not quite at that stage in your graduate studies yet, come up with a likely scenario. Describe it and discuss.**

Under the scenario that I want to write a package for Gibbs Sampler friendly to censored observations, I might want to build my work upon rags (I have difficulty in analyzing left and interval censored data with the current rags, so I assume this is a niche). Then I would consider using GPL-2, which is the license of rjags. It gives me freedom to distribute copies of free software, to receive source code, and to modify the software or use pieces of it in new free programs.  
