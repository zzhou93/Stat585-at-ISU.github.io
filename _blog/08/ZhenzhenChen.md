---
title: "It's magick!"
author: "Zhenzhen Chen"
topic: "08"
layout: post
root: ../../../
---

Write a blog post answering the following questions and detailing the progress: 

1. **Describe the difference between formats png, svg, and pdf. State your sources with (working!) links (take a look at the RMarkdown cheatsheet for RStudio to learn how to make working links). Make one plot in ggplot2 and save it (using R code) in each of the three file formats you discussed. Comment on the differences you observe in their usage.**

[Click me](https://www.95visual.com/blog/svg-pdf-jpg-png-whats-the-difference)

Scalable Vector Graphics (SVC) : 1). can use any browser to open it
2). it would not loss of image quality when you compressed or stretched
3). you can not read only a part of the graphic object. 

Portable Document File (PDF) : 1). can be view, edit, print or electonically transmitted by uploding, downloading or attaching it to message. 
2). can set a password to protect it, in case you want to restrict access and prevent copying or tampering. 
3). can be viewed by all browsers with the help of a blug-in. 

Portable Network Graphics (PNG) : 1). required a licensing fee from the compant that held the patent.
2). can not work for all browsers. 
3). with compression and a wider range of color it would not loss of detail, and still have higher quality graphic.


{% highlight r %}
library(tidyverse)
library(MASS)

pic <- ggplot(data = crabs, aes(x = FL, y = CW)) + 
  geom_point() + 
  geom_density2d() + 
  theme_bw()
{% endhighlight %}


{% highlight r %}
library(svglite)
ggsave("Ppng.png", plot = pic, device = "png")
{% endhighlight %}



{% highlight text %}
## Saving 7 x 7 in image
{% endhighlight %}



{% highlight r %}
ggsave("Ppdf.pdf", plot = pic, device = "pdf")
{% endhighlight %}



{% highlight text %}
## Saving 7 x 7 in image
{% endhighlight %}



{% highlight r %}
ggsave("Psvg.svg", plot = pic)
{% endhighlight %}



{% highlight text %}
## Saving 7 x 7 in image
{% endhighlight %}

The pdf and svg have the same file that are 5.98 x 5.39 in image. However, the png has the largest, that is 7 x 7 in image. 

2. **Use `magick` functionality to create an image to be used for a hex sticker.**  package `hexSticker` can help you to get started on dimensions of the sticker. **Include all code necessary to produce your sticker.** In case you are using local images, post those in a folder on **your** website and use the URL to link to them.


{% highlight r %}
library(magick)
library(hexSticker)

zzc <- image_read("https://t3.ftcdn.net/jpg/01/89/08/82/240_F_189088224_tiGffiF5egyRmTI5Oiqhkq62msigMBz6.jpg")
print(flower)
{% endhighlight %}



{% highlight text %}
## Error in print(flower): object 'flower' not found
{% endhighlight %}



{% highlight r %}
pic1 <- sticker(zzc, package = "ZC", h_fill = "white", s_width = 1, s_height = 1, s_x = 1, s_y = 0.9, p_x = 1, p_y = 1.5, p_size = 16)
print(pic1)
{% endhighlight %}

![center](../figure/08/ZhenzhenChen/unnamed-chunk-3-1.png)
