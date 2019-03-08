---
title: "All the legal stuff"
author: "Gulzina Kuttubekova"
root: ../../../
layout: post
topic: '06'
---

 Here, we want to focus on the use of licenses in R packages. There are several important aspects to consider when choosing a license for your work. Three of the main questions to answer are:

- Are you and your collaborators fine with other people modifying your work and then sharing the modified work?

- Are you and your collaborators fine with other people making a profit from those derivations?

- Who is responsible if your software does not do what it promises to do?

### Questions: 
1. Under what license does R operate?

 - It mainly operates under GPL-2 and GPL-3 licenses. There are other additional licenses like MIT, etc., that can be found on from the link: https://www.r-project.org/Licenses/ Any writer/owner of the package may choose any other license like LGPL-3, MIT and etc., when s/he decides to release her/his package. 

2. Answer the three questions listed above for the licenses: MIT, GPL-3, LGPL-3, and CC-0. Note that some of the questions might not be answered with a simple yes/no. In that case, go into more detail, but do not just copy the terms of the license.

#### MIT:
 - Yes, I and other collaborators are fine with other people modifying  our work and sharing the modified work. It stated in the description of this license that, a third party can modify/distribute the code within a package.
 
 - Yes, our group should be fine with it, too. It is also stated that a third party can use this package for commercial use/making profit.
 
 - This license clearly states that the product comes with NO warranty, so no one is responsible if the package isn’t working. However, the person, whose email address is given in the DESCRIPTION file, can be contacted regarding some questions.
 
#### GPL-3:
 - Yes, I and other collaborators are fine with other people modifying  our work and sharing the modified work. It stated in the description of this license that, a third party can modify/distribute the code within a package. However, a third party should state the changes, make sure to include the original software code, use the same license with a copy of the original copyright statement.
 
 - Yes, our group should be fine with it, too. It is also stated that a third party can use this package for commercial use/making profit.
 
 - This license also states that the software product comes with NO warranty.
 
#### LGPL-3:
 - No, we are not fine with other people modifying the original software code. Contents can be copied and then modified/distributed in a way similar to GPL-3 license conditions: a third party has to state changes, make sure to include the original software code, use the same license with a copy of the original copyright statement.
 - No, we are not fine with people making a profit of the original software product without any legal notice. Only if a third party uses small portions like functions, under particular conditions and compromises with the authors, they can make a profit of it.
 - There is NO warranty as well. So users are responsible for any crash of the software product.
 
#### CC-0:
 - Yes, we are fine with any sort of modification/distribution of software package.
 - Yes, we are fine with any sort of commercial use/making profit, since we “throw” the software to the public domain.
 - No, there is NO warranty coming along. So no one is responsible for any crash in the software.


3. Assume that you are in the process of making a package for your own graduate work. Describe considerations that come into play in deciding on a license. In case you are not quite at that stage in your graduate studies yet, come up with a likely scenario. Describe it and discuss.

- I am already up to finish my CC thesis work by this summer. And I was thinking about developing a package that automates some algorithms I developed for CC project. Honestly, I was not aware of these details such as choosing a license for the package, if in the future I would like to make it publicly available. Personally, I think, I will be okay with people making corrections, proposing some modifications to my code. However, I feel uncomfortable when credits are not properly given to me, even in the small collaborative group work. Taking into account all these, I would likely choose LGPL-3 license, to make sure I am aware of any modifications/distributions to the code in the future.
















