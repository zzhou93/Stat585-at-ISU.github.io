---
title: "More on Reproducibility..."
author: "Min Zhang"
topic: "05"
layout: post
root: ../../../
---

## Background:


In 2009 one of the associate editors of Biostatistics, Roger Peng, outlined a new policy of [reproducibility](https://doi.org/10.1093/biostatistics/kxp014) for the journal. 

This triggered a response from one of the other associated editors, Niels Keiding, and subsequently a large part of volume 11, issue 3 of Biostatistics was dedicated to a discussion of issues of redproducibility. 

## Prompt:

Read through 

- Roger Peng's [initial editorial](https://doi.org/10.1093/biostatistics/kxp014), 

- [Keiding's response](https://doi.org/10.1093/biostatistics/kxq033),

- its five [commentaries](https://academic.oup.com/biostatistics/issue/11/3),  

- Roger Peng's [response to Keiding](https://doi.org/10.1093/biostatistics/kxq032)

- and finally, Keiding's [response to the commentaries](https://doi.org/10.1093/biostatistics/kxq034)

Don't worry about the number of papers listed - these papers are all very short and easy reads. 


Write a blog post addressing the questions: 

1. **Answer each of the following questions with at least 2-3 sentences.**

    1. **Summarize Roger Peng's outline for reproducibility in** *Biostatistics*. 
    
    Roger Peng’s idea about reproducibility in Biostatistics is that one candidate should be “**reproducible research**” for minimum standard. The standard involves three **criteria** when evaluating the reproducibility: (a) data, (b) code, (c) successful execution and matching results. In order to satisfy these criteria, necessary **materials** are needed, so that the published results can be verified, and alternative analyses can be conducted. 
    
    2. **What are Keiding's main criticisms of the proposal?**. 
    
    However, Keiding believes that the quest for reproducibility may lead us further into the inbreeding of science, ignorance of the complicated context. He claims that meaningful research should be identifying substantive problems and developing new methodologies, rather than checking the statistical analysis and the correctness of calculations.

    
    3. **Which point in the commentaries speaks to you the most? Why?**
    
    I am more in favor of the commentary by Norman Breslow. Admittedly, reproducibility is critically important. However, it might be more productive to point such importance out to the authors (e.g. higher possibility of citation), instead of making the criteria as the minimum standards for publication. 
    
    4. **How does Keiding respond to the commentary you picked. What are his main points in his response?**
    
    Keiding responded to Breslow’s commentary of reproducible research having higher impact as credible. But he also pointed out that we should always be aware of the risk associated with reproducing other people’s work: alienating the methodologies from the real problems. The main ideas in his response lie in two points: (a) we need a stronger focus on problem-driven research, instead of method-driven research. (b) we need close collaboration between the statisticians and the substantive researchers, as it leads to deeper insight into the substantive context. 
    
2. **Describe your experience with a data intensive (collaborative) project. What are the most prominent issues with ensuring reproducibility of research results (focus on data related aspects)? What would you do differently if you could go back in time?**

A research project of mine about antimicrobial resistance is based upon a large longitudinal dataset. The most prominent issue related with reproducibility is that I don’t have permission to make the raw data public. The most I can/should do is to describe the dataset as detailed as possible, in the main text focusing on the most important summary information, and in the supplementary materials focusing on some less important yet necessary statistics. I have all of my computer code uploaded to a GitHub repository, with the most basic data cleaning code, the statistical model code, the model implementation code, and the result extraction/presentation code. In my case, I only satisfy one criterion proposed by Dr. Peng. I personally think I have reached the bar of reproducible research within my limitation. As for improvement, maybe more comments could be added to the current version to make it more readable and understandable. 
