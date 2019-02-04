---
title: "#3: Ethics and Reproducibility"
author: "Steve Harms"
topic: "03"
layout: post
root: ../../../
---
1. **Pick one of the papers Retraction Watch features on their website and describe what went wrong**. 

I will discuss the multiple retractions (183 and counting!) of Yoshitaka Fujii from the University of Tokyo, who is currently #1 on RetractionWatch's leaderboard. Dr. Fujii fabricated large amounts of data in order to get published in anesthesiology journals. Not only did he make up data, he purposely did not name the various ethics committees, hospitals, and institutions whom would have been responsible for signing off on these experiments and studies. He claimed the data came from previous (unnamed) positions, and forged co-author signatures and approval in order to cover for his own deliberate dishonesty. After an independent investigation was unable to account for the people, animals, hospitals and other data Dr. Fujii claimed to have used in his studies, the fabrication was obvious. The resulting retractions were almost hard to believe.

Dr. Fujii's gross misconduct was not just a violation of the rules of ethics in science. The consequences were not just related to Dr. Fujii's personal academic career and professorship. Many of the studies used public funds (which now cannot be accounted for), and he received public grant money for speaking engagements related to his fabricated research. Moreover, anesthesiology is quite literally a life and death field, and if any researchers used Dr. Fujii's results for their own work may have endagered animals and people who they used in their studies. The prospect of people dying due to fake data should be more troubling than one person risking the destruction of their own reputation and career.

[Another note]: It looks like most of the retracted Statistics papers were removed due to plagiarism/math errors, which just means we need to look a little bit harder during peer review in our field. The only two that appear under "falsification of data" for the Statistics category were not even produced by researchers in statistics departments.

2. **After reading the paper by Sandve et al. describe which rule you are most likely to follow and why, and which rule you find the hardest to follow and will likely not follow in your future projects.**

Ideally all of the rules should be followed, but there are a few that should be automatic. Recording all results both final and intermediate (Rules 5,7, and 10) and how you got them (Rules 1, 6, and 10) should be easy to follow. Just make sure you set and record your random seed, save all versions of all scripts (version control!) and save every piece of data that you produce. Not only does this help reproduciblity, but it also allows peer reviewers (and possibly yourself!) to investigate irregularities in data/code that could lead to future investigations. This is the bare minimum of ethical scientific conduct and requires nothing beyond good organization.

If there is a rule that might be difficult to follow, especially in statistics, I would suggest Rules #2 and/or #3. When we collect large amounts of messy data from outside and possibly disparate sources, it is not always straightforward to clean the data into a format that is useful for analysis. We might be unable to apply simple commands in R to give us a neat dataframe, hence we may need to manually copy/paste/merge our data if it's particularly bad. While this would violate Rule #2, as long as we're able to save the original data AND the exact methods we used to clean the data, we could still have some degree of reproducibility (although it's not ideal). For Rule #3, we may not have public access to the code for external programs, and thus if such a program were updated in the interim we may not be able to reproduce our results under new conditions. In an ideal world we would be able to use simple datasets and simple programs, but that is often not the case in data-heavy fields.

