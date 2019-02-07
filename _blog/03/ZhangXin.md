---
title: "Ethics and Reproducibility..."
author: "Xin Zhang"
topic: "03"
layout: post
root: ../../../
---

## Background:

## Prompt:


In May 2015 Science retracted - without consent of the lead author - a paper on  how canvassers can sway people's opinions about gay marriage, 
see also: http://www.sciencemag.org/news/2015/05/science-retracts-gay-marriage-paper-without-agreement-lead-author-lacour
The Science Editor-in-Chief cited as reasons for the retraction that the original survey data was not made available for independent reproduction of results, that survey incentives were misrepresented and that statements made about sponsorships turned out to be incorrect.<br>
The investigation resulting in the retraction was triggered by two  Berkeley grad students who attempted to replicate the study and discovered that the data must have been faked.
 
[FiveThirtyEight](https://fivethirtyeight.com/features/how-two-grad-students-uncovered-michael-lacour-fraud-and-a-way-to-change-opinions-on-transgender-rights/) has published an article with more details on the two Berkeley students' work.

Malicious changes to the data such Thailandas in the LaCour case are hard to prevent, but more rigorous checks should be built into the scientific publishing system. All too often papers have to be retracted for unintended reasons. [Retraction Watch](https://retractionwatch.com/) is a data base that keeps track of retracted papers (see the related [Science magazine](https://www.sciencemag.org/news/2018/10/what-massive-database-retracted-papers-reveals-about-science-publishing-s-death-penalty) publication). 

Read the paper [Ten Simple Rules for Reproducible Computational Research](https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1003285) by Sandve et al.


Write a blog post addressing the questions: 

1. **Pick one of the papers Retraction Watch features on their website and describe what went wrong**. 

I choose the news, "Food packaging journal to retract paper by researchers in Thailand" (https://retractionwatch.com/2019/02/01/food-packaging-journal-to-retract-paper-by-researchers-in-thailand/). In this news, it reports that the paper, “Production, characterization and controlled release studies of biodegradable polymer microcapsules incorporating neem seed oil by spray drying”, was retracted because of "self-plagiarism".

In this news, it is said that several sections in the retracted paper are the same as the paragraphes in a recently published paper, from the same authors. The correponding author reponsed that this was because that he didnt check the final manuscript before the paper was published. 

Hence, for our further research, we'd better not to just copy the paragraphes from our previous work when we prepare our new article.

2. **After reading the paper by Sandve et al. describe which rule you are most likely to follow and why, and which rule you find the hardest to follow and will likely not follow in your future projects.**

I'm most likely to follow:
Rule 1: For Every Result, Keep Track of How It Was Produced. This could be easily done by keeping the code.
Rule 6: For Analyses That Include Randomness, Note Underlying Random Seeds. I will set the random seed in my code and notify it in my report.
Rule 10: Provide Public Access to Scripts, Runs, and Results. It can be done by updating them to github and making an open access.


I think these rules are difficult to follow:
Rule 5: Record All Intermediate Results, When Possible in Standardized Formats. Keeping the intermediate results and making them into standardized formats might be memory-cost and time-consuming.
Rule 7: Always Store Raw Data behind Plots is hardest to follow. Becasue I usually keep the code for generating the plots but it will be memory-cost to store every dataset.
