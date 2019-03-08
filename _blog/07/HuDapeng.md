---
title: "All that legal stuff..."
author: "Dapeng Hu"
topic: "07"
layout: post
root: ../../../

---

Write a blog post addressing the following questions: 

1 **Under what license does R operate?**

R operates under the [GNU GPL v2](https://en.wikipedia.org/wiki/GNU_General_Public_License#Version_2) license.

2 **Answer the three questions listed above for the licenses: MIT, GPL-3,  LGPL-3, and CC-0. Note that some of the questions might not be answered with a simple yes/no. In that case, go into more detail, but do not just copy the terms of the license.**

**MIT**: 

Q1: Yes, but they must include the original copyright and license notice in any copies of the work.

Q2: Yes, but they also need to include the original copyright and license notice in any copies of the work.

Q3: Users should be responsible. Authors or copyright holders should not be liable.


**GPL-3**:

Q1: Yes, but they must obey several rules before modifying or distributing. They must include the original software and track changes or dates in source files. They also need to include the license and copyright of the original software (or work). And all modifications or software that including GPL-licensed codes should also be available under the GPL license. Besides, they should add the information needed to modify and reinstall the software.

Q2: Yes, but they also need to follow the rules listed in Q1.

Q3: Users should be responsible. 

**LGPL-3**:

Q1: They can modify and distribute the software if that modifications are described and licensed for free under LGPL. Derivatives works can only be redistributed under LGPL.

Q2: Yes, they can.

Q3: There is no information in the license text so I think it has the same terms as in GPL-3. If so, the users should be responsible.

**CC-0**:

Q1: Yes, anyone can use freely for any purpose.

Q2: Yes.

Q3: Users should be responsible.

3 **Assume that you are in the process of making a package for your own graduate work. Describe considerations that come into play in deciding on a license. In case you are not quite at that stage in your graduate studies yet, come up with a likely scenario. Describe it and discuss.**

If I want to release my package, I think the biggest consideration is whether I modify some functions in the imported or depended packages. If these packages are under GLP license, then I should also use GLP license. Another consideration would be I want other people track changes when they modify my source file because otherwise I have no idea what has been changed. Based on the two considerations, I would like to choose GPL license which I find most r packages are using.


