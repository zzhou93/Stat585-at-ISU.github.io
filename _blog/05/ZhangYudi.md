---
title: "More on Reproducibility..."
author: "Firstname Lastname"
topic: "05"
layout: post
root: ../../../
---

Write a blog post addressing the questions: 

1. **Answer each of the following questions with at least 2-3 sentences.**

    1. **Summarize Roger Peng's outline for reproducibility in** *Biostatistics*. 
    Peng pointed out that many scientific investigations can not be reproduced. Therefore, he give three rules to allow reproducibility, i.e. data and code should be available, and AER can execute the code on the data and produces matched results. Then he gave the instructions to the authors and an example to demonstrate his argument.
    
    2. **What are Keiding's main criticisms of the proposal?**. 
    Keiding's main criticisms mainly focused on the meaning of reproducibility, there are more important things such as "problem-driven" research taking novel statistical methods for statisticans to do, instead of reanalysising. Such reproducibility would lead us focus on the conclusions of data sets, but the real context things that we should pay attention has been forgotten.
    
    3. **Which point in the commentaries speaks to you the most? Why?**
    I like Goodman's commentaries. He thinks ask for the "statement by the authors of whether they will share their protocol, data, and statistical code, and if so, how and under what terms" is better than just trying to reproduce, which allows the researchers keep their research consistent and also allow some statistical coding practices.
    
    4. **How does Keiding respond to the commentary you picked. What are his main points in his response?**
    Keiding is persuaded by Goodman's point and mentioned that "better documentation of the computations will enhance the quality of statistical refereeing in subject-matter journals". So I think he partially denied his opinions on the code part before and Goodman's opinions are quite reasonable.
    
    
    
2. **Describe your experience with a data intensive (collaborative) project. What are the most prominent issues with ensuring reproducibility of research results (focus on data related aspects)? What would you do differently if you could go back in time?**
When I first started doing research with Karin, I was trying to mimic her code of reading fastq file and created my own version of reading data from fasta file, but I failed a lot of times due to several reasons, such as confounded the format of fastq anf fasta file, and read in error due to fail to malloc space. I would read through her code and understang everything in it first and then try to read the fastq file first, then write my own function to write reading fasta file.
