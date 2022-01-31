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

The link to my answered question is [this](https://stackoverflow.com/questions/70888562/argument-is-not-numeric-error-in-r-using-aggregate-inside-a-user-defined-fun/70888858#70888858)

3. **Relate your experience of answering the question to your reading. **
 
 About the question: 
 
 I think the question asked is a good question. It has an informative title, describes the problem effectively, and provides example code. One thing that can be improved is to make its example reproducible. The author of the post uses `mydf` as the dataset in the example. However we have enough information to reproduce the problem using `mtcars`. 
 
 About my answer:
 
 I'm feeling that my answer might be too wordy, and I'm not sure that all the theories underneath my answer are correct. Hopefully my answer helps.
 

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
