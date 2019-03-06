---
title: "All that legal stuff..."
author: "Yudi Zhang"
topic: "07"
layout: post
root: ../../../
---

1. **Under what license does R operate?**

GPL-2 or GPL-3

2. **Answer the three questions listed above for the licenses: MIT, GPL-3,  LGPL-3, and CC-0. Note that some of the questions might not be answered with a simple yes/no. In that case, go into more detail, but do not just copy the terms of the license.**
- MIT
(1) Yes.
(2) Yes. It says users can deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software.
(3) If it does not do what it promises to do. The software is provided "as is", without a warranty of any kind.
- GPL-3
(1) Yes, but users should include the source code, state the changes accompanied by the installation information.
(2) Yes.
(3) Users, since it says there is no warranty for this free software.
- LGPL-3
(1) No, but users can convey a copy of the modified version under this License.
(2) Yes.
(3) Users, it mentioned that be liable for your own damage.
- CC-0
(1) Yes, everyone can do anything.
(2) Yes.
(3) Users are liable for that.
3. **Assume that you are in the process of making a package for your own graduate work. Describe considerations that come into play in deciding on a license. In case you are not quite at that stage in your graduate studies yet, come up with a likely scenario. Describe it and discuss.**

I think the purpose of the package largely and the dependencies that I will use from others' packages determine which license I should use. 
For example, if I used a lot of functions from others' packages, it would be better if I can follow their licence, make things consisitent could avoid some unexpected problems.
And if I want other to add more new features without causing conflicts with my current package, I think it would be better to use GPL-3 license, such that I am aware of what have they done to my work, and once some functions in the package doesn't not workm they are responsible for that.
