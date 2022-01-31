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

Here is the question that I answered on stackoverflow: Updated to Mac OS Big Sur and getting "Warning: Expected min height of view" errors in R

2. **Document which question you answered (link to your answer).**

Here is the link to my answer: [https://stackoverflow.com/a/70883023/11251357](https://stackoverflow.com/a/70883023/11251357)

3. **Relate your experience of answering the question to your reading. **
 
I was searching on Stackoverflow to find which question to answer and found out that the question given above did not have any answers and a lot of people are facing the same issue. Personally, I did not face this issue since I am using latest version of Xcode,i.e Xcode 12. It throws a warning prompt while using Xcode 11.

I referred to this link for my reading: [https://github.com/macvim-dev/macvim/issues/1114](https://github.com/macvim-dev/macvim/issues/1114)

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
