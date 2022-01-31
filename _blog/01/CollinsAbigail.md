---
layout: blog
topic: "01"
short-topic: Asking Good Questions
due-date: 2022-01-27
root: ../../
---

## Prompt:

Asking good questions is a valuable skill to have - asking questions in an online setting is both easier and harder than asking questions in person: we can prepare to ask a question but we are also expected to prepare.
The links posted here give some advice on how to ask good questions:

- stackoverflow's [Asking a good question](http://stackoverflow.com/help/how-to-ask)

- R's [Posting guidelines](https://www.r-project.org/posting-guide.html)

- [minimal complete verifiable example](https://stackoverflow.com/help/mcve), [minimal reproducible example](https://www.tidyverse.org/help/)

Follow these links and read through the advice given, then

1. **Pick at least one question from stackoverflow or the R help and answer it.**

Write a blog post answering the following questions: 

2. **Document which question you answered (link to your answer).**

Link to question/answer: https://stackoverflow.com/questions/70572856/adding-datapoints-to-a-boxplot/70871635#70871635 
Link to answer: https://stackoverflow.com/a/70871635/18041385 

3. **Relate your experience of answering the question to your reading. **

The question I answered in Stackoverflow was a difficult question to answer in the sense that little information was provided. The author did not follow many of the steps to ask a good question. Because of this, I was not able to provide an exact solution, but rather a suggestion. The question I answered was asking how to create a boxplot with the data points shown in R. As discussed in the first Stackoverflow link, your question title should summarize the main problem in a concise way. I will acknowledge that the author did do this. I was able to have an idea of the skills needed to answer the question before reading any details. However, no further context or code was provided. The author mentioned that they were new to R, so it would have been beneficial for them to provide minimal and reproducible code. That is, they should have provided code, with a small dataframe composed of general/understandable variable names to make a boxplot (assuming they knew how to do so). This way I would have been able to reproduce the code easily by copying and pasting it into to R. Additionally, my response could have used the same dataframe/variable names so the author would have a better understanding. Since no dataframe or variable names were used, I had to use general names in my ggplot solution that may confuse the author (assuming they are unfamiliar with ggplot2). In summary, I was not able to provide a clear solution that I know will work for the author. I assume they will need to comment and ask further, more specific questions in order to get the desired plots. I have learned how important it is to provide context of the problem and minimal, complete, and reproducible code in order to get a good answer to a good question. 

<!--Go to [https://github.com/Stat585-at-ISU/blog](https://github.com/Stat585-at-ISU/blog) for instructions about how to prepare and submit your blog post.-->
Instructions to follow.


{% assign num_posts = site.blog | size %}
{% if num_posts > 0 %}
## Class posts:

<ul>
{% for post in site.blog %}
  {% if page.topic == post.topic %}
  <li><a href="{{ post.url }}">{{ post.title }} by {{ post.author }}</a></li>
  {% endif %}
{% endfor %}
</ul>
{% endif %}
