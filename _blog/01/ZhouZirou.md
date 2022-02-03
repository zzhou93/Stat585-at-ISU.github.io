---
Title: "Blog 1"
author: "Zirou Zhou"
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

  https://stackoverflow.com/a/70827469/17987705

3. **Relate your experience of answering the question to your reading. ** 

  This is a Statistic problem by using the R. The poster have a very sepecific request about what he want and the function should be used.
  What I learned from the guaidelines is in the question he posted in a image or pdf, which is easy to read and reproduct. 
  However, his discriptions about what function should be used is not highlighted in the text, which is a little bit confussing.

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
