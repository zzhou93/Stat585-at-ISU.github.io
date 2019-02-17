---
title: "More on Reproducibility..."
author: "Joe Zemmels"
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
    
    An issue that Peng describes at the beginning of the article is that many scientific investigations simply cannot be fully replicated due to a lack of time or resources. To bridge the gap between nothing and replicability, Peng discusses a set of criteria that Biostatistics uses to determine whether the results of an article are reproducible. Peng outlines three different criteria to evaluate the reproducibility of the article:
    
    - Data: Making the data available on the journal's website.
    - Code: Including any code or instructions that were used to compute the results published.
    - Reproducible: If the Associate Editor for reproducibility can reproduce the results discussed in the paper with the data and code/instructions available, then the article will be designated as "reproducible".
    
    2. **What are Keiding's main criticisms of the proposal?**.
    
    One of Keiding's criticisms of Peng's proposal is in Peng's encouragement to use the data submitted along with an article to perform "alternative analysis". As Keiding puts it, removing the data from their substantive context can oftem lead to poorly informed reanalyses. Rather than using old data to demonstrate the validity of some new improvement/generalization of an existing model (the "method-driven" approach), Keiding asserts that journals should encourage and promote research that is more "problem-driven". As he describes it, "problem-driven" research involves new statistical methods that were born out of a specific, substantive problem whereas "method-driven" research leads to methods cooked-up in a vacuum and justified using decontextualized data.
    
    Another criticism is in lack of scope that simply requiring the same data and code used to perform the analysis has when the ultimate goal is reproducibility of the results. As Keiding puts it, "it ridicules our profession to believe that there is a serious check on reproducibility in seeing if somebody else's computer reaches the same conclusion using the same code on the same data set as the original statistician's computer did." Without knowledge of the decisions that went into the construction of the dataset, it is unlikely that any semblance of a true reproduction could be achieved. This ties in with Keiding's final criticism being that not including information about the original context in which the data were formed would make it nigh impossible for some other interdisciplinary group to understand how to reproduce the results. While Peng's proposal left a space for such "external data or auxiliary files", Keiding asserts that such information is pertinent to achieving reproducibility.
    
    3. **Which point in the commentaries speaks to you the most? Why?**
    
    I found Cox's proposal of avoiding independent replication of the statistical analyses interesting. As many of the other authors, including Peng himself, discuss, there have been many examples of data misuse or incorrect analyses that have led to faulty conclusions. While Peng's proposal to use editors to, as Goodman puts it, check arithmetic doesn't seem to be the best use of their time, I do believe that verifying results is a worthwhile endeavor for an academic journal. I agree with Keiding's criticisms that simply making sure that the code used to perform the analyses works on a different computer isn't a good way to go about checking results. However, maybe including a substantial amount of auxilliary data and suplementary materials, as Cox discusses, might provide better context in which conclusions can be verified.
    
    4. **How does Keiding respond to the commentary you picked. What are his main points in his response?**
    
    Keiding responds to Cox's commentary by agreeing that Peng's reproducibility proposal is certainly a step in the right direction, but wouldn't quite achieve its ultimate goal in its proposed form. His major point in this commentary response is that Peng's original proposal missed the need to provide the "substantive context" in which a given dataset was created along with the dataset. Better documentation might lead to more transparency of how data came to be, so enforcing the addition of supplementary, expositional materials along with data/code would make the exercise of ensuring reproducibility more than just an "auditing activity".
    
2. **Describe your experience with a data intensive (collaborative) project. What are the most prominent issues with ensuring reproducibility of research results (focus on data related aspects)? What would you do differently if you could go back in time?**

  For the STAT 579 Final Project last semester, my teammates and I made a point to archive any data-related decisions that we made so that we could later justify our actions if needed to. For example, we made sure to not only save any scripts used to clean or transform data, but to provide exposition as to why we decided to clean/transform the data in the way we did. Using R Markdown made this process significantly easier since we were able to construct a "data narrative" around code chunks to provide context for the function of the code. Even with this documentation process, I felt that our team's members were often working on their own segment of the project and not ensuring that the decisions that one of us made were understood by the group overall. If I were to go back in time, I would make more of an emphasis on periodically communicating each member's progress. It may have also been useful to work together on the same Rmd file so that we could have made a more fluid connection between each other's work.
