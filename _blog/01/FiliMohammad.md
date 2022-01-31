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

<br>

1. **Pick at least one question from stackoverflow or the R help and answer it.**

I answered two questions from [stackoverflow](https://stackoverflow.com/) which were asked just recently at the time of answering.

<br>


2. **Document which question you answered (link to your answer).**

The questions can be found using the links below:

* *Question 1*: [Reformat Dataframe to start a new row at a certain column](https://stackoverflow.com/questions/70793051/reformat-dataframe-to-start-a-new-row-at-a-certain-column/70795468#70795468)


* *Question 2*: [Repeated row Id with 3 values for each Id](https://stackoverflow.com/questions/70794432/repeated-row-id-with-3-values-for-each-id/70794861#70794861)

<br>

3. **Relate your experience of answering the question to your reading. **

* *Question 1*: \
    * The title of question was very unclear to me. (poorly stated)
    * There was no code to reproduce the example.
    * In terms of conciseness, it was fine.
    * No grammatical errors.
    * Showing the desired output helped me better understand the need.
    * I guess if the individual searched a little bit, he could find a couple of  already existing solutions or ideas. \



* *Question 2*: \
    * Title was not well stated.(unclear)
    * The question was repetitive (questioner didn't not searched or checked previous questions)
    * The code to generate the example was minimal and complete.
    * No grammatical errors.
    * the desired output was shown.
    * The question could be shorter by removing the unnecessary explanations.



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
