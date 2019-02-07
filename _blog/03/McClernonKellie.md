---
title: "Blog Post 3: Ethics and Reproducibility"
author: "Kellie McClernon"
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

Malicious changes to the data such as in the LaCour case are hard to prevent, but more rigorous checks should be built into the scientific publishing system. All too often papers have to be retracted for unintended reasons. [Retraction Watch](https://retractionwatch.com/) is a data base that keeps track of retracted papers (see the related [Science magazine](https://www.sciencemag.org/news/2018/10/what-massive-database-retracted-papers-reveals-about-science-publishing-s-death-penalty) publication). 

Read the paper [Ten Simple Rules for Reproducible Computational Research](https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1003285) by Sandve et al.


Write a blog post addressing the questions: 

1. **Pick one of the papers Retraction Watch features on their website and describe what went wrong**. 

On the website *Retraction Watch*, they featured the paper "Short-term and long-term effects of a loading dose of atorvastatin before percutaneous coronary intervention on major adverse cardiovascular events in patients with acute coronary syndrome: a meta-analysis of 13 randomized controlled trials" originally published in the *European Heart Journal*. Unfortunately, what went wrong is that the criteria for inclusion in the analysis, so painstakingly detailed in the title of the article, was not met for most of the studies used. The meta-data not only included one set of data twice, but also some of the data was not even from controlled trials. If only that was all... However, the article originally was questioned because one of the studies used in the analysis was known to have excluded patients who planned on having percutaneous coronary intervention (PCI) performed. In summary, the data collected was **not** on PCI patients in clinical trials who received atorvastatin. The published findings consequently could not answer the scientific questions of interest about PCI patients who had recieved atorvastatin.

2. **After reading the paper by Sandve et al. describe which rule you are most likely to follow and why, and which rule you find the hardest to follow and will likely not follow in your future projects.**  

I am most likely to follow the rules of avoiding manual data manipulation and keeping track of how results were produced. In my own work and consultations, I already prefer to keep all analyses in one script file with commented notes. Each analysis script contains any data manipulations, graphics, and modeling procedures used. This avoids altering the original data set directly and allows me to quickly alter or duplicate analyses and graphical output. It is especially useful for graphical output, since I can see what data was used for the graph and can add legends or new views easily.  

Currently, I find version controlling scripts the hardest to follow. I usually end up with only one script at the end of the analysis. Often I end up deleting out rejected analyses for clarity rather than storing the intermediate scripts. Version control is difficult without an easy to use system that has been well-adopted. I hope to learn more about tools for versioning control and adopting one for future projects. However, at the end of the day, the hardest part will be retraining myself.
