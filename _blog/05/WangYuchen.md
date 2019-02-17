---

title: "More on Reproducibility..."

author: “Yuchen Wang”

topic: "05"

layout: post

root: ../../../

---
1. **Answer each of the following questions with at least 2-3 sentences.**



    1. **Summarize Roger Peng's outline for reproducibility in** *Biostatistics*. 
    The data used in producing the results should be provided and the authors need to make sure obtaining necessary permissions. The computer code should be provided and the software should be widely available. And the same results should be get from the provided data and the provided code by anyone. 

    2. **What are Keiding's main criticisms of the proposal?**. 
    The focus on reproducibility is actually an encouragement to conducting “alternative analyses”. And there are more important terms in statistical analysis than the calculations. 

    3. **Which point in the commentaries speaks to you the most? Why?**
    The point of working reproducibly can avoid the computing errors. Only when the code and data are open to other people, the results can be checked and convince people. If we do not know what have been done behind the results, the results will be less convincing.

    4. **How does Keiding respond to the commentary you picked. What are his main points in his response?**

    Keiding claims that Donoho did not explain how to connect the collaborative groups and the substantive context, and there is no space for imagination in such framework (work reproducibly). If people know the way to find the results, the imagination will be unnecessary.
    Keilding insists that working reproducibly is not easy to practice in the real world and does no good in encouraging people doing creative research nor understanding their own research results. But this proposal do have other benefits, which are mentioned by Cox and Donnelly.


2. **Describe your experience with a data intensive (collaborative) project. What are the most prominent issues with ensuring reproducibility of research results (focus on data related aspects)? What would you do differently if you could go back in time?**
   I was working on a course project with several teammates. When we were working on factor engineering, we need to change several numeric factors in to categorial factors, and change several categorial ones into numeric for easier conducting. But my result was totally different with one teammate’s even I followed his idea. We did not know what happened. After a lot of checking, I found out that I forgot to change the factor levels into characters before change them into numeric values. This little misconducting led to a lot problem. If I could do it again, I would make sure every details and read his code carefully before I write my own code.
