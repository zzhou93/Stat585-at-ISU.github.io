---
title: "Using GitHub as a Website Host"
author: "Yudi Zhang"
topic: "06"
layout: post
root: ../../../
---

- My website:
https://yudizhangzyd.github.io

- Problems:
When I was building the website, I didn't notice the format of _site.yml file. I first used:

navbar:
  title: "Yudi Zhang"
  left:
    - text: "research"
      href: research.html
  output:
    html_document:
      theme: flatly
      highlight: textmate
      css: styles.css
 
 But the "output" and the following should be at the same positions as "navbar", so it gave me quite strange format and my theme didn't work.
 
 And when I modified my website, I found it doesn't get updated. I didn't find solutions, until it updated 5 minutes later.
