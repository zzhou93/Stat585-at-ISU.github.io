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
https://stackoverflow.com/questions/70851687/ifelse-statement-if-the-strings-starts-or-ends-with-a-particular-set-of-charac/70852349#70852349

This is a string manipulation question in R, asking how to substitute a certain sub-string if this sub-string is found at the end of strings in data.frame


3. **Relate your experience of answering the question to your reading. **

The title for this question is clear and specific:"Ifelse statement : if the strings starts or ends with a particular set of characters, delete them", the author
also includes relevant tags like "r", "string", "if-statement" and "substring". Although the "Ifelse statement" might not be necessary in the title, as to my point
of view, this question is more like asking string manipulations. The specific question make it a lot easier for people to find this question, although it is a new 
question, I found two other people also posted their solutions during the time I composed mine.

A chuck of code as well as the code the authour tried or want to work with are included in the question, which make it easier to understand what specific part
of string manipulation the author wants to ask.

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
