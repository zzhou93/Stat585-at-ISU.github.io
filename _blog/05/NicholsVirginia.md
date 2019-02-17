---
title: "More on Reproducibility..."
author: "Virginia Nichols"
topic: "05"
layout: post
root: ../../../
---


1. **Answer each of the following questions with at least 2-3 sentences.**

    1. **Summarize Roger Peng's outline for reproducibility in** *Biostatistics*. 
    
There are several 'levels' of reproducibility, and by making a tiered system it may allow researchers to adhere to the level they are most comfortable with. Providing a 'reprodicibility' stamp could provide incentive to go through the extra effort required to make things truly reproducible. 

This phrase particularly struck me:

*For authors interested in submitting materials satisfying the “reproducible” criterion, the journal is currently limiting submissions to those whose analyses are conducted using the R software environment.*

Only R-users can do fully reproducible research (for that journal, probably applies more broadly). This is insane. I interpret this as if you are a researcher, your research needs to be reproducible. So if you are a researcher, you must know R. 

I know this was written in 2009, but I feel like in my area (Agriculture) almost no progress has been made towards increasing reproducbility of research. Using Excel and SAS are ingrained in my discipline, and as demonstrated by this article, those tools do not facilitate reproducible work. 
    
    2. **What are Keiding's main criticisms of the proposal?**.
    
They feel it's a shallow definition of reproducibility - that the mechanics of analyzing data are personal, and to 'reduce' data to simply the code that analyzes it is disrepectful. I think they are being jerks. 

    3. **Which point in the commentaries speaks to you the most? Why?**

I feel that while Keiding raises important points, it distracts from a serious issue that is the baseline to any type of reproducibility. It's like someone said 'women have the right to vote'. And someone replying 'well, not everyone should have the right to vote, you should have to be civically engaged and informed in order to vote'. True, but phase one is giving women the right to vote, right? Phase one is make what you did reproducible. THEN we can argue about whether what you did is correct. Goodman's commentary reaffirms this. 

In a reply, Breslow asks an important question: Do articles that supply reproducible data/code get cited more? **Has this been answered?**

    4. **How does Keiding respond to the commentary you picked. What are his main points in his response?**
    

    
2. **Describe your experience with a data intensive (collaborative) project. What are the most prominent issues with ensuring reproducibility of research results (focus on data related aspects)? What would you do differently if you could go back in time?**

Often it is not clear who is in charge of data. In my own lab, we collect a large amount of sensor data, and ONE person wrote some code to process it and produce a 'quality-checked' version. No one looked over his code, and no one else was taught to run it. That person has now graduated. Who is going to take over? This was never discussed. 

Because I need some of the data, I've started picking through the code. I've found several bugs, and still cannot understand the data flow/code combination the original author envisioned (and he left no readme to help). If I could go back I would sit him down, make him run through it, take notes, and write my own readme. I would also have him put it in github, so when someone finds something funny they can submit an issue (and have that documented). I don't know how to do 'issues' in github yet though, so *I'm still working towards my own standards.* 
