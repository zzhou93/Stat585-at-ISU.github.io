---
title: "More on Reproducibility..."
author: "Zerui Zhang"
topic: "05"
layout: post
root: ../../../
---

Write a blog post addressing the questions: 

1. **Answer each of the following questions with at least 2-3 sentences.**

    1. **Summarize Roger Peng's outline for reproducibility in** *Biostatistics*. 
    
    Peng pointed out the necessity to build a minimum standard for replication research to prevent the potential fraud and possible error. He proposed three different dimensions of reproducibility, including *Data*, *Code*, and *Reproducible* which should be met at least partially. He gave the instructions of satisfying the "reproducible" criterion which had the highest standard, and gave an example to show how the validation process worked.
    
    2. **What are Keiding's main criticisms of the proposal?**. 
    
    Keiding mainly argued that there is much more to novel research and sustantive problems than the correctness of calculations and reproduction. Some mandatory requirements for the real data and code to reproduce the same results ridiculed authors' profession, and the published data might help little with "alternative analyses" since the substantive context of them may be ambiguous according to different understanding. We should focus more on "problem-drive" research.
    
    
    3. **Which point in the commentaries speaks to you the most? Why?**
    
    I like Donoho's comments for his point that "Computational reproducibility is not an afterthough - it is something that must be designed into a project from the beginning". This helps researchers organize their files and work results better and develop a clear pathway of thoughts to present the stories in papers.
    
    4. **How does Keiding respond to the commentary you picked. What are his main points in his response?**
    
    Keiding was concerned that Donoho's detailed framework might leave little space for imaganation, which is essential for novel research. Donoho did not explain clearly that how a good documentation could benefit interdisciplinary collaborative groups and substantive context to help them create new things.
    

2. **Describe your experience with a data intensive (collaborative) project. What are the most prominent issues with ensuring reproducibility of research results (focus on data related aspects)? What would you do differently if you could go back in time?**

    Last summer, I was trying to do simulations using a large dataset which had billions of numbers. I understood the mechanism and wrote own functions to carry it out. However, it turned out to be very inefficient: each round of simulation cost about one hour and the waiting time was tedious. Then one time I read the code from my professor and found he transformed the dataset at first and then used some matrix techniques to solve the problem in a tidy and efficient way. So I think reproducibility could not only benefit us on research thoughts but a good way to learn techniques and experience.
