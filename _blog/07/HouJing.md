---
title: "All that legal stuff..."
author: "Jing Hou"
root: ../../../
layout: post
topic: '07'
---

Three of the main questions to answer are: 

1. Are you and your collaborators fine with other people modifying your work and then sharing the modified work?

2. Are you and your collaborators fine with other people making a profit from those derivations?

3. Who is responsible if your software does not do what it promises to do?


Write a blog post addressing the following questions: 

1. **Under what license does R operate?**

R as a package is licensed under GPL-2 | GPL-3. Some header files are distributed under LGPL-2.1. (https://www.r-project.org/Licenses/)

2. **Answer the three questions listed above for the licenses: MIT, GPL-3,  LGPL-3, and CC-0. Note that some of the questions might not be answered with a simple yes/no. In that case, go into more detail, but do not just copy the terms of the license.**

**MIT**: 
1) 2) Yes. Other people can do whatever they want as long as they include the copyright and license notices in their work. They can copy, modify, distribute, sublicense, and use the work commercially. 3) No one is responsible if the software does not do what it promises to do. The authors or copyright holders are not liable in any case.

**GPL-3**:
1) 2) Yes. Other people can copy, modify, distribute the software as long as they state changes, disclose source code, include the copyright and license notices. They can also use the work for commercial purposes. 3) There is no warranty for this free software. Since the modified versions are required to be marked as changed, the authors of previous versions are not responsible for any problems.

**LGPL-3**:
1) 2) Yes. This license is mainly for libraries. Others can copy, distribute and modify the software under the same condition as the GPL-3. But the applications using the library don't have to be under LGPL. They can also use the work for commercial purposes. 3) There is no warranty. The authors or copyright holders are not responsible if the software does not do what it promises to do.

**CC-0**:
1) 2) Yes. This kind of license releases software into the public domain. So anyone can use it for any purpose. 3) No one is responsible if the software does not do what it promises to do.

3. **Assume that you are in the process of making a package for your own graduate work. Describe considerations that come into play in deciding on a license. In case you are not quite at that stage in your graduate studies yet, come up with a likely scenario. Describe it and discuss.**

I think this will depend on the dependencies of my package. If I use a lot of functions from other packages in my work, I'd better use the same licenses as they do. If my package is very creative and very useful, I will release it by using GPL-3. I can share my work with others and keep my right at the same time.

