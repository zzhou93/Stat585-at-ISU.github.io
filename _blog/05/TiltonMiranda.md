---
title: "5: More on Reproducibility..."
author: "Miranda Tilton"
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
    
    The main gist of reproducibility is that the data and code used to obtain results should be made available and the Associate Editor for reproducibility (AER) should be able to recreate the analysis. Further guidelines and an example are provided to show how these goals should be accomplished.
    
    2. **What are Keiding's main criticisms of the proposal?**. 
    
    The main criticism of the proposal is that there is more to research than statistical analysis and there is often more nuance than can easily be absorbed and recreated by people without expertise in the subject at hand. Additionally, such an intense focus on reproducibility, especially in the example regarding the private sector, espouses a lack of trust among certain disciplines and contexts.
    
    
    3. **Which point in the commentaries speaks to you the most? Why?**
    
    Steven N. Goodman's commentary spoke to me in that he pointed out the importance that Peng's original guidelines are meant to be minimal. Asking researchers to publish their data, or allowing them to say no, still encourages best practices and transparency, or at least requires a justification for not sharing. This allows a lot of flexibility and power of choice for the researchers while also providing some guidelines that will help maintain the integrity of research and data practices.
    
    4. **How does Keiding respond to the commentary you picked. What are his main points in his response?**
    
    Keiding simply says that he is "persuaded by Goodman's point that better documentation of the computations will enhance the quality of statistical refereeing in subject-matter journals," which I take to mean is a good sign that Goodman's response is well-formed and poignant.
    
2. **Describe your experience with a data intensive (collaborative) project. What are the most prominent issues with ensuring reproducibility of research results (focus on data related aspects)? What would you do differently if you could go back in time?**

In my research with Susan, I often was saving graphics by plotting them in R and then using R's GUI to save the image to PNG. One issue with this was that I could tweak the size/parameters of the image and even the data underlying it without then remembering which image was based on which information. Additionally, other data selections using point-and-click methods, like file/image selection, was not my best work. If I could go back, I would use the practices I have since learned to save plots and document image selection.
