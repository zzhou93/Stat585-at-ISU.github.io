---
title: "Blog Post 5: More on Reproducibility"
author: "Kellie McClernon"
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
    2. **What are Keiding's main criticisms of the proposal?**. 
    3. **Which point in the commentaries speaks to you the most? Why?**
    4. **How does Keiding respond to the commentary you picked. What are his main points in his response?**  

Roger Peng's outline for reproducibility in *Biostatistics* focuses on the minimum requirement for recomputing the statistical output of a submitted article. The author is expected to provide the R code used to create all the models, results, and graphs, along with the data input used in the code. Peng's suggestion limits itself to a "master" file of code and data. Keiding criticizes this proposal since it seems to suggest that reproducibility merely means checking someone's arithmetic. Also, the proposal does not address the complexity of choices made by (substantive) scientists and statisticans in the collection of data and the final analysis. It appears that Keiding is concerned with the use and interpretation of these public-made data sets isolated from their original intent and meaning.  

The point Cox and Donnelly make in their commentary that data sets should be made available to the public in order not for the same analysis to be repeated but rather so that new questions and analyses can be formed from the data speaks to me the most. To me, this is the most natural process of scientific discovery, using others analysis and data as a springboard for discussion and the beginnings of a blueprint for data collection. The goal is still to expand upon what has already been done. Keiding responds to Cox and Donnelly by agreeing and requoting their conclusion. All agree that scientific reproducibility goes beyond computational reproducibility. The true objective of reproducibility in science historically was to verify the truthfulness of scientific conclusions, not the accuracy of numbers. Verifying scientific conclusions though relies on an understanding of the problem at hand and its inherent complexities, but when subject knowledge is brought to bear on an analysis the conclusions are much richer. Hence, Keiding emphasizes over and over his preference for statistical advances driven by a practical need in the analysis of data from a collaboration with a substantive scientist.  

2. **Describe your experience with a data intensive (collaborative) project. What are the most prominent issues with ensuring reproducibility of research results (focus on data related aspects)? What would you do differently if you could go back in time?**  

For a class project, we were building a predictive model on housing data. We went through several iterations of creating new variables. Each team member was working essentially with a different data file since we were not successful at sharing and starting with the most current version. Therefore, we were not able to get similar performance on our models since the underlying data was different. This made it difficult to reach a consensus on which models had the best accuracy. As we scrambled to validate the other members' model performance, we were not advancing our modeling techniques.  

In the future, I would use more literate programming so that I know how and why each new variable was created. Then I would share the data and results in real time so each member could work on the most update version. Given the time needed to run each model, I would cache key results and figures to reduce the time needed for other members to recreate my results if desired.
