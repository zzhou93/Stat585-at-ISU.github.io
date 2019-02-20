---
title: "More on Reproducibility"
author: "Gulzina Kuttubekova"
root: ../../../
layout: post
topic: '05'
---


1. Answer each of the following questions with at least 2-3 sentences.
 - Summarize Roger Peng’s outline for reproducibility in Biostatistics:

Based on Roger Peng’s newly introduced regulations, articles which are claimed to be reproducible should be submitted with supplementary materials along with itself. AER will go through the article if only it is approved for publication. AER should be able to recover exactly the same results up to some tolerable error from the same data and the code written strictly in R. It is one of the requirements that authors use open source data, software and open, documented formats for the code. Results also have to be written and submitted in LaTeX.

 - What are Keiding’s main criticisms of the proposal?
 
 Keiding mainly focuses on the fact that: by endlessly trying to get an ultimately same numerical result from the same data set using the same code is useless if the substantial context of the research is forgotten. Focusing only on the technical part would generate tons of “reproducible” papers which are useful for the authors and other researchers like themselves, leaving colleagues from the industry or medicine outside. 
 
 - Which point in the commentaries speaks to you the most? Why?
 
 Commentary from Norman E. Breslow, is the most meaningful from my perspective. Although he doesn’t agree with Keiding’s criticism, he also doesn’t support Peng’s suggested regulations himself. He mentioned that focusing only on the data and getting the same outcome as in the paper can hide other important aspects in the paper. To give an example: there might be significant issues with measurement error, multicollinearity, selection bias, which might be left unnoticed. However, he believes that retaining the original data and the sample code along with paper will make it more reader interactive. I also think there always will be a trade-off between focusing on the technical part or on context.
 
 - How does Keiding respond to the commentary you picked. What are his main points in his response?
 
 He mainly responded to Donoho, who shares the same views about the Keiding’s criticism with Breslow. Keiding gave a couple of counterexamples by mentioning that strict regulations might question the role of imagination in science. He gives as an argument the possible fact of ruling out the creativity while documenting and writing everything according to a strict protocol.
 
 
 
 
 2. Describe your experience with a data intensive (collaborative) project. What are the most prominent issues with ensuring reproducibility of research results (focus on dta related aspects)? What would you do differently if you could go back in time?
 
 Last semester I had an experience of taking part in data mining competition, where I (personally) faced many issues with reproducibility. We had a large set of data, consisting of many different data sets. While members of a group were each working on their parts, I had difficulty in following them up, since sometimes the codes as well the documentation was not provided by the implementer or it was lost within a bulk of other changes. To give an example: the new dataset, containing only the covariates, was created with the help of feature engineering. However, I could not reproduce it later, simply because of the absence of the appropriate code. 

If I could go back in time, I would suggest my teammates record every possible change, or simply use GitHub and regularly push the commits.

 
 
 
 
 
 
 
 
 
