
---
title: "More on Reproducibility..."
author: "Firstname Lastname"
topic: "05"
layout: post
root: ../../../
---


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
    
    In Roger Peng's paper, three dimensions of reproducibility have been proposed:
       
       1) Data: The data should be accessible online and the auther should get the permission before distributing the data.
       
       2) Code: The auther should provide the information about the software and related codes.
       
       3) Reproducible: The Associate Editor for reproducibility will re-run the code and the work will be accepted if the re-run results is the same or almost the same as the results in the work.
    
    2. **What are Keiding's main criticisms of the proposal?**. 
    
    Keiding agrees that it is necessary to make sure that the statistical calculations is reproducible. But he thinks that there are some issues are more important than the correctness of calculations. He encourages statisticians to deeply understand 'the substantive contex' of the problem, instead of just repeating the analysis for old datasets. Kieding gives the following points:
    
       1) Reseach should be more inductive or “problem-driven,” which requires 'a collaboration between substantive scientists and statisticians has identified a substantive problem that requires new statistical methodology for its satisfactory solution.' This means that we'd better not focu on reproduing the analysis on old datasets.
       
       2) 'It is impractical to devise a reanalysis template that can capture this whole process.' Kieding thinks that it is necessary to deeply understand the underlying story before reaching the conclusions.
       
       3) It is important to make the 'interdisciplinary group of researchers to understand the substantive context and the strengths and weaknesses of the data.' 
       
       4) 'The original substantive collaborators make themselves available as partners in reanalyses, and some might put this as a condition for releasing the data.'
    
    3. **Which point in the commentaries speaks to you the most? Why?**
    
    I'm interested in the commentary given by D. R. Cox and Christl Donnelly. They suggests that instead of just reproducing the analyzing results, it would be more important to the formulate and investigate new problems with related subject-matter specialists. This would be more often if the data are fully provided.
    
    4. **How does Keiding respond to the commentary you picked. What are his main points in his response?**
    
    Keilding agrees with D. R. Cox and Christl Donnelly's opinion. He thinks it is encouraged to make data availible.
    
    
2. **Describe your experience with a data intensive (collaborative) project. What are the most prominent issues with ensuring reproducibility of research results (focus on data related aspects)? What would you do differently if you could go back in time?**

Last year, I had a team project on analyzing US precipitation data. We shared the code within the team but we found that we could not reach the same results. Then we took a very long time to exam the code and found that in the code there is a step to generate spatial block. However, the generation of the blocks is randomly conducted. And we didnt' specify a seed for it. This cause the differences. From then on, I would set a seed for the code associated with randomness.

