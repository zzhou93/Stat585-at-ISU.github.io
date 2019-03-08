
---
title: "All that legal stuff..."
author: "Xin Zhang"
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

R is distributed under the terms of the GNU GENERAL PUBLIC LICENSE, either Version 2, June 1991 or Version 3, June 2007. A copy of the version 2 license is in file R_HOME/doc/COPYING and can be viewed by RShowDoc("COPYING"). Version 3 of the license can be displayed by RShowDoc("GPL-3"). (https://www.rdocumentation.org/packages/base/versions/3.5.2/topics/license)

2. **Answer the three questions listed above for the licenses: MIT, GPL-3,  LGPL-3, and CC-0. Note that some of the questions might not be answered with a simple yes/no. In that case, go into more detail, but do not just copy the terms of the license.**

- MIT (https://en.wikipedia.org/wiki/MIT_License)
(1) Yes: 'without limitation the rights to use, copy, modify and merge copies of the Software.'
(2) Yes: 'without limitation the rights to publish, distribute, sublicense, and/or sell copies of the Software.'
(3) No one: 'the software is provided "as is", without warranty of any kind.'

- GPL-3 (https://www.gnu.org/licenses/gpl-3.0.en.html)
(1) Yes: 'the GNU General Public License is intended to guarantee your freedom to share and change all versions of a program--to make sure it remains free software for all its users.'
(2) Yes: 'you are allowed to sell copies of the modified program commercially, but only under the terms of the GNU GPL.' 
(3) No one: 'with this licenses, you can avoid the risk of having to compete with a proprietary modified version of your own work.'

- LGPL-3 (https://www.gnu.org/licenses/lgpl-3.0.en.html)
(1) Yes: 'You may copy, distribute and modify the software provided that modifications are described and licensed for free under LGPL.'
(2) Yes.
(3) No one.

- CC-0 (https://creativecommons.org/publicdomain/zero/1.0/)
(1) Yes: 'You can copy, modify, distribute and perform the work, even for commercial purposes, all without asking permission.'
(2) Yes: 'You can copy, modify, distribute and perform the work, even for commercial purposes, all without asking permission.'
(3) No: 'Unless expressly stated otherwise, the person who associated a work with this deed makes no warranties about the work, and disclaims liability for all uses of the work, to the fullest extent permitted by applicable law.'


3. **Assume that you are in the process of making a package for your own graduate work. Describe considerations that come into play in deciding on a license. In case you are not quite at that stage in your graduate studies yet, come up with a likely scenario. Describe it and discuss.**

I think for my graduate work, I'd like use the GPL-3. For example, I will make a package for my previous work SCUSUM under GPL-3 license because:

(1) this work is public for researchers. I'm fine that other researchers modify and improve my method.

(2) I'm fine with other people getting profit frome my work.

(3) also right now I'm not focusing on that work and I cannot keep updating and maintaining that package. So it will be good with GPL-3 license that I don't need to be responsible.
