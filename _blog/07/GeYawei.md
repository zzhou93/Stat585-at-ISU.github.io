---
title: "All that legal stuff..."
author: "Yawei Ge"
topic: "07"
layout: post
root: ../../../
---
**1. Under what license does R operate?**

R is under GPL (version 2 or later) license.

**2. Answer the three questions listed above for the licenses: MIT, GPL-3, LGPL-3, and CC-0. Note that some of the questions might not be answered with a simple yes/no. In that case, go into more detail, but do not just copy the terms of the license.**

**For Question 1: Are you and your collaborators fine with other people modifying your work and then sharing the modified work?**

MIT License: work can be modified and shared by other people; but the part of the code under MIT should still be under MIT license.

GLP-3 License: work can be modified and shared by other people; but the software or modifications using GPL3-licensed code must also be under GPL-3. And changes should be stated.

LGPL-3 License: work can be modified and shared by other people; but the software or modifications using LGPL3-licensed code must also be under LGPL-3. And changes should be stated. However, applications using the library don't have to be under LGPL-3. (This license is mainly applied to libraries)

CC-0 License: work can be modified and shared by other people freely.

**For Question 2: Are you and your collaborators fine with other people making a profit from those derivations?**

MIT License: work can be used for commercial purpose.

GLP-3 License: work can be used for commercial purpose.

LGPL-3 License: work can be used for commercial purpose.

CC-0 License: work can be used for commercial purpose.

**For Question 3: Who is responsible if your software does not do what it promises to do?**

MIT License: the author of the work is not responsible for possible failure.

GLP-3 License: the author of the work is not responsible for possible failure.

LGPL-3 License: the author of the work is not responsible for possible failure.

CC-0 License: the author of the work is not responsible for possible failure.


**3. Assume that you are in the process of making a package for your own graduate work. Describe considerations that come into play in deciding on a license. In case you are not quite at that stage in your graduate studies yet, come up with a likely scenario. Describe it and discuss.**

For example, if I have written a ggplot2 extension, I want to share my package widely and freely, but at the same time, I still want to keep the Copyright, i.e. this is my work. Also, because I worked on the extension of ggplot2, I need to follow the GPL2 which ggplot2 used. And that is fine in this case.






















