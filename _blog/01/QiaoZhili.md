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

[Subset data from data.frame in R](https://stackoverflow.com/questions/70852996/how-can-i-subset-data-from-a-data-frame-in-r/70854288#70854288)

This is a question about subseting data frame in R by excluding certain conditions.

3. **Relate your experience of answering the question to your reading. **
 
 (1) The tags for the question is clear: "r", "dataframe" ans "subset".
 
 (2) The question itself is clear, easy to understand. The code example from the author is also straightforward.
 
 (3) The title is not very clear. "How can I subset data from a data.frame in R" is way too general. I couldn't figure out what specific question it is asking, until I clicked into the question's page and read the details.
 
 (4) No introduction about the question before the code block. I had to read through the code and understand it myself before I see the comments.
 
 (5) There is another responder at the time I wrote the solution 6 hours ago. And until now we are still the only two people responding.
 
 (6) It turns out that I myself used to be a very bad questioner...
 

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
