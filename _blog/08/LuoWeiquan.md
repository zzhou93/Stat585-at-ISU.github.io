---
title: "It's magick!"
author: "Weiquan Luo"
topic: "08"
layout: post
root: ../../../
---

1. **Describe the difference between formats png, svg, and pdf. State your sources with (working!) links (take a look at the RMarkdown cheatsheet for RStudio to learn how to make working links). Make one plot in ggplot2 and save it (using R code) in each of the three file formats you discussed. Comment on the differences you observe in their usage.**

* the following is my little experiment.

{% highlight r %}
library(ggplot2)
library(magick)
head(iris)
ggplot1 <- ggplot(data=iris) +
  geom_point(mapping = aes(x= Sepal.Length, y = Sepal.Width))
ggsave("ggplot1.png", device = "png")
ggsave("ggplot1.svg", device = "svg")
ggsave("ggplot1.pdf", device = "pdf")
{% endhighlight %}
|Criterion| Portable Network Graphics (png)| Scalable Vector Graphics (svg)| Portable Document File (pdf)|
|--------------|-------------------------|-------------------------|-------------------------|
|Image quality | bitmap | not problem with compressing or stretching | not problem with compressing or stretching | 
|storage size|53 KB|31 KB| 6 KB|
Table: Comparision between Resulting Graphic foramat


* The [95VISUAL\'s blog](https://www.95visual.com/blog/svg-pdf-jpg-png-whats-the-difference) provides a great comparision between various graphic formats. Within the scope of this blog, the following three graphic formats are discussed. 

|Criterion| Portable Network Graphics (png)| Scalable Vector Graphics (svg)| Portable Document File (pdf)|
|--------------|-------------------------|-------------------------|-------------------------|
|Image quality | [Since it is a raster image format, so it made up of a fixed number of  pixels that form a complete image. The image cannot be enlarged without distortion occurring](http://asiapacific.anu.edu.au/mapsonline/faq/what-difference-between-png-file-raster-image-and-svg-file-vector-image)|An SVG image can be compressed or stretched without loss of image quality. [A vector image remains crisp and clear at any resolution or size](http://asiapacific.anu.edu.au/mapsonline/faq/what-difference-between-png-file-raster-image-and-svg-file-vector-image)|It supports both raster and vector image format.|
|Web pages compatibility|Yes, the PNG format is suitable for web images like logos that you want to include transparency and fading effects |Yes, but not support for transparency|Yes, but not support for transparency|
|Storage size|Because of the size of a PNG file, this format is not recommended for photos as JPG is unless file size is not an issue.|SVG image element files are smaller than if the image were present in a raster format, but if an object in the image contains many small elements, the size of the file can grow very fast| the file sizes are usually smaller than if you saved a document in its native format including its graphic files.|
Table: Summary of Comparision between Graphic foramat

  A cross-check table for comparision from the 95VISUAL is attached at below.
<img src="./https://www.95visual.com/sites/default/files/images/inline/file_format_chart.png" title="file_format_chart.png" alt="file_format_chart.png" width="40%" />

2. **Use `magick` functionality to create an image to be used for a hex sticker.**  package `hexSticker` can help you to get started on dimensions of the sticker. **Include all code necessary to produce your sticker.** In case you are using local images, post those in a folder on **your** website and use the URL to link to them.

* the following is my code to generate a hex sticker.

<img src="./https://github.com/WeiquanLuo/WeiquanLuo.github.io/raw/master/IFEWBNet.png" title="IFEWBNet.png" alt="IFEWBNet.png" width="50%" />

Reference: 

* https://omnianalytics.io/isu-graphics/magick/
* https://cran.r-project.org/web/packages/magick/magick.pdf

Code:


{% highlight r %}
library(tidyverse) # piping
library(magick) # graphic editing
library(hexSticker) # forming sticker
library(sysfonts) # for font style
{% endhighlight %}


{% highlight r %}
# read in FEW
FEW <- image_read("https://github.com/WeiquanLuo/WeiquanLuo.github.io/raw/master/FEW.jpg")

w <- image_info(FEW)$width
h <- image_info(FEW)$height

FEW <- FEW %>%
  image_contrast(sharpen = 100) %>% 
  image_fill("white", paste0("+", w/2, "+", h/2), fuzz=7) %>% 
  image_fill("white", paste0("+", w/25, "+", h/25), fuzz=7) %>% 
  image_negate %>% 
  image_transparent("black") %>% 
  image_negate %>% 
  image_crop("250X+63+0") %>% 
  image_scale("200x")

FEW <- image_composite(image_blank(400,400,color="white"), FEW, offset = paste0("+",(400-200)/2,"+",(400-200)/2)) %>% 
    image_transparent("white"); FEW
{% endhighlight %}


{% highlight r %}
# read in Iowa_watershed
Iowa_watershed <- image_read("https://github.com/WeiquanLuo/WeiquanLuo.github.io/raw/master/ia_watershed.jpg")
w <- image_info(Iowa_watershed)$width
h <- image_info(Iowa_watershed)$height

Iowa_watershed <- Iowa_watershed %>%
  image_fill("red", paste0("+", w/30, "+", h/30), fuzz=10) %>%
  image_oilpaint(radius = 3) %>% 
  image_transparent("red") %>% 
  image_scale("400x")

Iowa_watershed <- image_composite(image_blank(400,400,color="red"), Iowa_watershed, offset = paste0("+",(400-400)/2,"+",(400-287)/2)) %>% 
    image_transparent("red"); Iowa_watershed
{% endhighlight %}


{% highlight r %}
# combine layers
IFEW <- image_composite(Iowa_watershed,FEW) %>% 
  image_transparent("red"); IFEW

# font
font <- "Indie Flower"
font_add_google(font)

# sticker 518*600
sticker(IFEW, package = "IFEWBNet",
        p_size = 30, p_y = 0.6, p_color = "grey40", p_family = font,
        s_x = 1, s_y = 1, s_width = 2, s_height = 1.5,
        h_fill = "gray95", h_color = "aquamarine4", h_size = 1.8)
image_read("IFEWBNet.png")
{% endhighlight %}



