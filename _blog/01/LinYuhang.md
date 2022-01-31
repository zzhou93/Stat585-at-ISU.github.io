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
    
  The question I answered:
  [setting a limit/threshold for each value in a given row(s) of a matrix during a forloop](https://stackoverflow.com/a/70857902/18033429)

3. **Relate your experience of answering the question to your reading. **

  First of all,
  I would say finding a "suitable" question to answer is much harder than what I thought before,
  which surprised me a lot.
  Originally,
  after reading those four posted blogs you shared, I just realized that it is even hard to ask a question.
  When I began to search on StackOverflow,
  those unanswered questions were either duplicated, not making sense to me, not reproducible, or too hard for me to answer.
  Even if I finally found a reasonable question to answer, it still suffers from several perspectives described in those blogs.
  
  The question is not well-phrased.
  The title is suitable enough to summarize the problem,
  and the question is well introduced before any code is posted.
  I can see where the author was stuck,
  but I cannot link his code with his question at the very first glance.
  I don't think I would spend time locating where his problem was embedded in his code if I didn't have enough time.
  
  The sample code provided is reproducible and just enough from my point of view.
  I successfully reproduced his problem and the answer by ```reprex``` package in the end.
  But the problem seems to be fairly straightforward once I understand it,
  and I hope I understand it correctly.
  The author was already on the right track, and as long as he did some research or even proofread it before he posted the question,
  I believe he could work it out himself.



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
