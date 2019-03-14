---
title: "It's magick!"
author: "Earl Hur"
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


Write a blog post answering the following questions and detailing the progress: 

1. **Describe the difference between formats png, svg, and pdf. State your sources with (working!) links (take a look at the RMarkdown cheatsheet for RStudio to learn how to make working links). Make one plot in ggplot2 and save it (using R code) in each of the three file formats you discussed. Comment on the differences you observe in their usage.**

    PNG File: Portable Network Graphics file was improved from GIF file based on raster images. It supports the same color pallette but has better transparency. This format is not compatible to many other formats and has larger than the JPG files. ([Source](https://www.movavi.com/blog/what-image-format-is-the-best.html)). 
    
    SVG File: Scalable Vector Graphics is an XML-based vector image format. As the XML file do, this format also be editted using any text editor. This format also supports interactivity and animation. ([Source](https://www.coreldraw.com/en/pages/svg-file/))
    
    PDF File: Portable Document Format can store both raster and vector based format. This file format does not support transparency, but is relatively smallin its size compare to the other formats. ([Source](https://en.wikipedia.org/wiki/PDF#Imaging_model))



{% highlight text %}
## Error in library(statnet): there is no package called 'statnet'
{% endhighlight %}


![center](./../figure/08/EarlHur/unnamed-chunk-2-1.png)


{% highlight r %}
ggsave("network.pdf")
ggsave("network.png")
ggsave("network.svg")
{% endhighlight %}


    It seems like the PNG file is far larger than the other two and SVG file is the smallest. The quality of the format seems to be similar to each other. When we print and share the image with others, PDF format would be the most appropriate.
    
    
    


{% highlight r %}
broncos <- image_read("https://earl88.github.io/broncos.png")
sticker(broncos, package = "Broncos", 
        p_color = "#FF0000", h_fill = "white", 
        h_color = "#FF0000",
        s_width = 1.5, s_height = 1.5, s_x = 1, s_y = 1, 
        p_x = 1, p_y = 1.65, p_size = 16)
knitr::include_graphics("Broncos.png")
{% endhighlight %}

![center](./Broncos.png)

