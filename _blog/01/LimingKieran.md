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

[I answered a question about categorizing NA data in R.](https://stackoverflow.com/questions/70839794/recode-continuous-data-into-categorical-data-using-is-na-and-if-else-in-r/70839935#70839935)

3. **Relate your experience of answering the question to your reading. **
 
This question did a decent job of following stackoverflow's good question guidelines. It had a title that accurately described the problem that the user was tring to solve. However, initially the used did not provide code or an example of the issue they were having. This appears to have been updated by the time I answered their question. 

I tried to follow the idea of the minimal complete verifiable example. I started by creating a small toy example for the user. Then, I provided a short snippet of code that achieved the outcome the user was looking for within their specifications. Here I tried to abide by the idea of minimal while still being readable. Additionally, my answer was complete, because it solved the user's problem. Finally, The code I provided was reproducible because it could be copied and pasted by the user and ran on their R without any alterations.  

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
