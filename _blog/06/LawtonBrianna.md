---
title: "Blog #6: Using GitHub as a Website Host"
author: "Brianna Lawton"
topic: "06"
layout: post
root: ../../../
---

## First RMarkdown Website, YAH!

Welcome to my first Simple RMarkdown Website. I would consider myself a novice R language level coder but I learn new things each day to build on my current knowledge which keeps things interesting!

I did encounter some problems while building this Simple RMarkdown website, which are listed below along with how I went about solving them.

1. I had issue "building" my website the first time when I ran the "build" command. I tried running the rmarkdown::render_site() but I soon leared that I had to give RStudio time to buffer and recognize what I was doing. 

2. Spacing matters! I had some extra spacing in between my "text" and "href" lines, which would not allow me to "build" or update my website from time to time.

3. When adding my resume/cv it was originally a link to the pdf but I wanted it to automatically show up, so I inserted my direct pdf file in the "yml" file under that html sheet created.

4. Lastly, IMAGES! They gave me much grief. I learned that when inserting picture images into your html sheets, make sure you have them in the correct format (i.e. jpg or png) and have them in the orientation you want them to appear before importing them into your website. So, I leared this the hard way because many of my pictures appeared rotated or too big so I had to change the orientation by using the "rotate" command.Another part of inserting images within my website was having the right path (i.e.folder_name/image_name.jpg) [*note you don't need ""] to call that image when building your website. I had to make sure that all the pictures I wanted to use were inside my RMarkdown project folder and called properly. 

Now that you know some hints to help when building your first website, check out [mine](brlaw17.github.io)!
