---
title: "It's magick!"
author: "Gani Agadilov"
output:
  pdf_document: default
root: ../../../
layout: post
topic: 08
---

Write a blog post answering the following questions and detailing the progress: 

1. **Describe the difference between formats png, svg, and pdf. State your sources with (working!) links (take a look at the RMarkdown cheatsheet for RStudio to learn how to make working links). Make one plot in ggplot2 and save it (using R code) in each of the three file formats you discussed. Comment on the differences you observe in their usage.**

The link to the working sourse is [95visual](https://www.95visual.com/blog/svg-pdf-jpg-png-whats-the-difference).

The Portable Network Graphics format(PNG) is an open format which is an alternative to GIF format. The PNG format can be compressed without losing the quality of color of the graph. Mainly, the PNG format used on websites for images but for photos as JPG.

The Scalable Vector Graphics (SVG) is designed for an image and its elements in XML. The SVG can be used to create icons and compressing does not affect the quality of the image. The main feature to note is the size of the objects. If elements are small, the size of the file will become large. The part of the graph cannot be read.

The Portable Document File (PDF) is a format that provides an electronic image of text and graphics. The effective aspect of the PDF format is having small size and links can be embedded in the document. The PDF format files might have codes and electronic signature to access the document.



{% highlight r %}
library(ggplot2)
library(svglite)

# Read the dataset
data("midwest", package = "ggplot2")

# Plot the density of the population
density <- ggplot(midwest, aes(x=area, y=poptotal)) + 
  geom_point(aes(col=state, size=popdensity)) + 
  geom_smooth(method="loess", se=F) + 
  xlim(c(0, 0.1)) + 
  ylim(c(0, 500000)) + 
  labs(subtitle="Area Vs Population", 
       y="Population", 
       x="Area", 
       title="Scatterplot", 
       caption = "Source: midwest")
density
{% endhighlight %}

![center](./../figure/08/GaniAgadilov/unnamed-chunk-1-1.png)

{% highlight r %}
# Save files in three different formats.

ggsave("density.pdf")
{% endhighlight %}



{% highlight text %}
## Saving 7 x 7 in image
{% endhighlight %}



{% highlight r %}
ggsave("density.png")
{% endhighlight %}



{% highlight text %}
## Saving 7 x 7 in image
{% endhighlight %}



{% highlight r %}
ggsave("density.svg")
{% endhighlight %}



{% highlight text %}
## Saving 7 x 7 in image
{% endhighlight %}
After saving the files, it can be seen that the PNG format has the largest size and the PDF format has the smallest size. However, the quality of the image is better in png format.

2. **Use `magick` functionality to create an image to be used for a hex sticker.**  package `hexSticker` can help you to get started on dimensions of the sticker. **Include all code necessary to produce your sticker.** In case you are using local images, post those in a folder on **your** website and use the URL to link to them.

I desided to make a sticker by using the ISU logo. 

{% highlight r %}
library(hexSticker)
library(magick)

#Read the png file form my website
statlogo <- image_read('https://ganiagadil.github.io/logo.png')
print(statlogo)
{% endhighlight %}



{% highlight text %}
## # A tibble: 1 x 7
##   format width height colorspace matte filesize density
##   <chr>  <int>  <int> <chr>      <lgl>    <int> <chr>  
## 1 PNG      208    242 sRGB       FALSE     7390 72x72
{% endhighlight %}

![center](./../figure/08/GaniAgadilov/unnamed-chunk-2-1.png)

{% highlight r %}
#Create the sticker
sticker(statlogo, package = "Significant", p_color = "red", 
        s_x =1,s_y = 0.8,s_width = 0.9, s_height = 0.9,
        h_fill = "white", h_color = "black", spotlight = TRUE, 
        l_alpha = 0.5,filename = "Statlogo.png")
{% endhighlight %}



