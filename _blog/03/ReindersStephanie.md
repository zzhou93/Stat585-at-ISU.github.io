---
title: "Ethics and Reproducibility..."
author: "Stephanie Reinders"
topic: "03"
layout: post
root: ../../../
---

## Prompt:


In May 2015 Science retracted - without consent of the lead author - a paper on  how canvassers can sway people's opinions about gay marriage, 
see also: http://www.sciencemag.org/news/2015/05/science-retracts-gay-marriage-paper-without-agreement-lead-author-lacour
The Science Editor-in-Chief cited as reasons for the retraction that the original survey data was not made available for independent reproduction of results, that survey incentives were misrepresented and that statements made about sponsorships turned out to be incorrect.<br>
The investigation resulting in the retraction was triggered by two  Berkeley grad students who attempted to replicate the study and discovered that the data must have been faked.
 
[FiveThirtyEight](https://fivethirtyeight.com/features/how-two-grad-students-uncovered-michael-lacour-fraud-and-a-way-to-change-opinions-on-transgender-rights/) has published an article with more details on the two Berkeley students' work.

Malicious changes to the data such as in the LaCour case are hard to prevent, but more rigorous checks should be built into the scientific publishing system. All too often papers have to be retracted for unintended reasons. [Retraction Watch](https://retractionwatch.com/) is a data base that keeps track of retracted papers (see the related [Science magazine](https://www.sciencemag.org/news/2018/10/what-massive-database-retracted-papers-reveals-about-science-publishing-s-death-penalty) publication). 

Read the paper [Ten Simple Rules for Reproducible Computational Research](https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1003285) by Sandve et al.


Write a blog post addressing the questions: 

1. **Pick one of the papers Retraction Watch features on their website and describe what went wrong**. 

Retracted Paper: Wakefield, Andrew J., Simon H. Murch, Andrew Anthony, John Linnell, David M. Casson, Mohsin Malik, Mark Berelowitz et al. "RETRACTED: Ileal-lymphoid-nodular hyperplasia, non-specific colitis, and pervasive developmental disorder in children." (1998): 637-641.

The [Reaction Watch](http://retractiondatabase.org/RetractionSearch.aspx#?auth%3dWakefield%252c%2bAndrew%2bJ) database entry for Wakefield's paper lists the following reasons for retraction:

* Falsification/Fabrication of Data
* Investigation by Company/Institution
* Investigation by Third Party
* Lack of Approval from Company/Institution
* Lack of IRB/IACUC Approval
* Manipulation of Results
* Upgrade/Update of Prior Notice


2. **After reading the paper by Sandve et al. describe which rule you are most likely to follow and why, and which rule you find the hardest to follow and will likely not follow in your future projects.**

I started following "Rule 1: For Every Result, Keep Track of How It Was Produced" pretty much as soon as I started my steganalysis research. My motivation for doing so at the time was simply so that I would remember which Matlab script, inputs, and parameters I used to generate a specific set of results. Of course, now I realize that following this rule is important for reproducability as well.

I do not plan to follow "Rule 3: Archive the Exact Versions of All External Programs Used." Even if I archived the exact version of Matlab that I use, I couldn't make it available to other researchers to use because Matlab is not open source. 

