---
title: "7: All that legal stuff..."
author: "Miranda Tilton"
topic: "07"
layout: post
root: ../../../
---

1. **Under what license does R operate?**

R operates under the GPL-3 license.

2. **Answer the three questions listed above for the licenses: MIT, GPL-3,  LGPL-3, and CC-0. Note that some of the questions might not be answered with a simple yes/no. In that case, go into more detail, but do not just copy the terms of the license.**

**MIT:**

1. MIT allows others to freely distribute your code as long as it is also distributed with the license.

2. MIT allows others to make a profit off of derivations of your code.

3. MIT does not hold you liable if your software does not do what it promises to do.

**GPL-3:**

1. GPL-3 allows others to distribute your code so long as they include the license, copyright information, the source location/purpose and stated changes, and installation instructions.

2. GPL-3 allows others to make a profit off of derivations of your code.

3. GPL-3 does not hold you liable if your software does not do what it promises to do.

**LGPL-3:**

1. LGPL-3 is primarily for libraries. It allows others to distribute your code under the same restrictions as the GPL-3 (above), but derivatives must also be distributed under the LGPL-3 (excluding applications of the library).

2. LGPL-3 allows others to make a profit off of derivations of your code.

3. LGPL-3 does not hold you liable if your software does not do what it promises to do

**CC-0:**

1. CC-0 fully releases your code into the public domain. Others are free to distribute your code in whatever way they would like, but they cannot trademark the derivations or use any patent claims.

2. CC-0 allows others to make a profit off of derivations of your code.

3. CC-0 does not hold you liable if your software does not do what it promises to do

3. **Assume that you are in the process of making a package for your own graduate work. Describe considerations that come into play in deciding on a license. In case you are not quite at that stage in your graduate studies yet, come up with a likely scenario. Describe it and discuss.**

Susan VanderPlas and I will likely be compiling our CNN code into a package that makes training and evaluating a CNN a little more user-friendly for beginners and for our future modeling. Since most of our code will be applications of the code already present in R's keras package, I imagine we'll have to consider the license that the package uses when writing our derivations. We'll also want to consider liability, as we want to minimize errors but are imperfect humans.
