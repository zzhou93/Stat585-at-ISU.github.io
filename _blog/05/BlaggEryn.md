---
title: "More on Reproducibility..."
author: "Eryn Blagg"
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

Peng is proposing that in order to improve reproducibility in the Biostatistics paper community there needs to be a new standard of what author who want to publish must have. Biostatistics, the magizine is required autors meet a subset three different criteria when evaluating the reproducibility of an article: Data, Code and Reproducible. The Data of an aritcle will now be required to be made available on the journal's Web site. For code, any computer code should be provided. Finally for repoducible, "an article is designated as reproducible if the AER succeeds in executing the code on the data provided and produces results matching those that the authors claim are reproducible". Peng is proposing that an author should have these things when publishing an article. 
    
    2. **What are Keiding's main criticisms of the proposal?**. 

Overall, the main criticism that Keiding states is that although these are desired steps to have in a paper, there is usually much more to “research” than the statistical analysis, and there is much more to the statistical analysis than the correctness of calculations in Biostatisical papers. With that, there are three subpoints Keiding makes. The first is, problem-driven biostatistics involes collaboration that often has many necessitated resources in data. The second is, the actual mechanical number crunching of the finally developed master data set is a minor part of the totality of the statistical analysis, and not as important as the steps to get there. His final point is in real alysis it is important to make sense more broadly than checking the calculations of data.  There at least has to be sufficient information to make it realistic for another interdisciplinary group of researchers to understand the substantive context and the strengths and weaknesses of the data. 

    
    3. **Which point in the commentaries speaks to you the most? Why?**
T
he commentary that speaks the most to be is the commentary by Steven N. Goodman. I think although I do not 100% agree with him, he makes a point that although it is important to have some guidelines when it comes to statistical code, often time scientist and statistitians dont really have that much communication about all of the background that goes into a final model, and while it is important for statisticians to understand that, I can see why he thinks maybe its not as important to understand all the steps to get to that model, as what the model is. 
 
    
    4. **How does Keiding respond to the commentary you picked. What are his main points in his response?**
Keiding responds to Good man by saying that there are  plenty of papers in biostatistical journals where the authors do not have full understanding of tthe substantive details in the examples they are writing and talking about, and many editors put too little importance on this issue. Keiding states that is a major problem, pointing out how can you understand a solution without the underlying knowledge. 
    
2. **Describe your experience with a data intensive (collaborative) project. What are the most prominent issues with ensuring reproducibility of research results (focus on data related aspects)? What would you do differently if you could go back in time?**

In undergrad, I did a data project on baseball players and errors during games. There is a lot of data on that. One of the difficulties that may go into reproducibility is how missing data is delt with. Since I didnt collect the data I didnt know why data points are missing, and that effects the model that you do. If someone was trying to reproduce my results, these missing points may cause problems. I think that if I did it again, I would do more research on why the data points are missing and not just ignore them as I did. 

## Instructions:

Update your forked version of the 'blog-2019' repository (or re-fork it after deleting your previous repo).

Save a **copy** of this file, replacing "Lastname" and "Firstname" with your own and *leave the original unedited*.

In **your copy**, replace the `title:` and `author:` fields in the YAML above, while leaving the remaining fields intact. Remove the background and the instructions sections and write your blog post! 

Once you are done, **create a pull request** to upload your changes to the original repository. Do not commit the compiled HTML file to the repository.
