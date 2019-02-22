---
title: "Blog 5 - More on Reproducibility..."
author: "Earl Hur"
layout: post
root: ../../../
---

1. **Answer each of the following questions with at least 2-3 sentences.**

    1. **Summarize Roger Peng's outline for reproducibility in** *Biostatistics*.
    
    Peng's outline is that data need to be available in the journal's website and code to be provided. In reproducing the result, reasonable bound of numerical tolerance need to be considered.
    
    2. **What are Keiding's main criticisms of the proposal?**.
    
    Keiding's critism was that reproducing may ignore the context. In his view, research is not just the numerical results from statistical analysis. He argues that we should focus on the substansive context instead of just numerical results.
    
    3. **Which point in the commentaries speaks to you the most? Why?**
    
    Norman E. Breslow's commentaries speaks to me the most. As he mentioned, the sample code and test datset seem to be enough for readers to understand the methods and the results. Instead of having the full data sets and code available to reproduce, having authors to explain the procedure and the benefits from the result would be enough.
    
    4. **How does Keiding respond to the commentary you picked. What are his main points in his response?**
    
    Keiding's first response to the commentary was that the reproducible research will have higher impact. However, he also awares the importance or reproducibility and was actually persuaded by Goodman's point that "better documentation of the computations will enhance the quality of statistical refereeing in subject-matter journals."
    
2. **Describe your experience with a data intensive (collaborative) project. What are the most prominent issues with ensuring reproducibility of research results (focus on data related aspects)? What would you do differently if you could go back in time?**

    When I was a research assistant from the department of political science, my research professor and I worked with a terrorism dataset. This dataset is a panel data from 1970 to 2014 and there are tons of observations in the dataset as well. For our research purpose, I wanted to merge this dataset with other data, such as GDP, monthly rainfall or temperature by the name of countries. An issue that came out while merging these data was that the name of countries are all different from each data set. Moreover, there are countries that changed their name, suhc as Myanmar that was previously Burma. In order to deal with these names, Not knowing that there is *countrycode* package in r, I had to change the names manually so that all the data sets have the same country names. This would be an issue ensuring reproducibility. If I could go back in time, I would try to use this package so that I could save time to deal with the observation manually and also ensure the reproducibility. 
    
 
 
