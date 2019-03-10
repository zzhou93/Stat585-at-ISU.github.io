---
title: "It's magick!"
author: "Joe Zemmels"
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

png vs svg (Source: [Australian National University, "What is the difference between a png file (raster image) and a svg file (vector image)?"](http://asiapacific.anu.edu.au/mapsonline/faq/what-difference-between-png-file-raster-image-and-svg-file-vector-image)): The main difference between png and svg files is the way in which the image data is stored. Portable Network Graphics files are a type of bitmap or raster image file format. This means that the file is made up of a set of pixels, each of which containing color information (such as rgb or grayscale values). Scalable Vector Graphics, on the other hand, contain image information in the form of a set geometric objects. This means that no matter how much an svg image is zoomed, the image will not become grainy or pixelated (hence the "Scalable" in the name). Png images, on the other hand, cannot scale well since they are just a grid of discrete pixels.

pdf vs png and svg (Source: [Abbyy.com, "What is a PDF?"](https://www.abbyy.com/en-us/finereader/what-is-pdf/)): The Portable Document Format isn't a file type meant for images specifically. Rather, the main benefit of pdf files is that they look the same no matter the operating system, device, or reader with which they are viewed. Pdf images can be bitmap or vector images (Source: [Visual Integrity, "Raster vs Vector Files"](https://visual-integrity.com/faqs/spotting-difference-vector-raster-pdf/)). However, because pdfs are designed to keep the layout and look of the original document consistent no matter where they are viewed, it is harder to edit a pdf images than a png or svg image.


{% highlight r %}
library(tidyverse)
library(magick)

fig <- image_graph(width = 400, height = 400, res = 96)
mtcars %>%
  ggplot(aes(x=hp,y=mpg,colour=factor(cyl))) + 
  geom_point() +
  geom_smooth(method="lm",se = FALSE)
dev.off()
{% endhighlight %}



{% highlight text %}
## quartz_off_screen 
##                 3
{% endhighlight %}



{% highlight r %}
#Save png and pdf using magick
image_write(fig,"mtcars.png",format = "png")
image_write(fig,"mtcars.pdf",format = "pdf")

#Save svg using ggsave
plt <- mtcars %>%
  ggplot(aes(x=hp,y=mpg,colour=factor(cyl))) + 
  geom_point() +
  geom_smooth(method="lm",se = FALSE)

ggsave("mtcars.svg",plot=plt,width=10,height=8)
{% endhighlight %}

(I'm not sure where you want the images saved, but I imagine you don't want them in the blog-2019 directory). I see that png and pdf images are quite portable and easy to write. If I were interested in sending an image to a colleague, then I would likely use those. However, an svg file would be useful to store locally so that I would have at least one high-quality copy of the image.


2. **Use `magick` functionality to create an image to be used for a hex sticker.**  package `hexSticker` can help you to get started on dimensions of the sticker. **Include all code necessary to produce your sticker.** In case you are using local images, post those in a folder on **your** website and use the URL to link to them.


{% highlight r %}
library(hexSticker)

image <- image_read("https://pbs.twimg.com/profile_images/915963646575968256/q4WcPXLF_400x400.jpg") %>%
  image_fill("#2CA8FF",fuzz=20) %>%
  image_transparent("#2CA8FF")

sticker <- sticker(image,package="csafe",p_size=25, p_color="white",p_y=1.6,s_x=1,s_y=.85, s_width=1.3,s_height = 1.4,h_fill="#2CA8FF",h_color="#4a8eff")
sticker
{% endhighlight %}

![center](../figure/08/ZemmelsJoe/unnamed-chunk-2-1.png)

{% highlight r %}
#Played around with these colors so that the inside of the logo was made transparent too:
image <- image_read("https://pbs.twimg.com/profile_images/915963646575968256/q4WcPXLF_400x400.jpg") %>%
  image_transparent("white",fuzz=20)

sticker <- sticker(image,package="csafe",p_size=25, p_color="gray40",p_y=1.6,s_x=1,s_y=.85, s_width=1.3,s_height = 1.4,h_fill="gray90",h_color="#4a8eff")
sticker
{% endhighlight %}

![center](../figure/08/ZemmelsJoe/unnamed-chunk-2-2.png)

I can't seem to stop the "csafe.png" file from being created. I would like to just print it out, but it seems to want to save it as a file.
