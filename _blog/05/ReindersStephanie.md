---
title: "Blog 5"
author: "Stephanie Reinders"
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
    
    Peng explains the need for reproducable research. He proposes 3 criteria that the Biostatistics journal could use to evaluate the reproducability of research submitted to the journal for publication. The 3 criteria are (1) data used in the research should be made available to others (2) computer code, software, and instructions should also be made available, and (3) the Associate Editor for reproducibility should be able to execute the code and get the same results.  
    
    2. **What are Keiding's main criticisms of the proposal?**. 
    
    Keiding argues that the field has the tendency to overuse certain datasets. He also argues that scientists might use datasets without taking the time to properly understand the data. 
    
    3. **Which point in the commentaries speaks to you the most? Why?**
    
    I appreciated that Donoho mentioned that because errors can so easily crop up in scripts, it is important to make all of your code available so that others can see precisely how you calculated your results. I worry that there might be some small error in my research scripts that I have missed.
    
    4. **How does Keiding respond to the commentary you picked. What are his main points in his response?**
    
    Keiding's response to Donoho's commentary is that Donoho's proposal of increased documentation does not address the issues that Keiding raised in his first response to Peng's paper. Keiding does however say that Donoho's efforts are "highly commendable and long overdue."
    
    
2. **Describe your experience with a data intensive (collaborative) project. What are the most prominent issues with ensuring reproducibility of research results (focus on data related aspects)? What would you do differently if you could go back in time?**

In our steganlysis research, Li Lin and I have both, individually, performed the some of the same experiments, using the same machine learning scripts, on the same data. While our results were similar, they weren't actually the same because neither of us had kept track of the seeds we used for the pseudo-random number generators in the code. If I could go back in time, I would record the seeds and ask Li to do the same. 




