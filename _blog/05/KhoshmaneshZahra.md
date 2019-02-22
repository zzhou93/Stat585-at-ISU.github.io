---
title: "More on Reproducibility..."
author: "Zahra Khoshmanesh"
topic: "05"
layout: post
root: ../../../
---


1. **Answer each of the following questions with at least 2-3 sentences.**

    1. **Summarize Roger Peng's outline for reproducibility in** *Biostatistics*. 
    
        Roger Peng as editor of Biostatistics journal proposed a minimal standard framework for replication. 
        In his reproducibilty  framework, there are three important elements for reproducible works:
          data : the dataset which results comes from
          code : the computer program used for extracting the result from data
          reproducible : a document explaining the code to use data step by step and reach the results.
            
    2. **What are Keiding's main criticisms of the proposal?**. 
    
    Keiding beleives that the context behind the data is very important and mostly in statistic dield statistician collaborate 
    with subject matter fields to undrestand the context better and after that inference the result from data since there are
    many confounding variables and sampling limitations that limit the generalization of data and method.He thinks without 
    knonwing the context publishing the data and code mislead the researchers.
    
    3. **Which point in the commentaries speaks to you the most? Why?**
    
        the point commented by Steven N. Goodman is my favoriate commentry among commentries. He mentions a very important issue in 
        reproducibility in statistics that is the importance of knowing the domain and context than checking the arithmatic code 
        although be able to vaeify the numbers and code results is part of reproducibility.
        
    4. **How does Keiding respond to the commentary you picked. What are his main points in his response?**
    
     Kieding confirms his commentry and give some examples in research in the field of statistic  and biostatistical journals that 
     researchers do not know the substantive context and the domain very well and he bring this issue that how they can reach to a
     result without knowing the underlying knowledge.
     
    
2. **Describe your experience with a data intensive (collaborative) project. What are the most prominent issues with ensuring reproducibility of research results (focus on data related aspects)? What would you do differently if you could go back in time?**

    In my recent project I had to work with different safety critical systems having dataset in same shape and columns
    with totally different context and domain knowledge. My python code was same across the whole projects but inferring the 
    result was different across the case studies. Even I published my code , I had to explain the result step by step in every
    case study.
    If I could go back in time, I would publish a very good document explaining the whole data and resulty step by step. 
    I would probably choose jupyter notebook or R markdown for this purpose.
