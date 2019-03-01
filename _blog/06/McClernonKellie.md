---
title: "Blog Post 6: Using GitHub as a Website Host"
author: "Kellie McClernon"
topic: "06"
layout: post
root: ../../../
---

## Background:

GitHub is an incredibly useful tool for project management and collaboration. It also has several useful features for professional promotion: you can host your own site on github using [GitHub pages](https://pages.github.com/), describe yourself using a GitHub developer profile, and even use [resume.github.io](http://resume.github.io/) to generate a resume summary of your activity on GitHub (you must opt-in by [starring the project page](https://github.com/resume/resume.github.com)). 

RStudio and the associated package infrastructure provide multiple ways to generate websites using Rmarkdown. You can complete this assignment using one of two options: 

- Simple RMarkdown websites    
For more information about simple R Markdown websites, please read the documentation at https://bookdown.org/yihui/rmarkdown/rmarkdown-site.html. Simple R Markdown sites are _not_ based on **blogdown**. They are probably good for websites with only a few Rmd documents.

- [Blogdown](https://github.com/rstudio/blogdown)    
For larger-scale and more sophisticated websites (such as blogs), you may want to use **blogdown** instead: https://github.com/rstudio/blogdown.

## Instructions:

1. Create a new GitHub repository named `<your-username>.github.io` (replacing "<your-username>" with your GitHub username). Initialize this repo with a readme.

2. Set up your website using either the Simple Markdown Site or Blogdown instructions below. If you would like to use this repository to host a blog, you may find Blogdown to be a more convenient option, however, it is more complicated than the simple Rmarkdown site. 

3. Create a file <LastnameFirstname>`.Rmd` in the 06 folder of the blog-2019 repository. In that file, add a link to your site (found at https://<your-username>.github.io). Write at least 2-3 sentences describing the problems you encountered while following these instructions, how you solved them, and how you anticipate using this site in the future. 

To get full marks for this blog post, you should modify your site beyond the default template files, adding at least some content that is unique to you - packages you find interesting, sites you enjoy, projects you have worked on, a page with your CV, etc.

### Simple RMarkdown Site

I chose to build a simple Rmarkdown site for now. The website I have begun can be found [kmcclernon.github.io](https://kmcclernon.github.io/). My biggest issue was that I wanted to make to make my website visually appealing from the beginning. However, I am a complete novice at web design so I do not know html formatting or what a CSS stylepage is. I looked at the documentation for simple R markdown sites on bookdown.org and was interested in customing the page styles, but I was not familiar with the theme "cosmos" that was used in the example. I started by looking at themes for rendering HTML pages through RMarkdown. Also on bookdown.org I found information about changing the appearance of HTML pages using bootstrap themes. Then I followed the link to [Bootswatch](https://bootswatch.com/3/) in order to preview the available themes. Even with my new bootstrap theme, I long for more creative power over the layout. After looking at example pages I think I need to consider **blogdown** for more control over the layout.  

I plan on using my site to provide information about projects I have completed. Also, I am working on starting a section that includes resources for my consulting clients. Questions on predictive models are becoming more common but often scientists in other fields need help with the coding aspect. I would like to host my sample code on my webpage instead of sending the files in an email. I have started a page on variable selection but I am still working on the content. In the future, I can send clients to my webpage instead of attaching various code files in an email. As my webpage grows in content I anticipate needing to convert it to a **blogdown** site.
