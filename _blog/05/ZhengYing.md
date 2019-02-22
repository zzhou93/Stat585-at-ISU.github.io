---
title: "More on Reproducibility..."
author: "Ying Zheng"
topic: "05"
layout: post
root: ../../../
---



1. **Answer each of the following questions with at least 2-3 sentences.**

    1. **Summarize Roger Peng's outline for reproducibility in** *Biostatistics*. 
    
    Roger Peng introduced three dimensions of reproducibility: data, code and reproducible. The data and corresponding codes for the principal results need to be publicly avaliale. If the AER can successfully execute the code on the data and reproduce the results claimed in the paper, then the work is reproducible.

    2. **What are Keiding's main criticisms of the proposal?**. 
    
    Keiding's main criticisms is that a good work should focus on substantive context rather than the data and code. He prefer "problem-driven" to "method-driven".
    
    3. **Which point in the commentaries speaks to you the most? Why?**
    
    Cox and Donnelly’s commentary is interesing to me. They said providing the full data was not primarily to encourage repetition of the analyses, but encourage other researchers to  investigate new questions. So the "proposals for Biostatistics are to be welcomed even though their name and objectives are misformulated."
    
    4. **How does Keiding respond to the commentary you picked. What are his main points in his response?**
    
    Keiding respond to the Cox and Donnelly’s commentary with fully agreement. His main point in this response is we need a stronger focus on problem-driven research rather than method-driven analysis; and also, statistician and the substantive researchers should closely contact with each other.

    
2. **Describe your experience with a data intensive (collaborative) project. What are the most prominent issues with ensuring reproducibility of research results (focus on data related aspects)? What would you do differently if you could go back in time?**

    In some of my previous projects, I shared pipelines developed by me with other students. But the same code on same data did not get the expected same results, or even fail to run. The main reason is the different version of softwares. As bioinformatcis software developed so rapidly, they may change the format of the output or even change the command. It is important to record the version of every software invloved in the pipeline. Sometime, we can use Docker to make a uniform environment to avoid this.






