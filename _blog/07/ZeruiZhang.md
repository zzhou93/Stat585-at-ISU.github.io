---
title: "All that legal stuff..."
author: "Zerui Zhang"
topic: "07"
layout: post
root: ../../../
---

Here, we want to focus on the use of licenses in R packages.
There are several important aspects to consider when choosing a license for your work. 
Three of the main questions to answer are: 

1. Are you and your collaborators fine with other people modifying your work and then sharing the modified work?

2. Are you and your collaborators fine with other people making a profit from those derivations?

3. Who is responsible if your software does not do what it promises to do?

Write a blog post addressing the following questions:

1. **Under what license does R operate?**

    R as a package is licensed under GPL-2 | GPL-3. [(Link)](https://www.r-project.org/Licenses/)

2. **Answer the three questions listed above for the licenses: MIT, GPL-3,  LGPL-3, and CC-0. Note that some of the questions might not be answered with a simple yes/no. In that case, go into more detail, but do not just copy the terms of the license.**

    **MIT**

    1. Yes, as long as you include the original copyright and license notice in any copy of the software/source.

    2. Yes, as long as you include the original copyright and license notice in any copy of the software/source.

    3. No one. The work is provided "as is". We may not hold the author liable.

    **GPL-3**

    1. Yes, as long as you track and state the changes/dates in source files, preserve the licences and copyright and make any modifications available.

    2. Yes, as long as you track and state the changes/dates in source files, preserve the licences and copyright and make any modifications available.

    3. No one.

    **LGPL-3**

    1. Yes, as long as you disclose the source, preserve the licences and copyright and state the changes.

    2. Yes, as long as you disclose the source, preserve the licences and copyright and state the changes.

    3. No one.

    **CC-0**

    1. Yes.

    2. Yes.

    3. No one.


3. **Assume that you are in the process of making a package for your own graduate work. Describe considerations that come into play in deciding on a license. In case you are not quite at that stage in your graduate studies yet, come up with a likely scenario. Describe it and discuss.**

    It depends on how much code will be completely original from my work. If I want to do some derivative work or modifications on some currently available package, I will first check what licenses these packages use and follow their choice. In some situations that I write a completely original package, I'd like to use GPL-3 so that if others wants to add some features or make some modifications, I could also get access to their parts.
