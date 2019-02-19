---
title: "More on Reproducibility..."
author: "Oscar Aguilar"
topic: "05"
layout: post
root: ../../../
---

1. **Answer each of the following questions with at least 2-3 sentences.**

    1. **Summarize Roger Peng's outline for reproducibility in** *Biostatistics*. 
    Reproducibility in simple words means being able to validate someone else analysis. Peng's proposed reproducibility by       
    having the following components: 
    Data: the data used in the analysis. 
    Code: computer code and sowftare used to obtain the results.
    Reproducibility: an article designed to walk you through step by step how to obtain the results from the analysis.

    2. **What are Keiding's main criticisms of the proposal?**.
    The main criticism is that duplicating someone else result by running computer code is not enough (context is really 
    important). He pointed out that if we just focus on crunching number, we are missing the big picture (which I totally 
    agree!).
    
    3. **Which point in the commentaries speaks to you the most? Why?**
    Goodman's commentary spoke to me the most because he pointed out that Peng's original guidelines are meant to be     
    minimal. Asking researchers to publish their data, and computer code encourages better practices and transparency in     
    research.
    
    4. **How does Keiding respond to the commentary you picked. What are his main points in his response?**
    He says: "I am persuaded by Goodman's point that better documentation of the computations will enhance the quality of 
    statistical refereeing in subject-matter journals."

2. **Describe your experience with a data intensive (collaborative) project. What are the most prominent issues with ensuring reproducibility of research results (focus on data related aspects)? What would you do differently if you could go back in time?**

I don't have a lot experience with big collaborative projects in academia, but I do have some experience in the industry. Sometimes when practitioners develop a model and put it in production (the model will be run on a regular basis), documentation is very minimal. On the top of that, you may face with data issues. For example, if a model was built five years ago, back then they were capturing some specific information that may not be available now, which will break the model. I would encourage documentation and code readibility (include commments everywhere in your code!).

