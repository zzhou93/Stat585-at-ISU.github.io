---
title: "Blog 7 - Licenses"
author: "Lydia English"
topic: "07"
layout: post
root: ../../../
---

1. Are you and your collaborators fine with other people modifying your work and then sharing the modified work?

2. Are you and your collaborators fine with other people making a profit from those derivations?

3. Who is responsible if your software does not do what it promises to do?


Write a blog post addressing the following questions: 

1. **Under what license does R operate?**
    R operates under the GPL-2 or GPL-3 [licenses](https://www.r-project.org/Licenses/), although there are more license options for different packages. 

2. **Answer the three questions listed above for the licenses: MIT, GPL-3,  LGPL-3, and CC-0. Note that some of the questions might not be answered with a simple yes/no. In that case, go into more detail, but do not just copy the terms of the license.**

**MIT:**
  An MIT license allows persons to distribute, modify, use, etc. the package in any way they want. The only restriction is that the license and copywrite notice must travel with any versions of the package. It's ok for people to profit off the package. If the software doesn't perform as it was intended the original authors are not liable damages/legal recourse. 

**GPL-3:**
  A GNU General Public License (v3) allows users to modify, use, and distribute packages so long as changes are tracked in the source files and the license and copywrite files are preserved. The source code must be available to all, even after the modifications. It appears that it's ok for people to profit from this package under this license, but once again, the authors are not liable if the package doesn't perform (no warranty). 

**LGPL-3:**
  A GNU Lesser General Public License is similar to the GPL-3 but this license generally applies to libraries. The packages may be modified and distributed so long as any changes remain freely licensed under an LGPL. I believe it's ok for people to profit. Similarly, any work that is derivative from the package library must also be distrubuted under a LGPL. In other words it cannot be distributed under a different sublicense. Once again the authors of the library/packages are not liable under any warranty if the package does not perform. 
  
  
**CC-0**:
  A Creative Commons license appears to be the most lax of them all, allowing anyone to do anything they chose with package, including make a profit off of it. There aren't requirements to distribute a license. Understandably the authors of the original package are not responsible for any problems with the software. 


3. **Assume that you are in the process of making a package for your own graduate work. Describe considerations that come into play in deciding on a license. In case you are not quite at that stage in your graduate studies yet, come up with a likely scenario. Describe it and discuss.** One of my committee members helped me design a very simple package to house all my data from my graduate research. Ideally I'd like for that data to be made publicly available and open sourced, but I also think I would want any change/modifications to be tracked and documented if it were to be distributed. I don't have a problem with people making a profit off it and wouldn't want to be held liable, so it seems like a GPL-3 license would work. Right now the package has point coordinates that identify site locations so we will have to make sure all that information is deleted and anonymized before it goes public. 
