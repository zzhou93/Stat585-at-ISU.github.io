---
title: "It's magick!"
author: "Eryn Blagg"
topic: "08"
layout: post
root: ../../../
---

## Background:

Image files come in all kinds of formats. There's png, tiff, svg, pdf, just to name a few. What's the difference, and how can we work with them?

Reading: 

  - Identify online sources to read up on differences between image file formats. 

  - The `magick` package allows us to work with raster images in R. Read through the  [magick vignette](https://cran.r-project.org/web/packages/magick/vignettes/intro.html) to learn about the package's functionality.

Write a blog post answering the following questions and detailing the progress: 

1. **Describe the difference between formats png, svg, and pdf. State your sources with (working!) links (take a look at the RMarkdown cheatsheet for RStudio to learn how to make working links). Make one plot in ggplot2 and save it (using R code) in each of the three file formats you discussed. Comment on the differences you observe in their usage.**

Portable Network Graphics (PNGs): PNG is a high-quality file format. This format is a lossless quality file, meaning it will not blur when uploaded. Portable Network Graphics files are a type of bitmap or raster image file format. They are made up of a set of pixels, containing color information. 

SVG is often used in website design, due to the fact that it loads at high speeds. Furthermore, Scalable Vector Graphics contain image information in the form of a set geometric objects. No matter how much an svg image is zoomed, the image will not become grainy or pixelated 

PDF The Portable Document Format is not really a picture image, it is often used for text, however, pdfs look the same no matter the operating system, device, or reader with which they are viewed, making it harder to edit them. 

info from: https://www.95visual.com/blog/svg-pdf-jpg-png-whats-the-difference


{% highlight r %}
library(magick)
library(tidyverse)
library(svglite)
{% endhighlight %}


{% highlight r %}
#read the image
ocean <- image_read('https://oceanconservancy.org/wp-content/uploads/2017/04/gulf-1600x1067.jpg')
image_info(ocean)
{% endhighlight %}



{% highlight text %}
## # A tibble: 1 x 7
##   format width height colorspace matte filesize density
##   <chr>  <int>  <int> <chr>      <lgl>    <int> <chr>  
## 1 JPEG    1600   1067 sRGB       FALSE   238767 72x72
{% endhighlight %}


{% highlight r %}
#making it into a ggplot 
oceana<-image_ggplot(ocean)
oceana
{% endhighlight %}

![center](./../figure/08/BlaggEryn/unnamed-chunk-3-1.png)


{% highlight r %}
#saving as png and pdf
image_write(ocean,"ocean.png",format = "png")
image_write(ocean,"ocean.pdf",format = "pdf")
{% endhighlight %}


{% highlight r %}
#saving as svg
ggsave(plot = oceana, filename = "dino.svg", device = "svg")
{% endhighlight %}



{% highlight text %}
## Saving 7 x 7 in image
{% endhighlight %}


2. **Use `magick` functionality to create an image to be used for a hex sticker.**  package `hexSticker` can help you to get started on dimensions of the sticker. **Include all code necessary to produce your sticker.** In case you are using local images, post those in a folder on **your** website and use the URL to link to them.
Making a hex sticker 

{% highlight r %}
wave<-image_read("https://photos.gograph.com/thumbs/CSP/CSP619/abstract-color-swirl-wave-vector-clipart_k6193211.jpg")%>%
  image_transparent("white", fuzz=10)
{% endhighlight %}



{% highlight r %}
library(hexSticker)
library(magick)
{% endhighlight %}


{% highlight r %}
oceanean<- sticker(wave, s_x=1, s_y=.9,s_width=1.5, s_height=1.5, package = "Oceanic", p_size=15, p_color = "lightsteelblue4", h_color="lightseagreen", h_size=3.5, p_family = 'mono', h_fill="seashell2")
{% endhighlight %}


{% highlight r %}
oceanean
{% endhighlight %}

![center](./../figure/08/BlaggEryn/unnamed-chunk-9-1.png)

## Instructions:

Update your forked version of the 'blog-2019' repository (or re-fork it after deleting your previous repo).

Save a **copy** of this file, replacing "Lastname" and "Firstname" with your own and *leave the original unedited*. (Note: Lastname = your family name, Firstname = your given name)

In **your copy**, replace the `title:` and `author:` fields in the YAML above, while leaving the remaining fields intact. Remove the background and the instructions sections and write your blog post! 

Once you are done, **create a pull request** to upload your changes to the original repository. Do not commit the compiled HTML file to the repository.
