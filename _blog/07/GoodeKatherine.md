---
title: "Blog 7: All that legal stuff..."
author: "Katherine Goode"
topic: "07"
layout: post
root: ../../../
---

The reading can be found [here](http://r-pkgs.had.co.nz/description.html).

### Question 1

**Under what license does R operate?**

R operates under the GNU General Public License. I found this by using the `license` function as suggested in the opening message in R.

> R is free software and comes with ABSOLUTELY NO WARRANTY.
> You are welcome to redistribute it under certain conditions.
> Type 'license()' or 'licence()' for distribution details.

Here is the output from `license`.


{% highlight r %}
license()
{% endhighlight %}



{% highlight text %}
## 
## This software is distributed under the terms of the GNU General
## Public License, either Version 2, June 1991 or Version 3, June 2007.
## The terms of version 2 of the license are in a file called COPYING
## which you should have received with
## this software and which can be displayed by RShowDoc("COPYING").
## Version 3 of the license can be displayed by RShowDoc("GPL-3").
## 
## Copies of both versions 2 and 3 of the license can be found
## at https://www.R-project.org/Licenses/.
## 
## A small number of files (the API header files listed in
## R_DOC_DIR/COPYRIGHTS) are distributed under the
## LESSER GNU GENERAL PUBLIC LICENSE, version 2.1 or later.
## This can be displayed by RShowDoc("LGPL-2.1"),
## or obtained at the URI given.
## Version 3 of the license can be displayed by RShowDoc("LGPL-3").
## 
## 'Share and Enjoy.'
{% endhighlight %}

### Question 2

**Answer the three questions listed above for the licenses: MIT, GPL-3,  LGPL-3, and CC-0. Note that some of the questions might not be answered with a simple yes/no. In that case, go into more detail, but do not just copy the terms of the license.**

The three questions to answer for each of the licenses are as follows.

1. Are you and your collaborators fine with other people modifying your work and then sharing the modified work?

2. Are you and your collaborators fine with other people making a profit from those derivations?

3. Who is responsible if your software does not do what it promises to do?

##### MIT

1. Yes. The MIT license allows modifying and sharing of the work as long as the license is distributed with the code.
2. Yes. The MIT license allows others to make a profit those derivations.
3. The author is not responsible with the MIT license.

##### GPL-3

1. Yes. The GPL-3 license allows modifying and sharing of the work as long as the changes are tracked in the source files.
2. Yes. The GPL-3 license allows others to make a profit those derivations.
3. It appears that the author may be held liable and charged for damages in some cases.

##### LGPL-3

1. Yes. The LGPL-3 license allows modifying and sharing of the work as long as the changes are described and licensed under LGPL.
2. Yes. The LGPL-3 license allows others to make a profit those derivations.
3. It appears that the author may be held liable and charged for damages in some cases.

##### CC-0

1. Yes. The LGPL-3 license allows modifying and sharing of the work.
2. Yes. The LGPL-3 license allows others to make a profit those derivations.
3. It appears that the author may be held liable and charged for damages in some cases.

### Question 3

**Assume that you are in the process of making a package for your own graduate work. Describe considerations that come into play in deciding on a license. In case you are not quite at that stage in your graduate studies yet, come up with a likely scenario. Describe it and discuss.**

I have been working on a package called ggResidpanel with a collaborator. When we were deciding which license to use, we were not really sure how to choose one. We did consider whether if it bothered us if individuals modified or shared our work, and we decided that was fine. We ended up going with the MIT license, because of it being a simple license and neither of us has had much experience with licenses yet. Additionally, we had no interest in being liable since we originally started the project for fun.

