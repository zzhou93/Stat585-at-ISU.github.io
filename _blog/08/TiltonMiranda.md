---
title: "8: It's magick!"
author: "Miranda Tilton"
topic: "08"
layout: post
root: ../../../
---

**Note:** This blog requires the generation of a number of files. Knitting this document will create a directory called "MirandaTilton_blog8" in the current working directory, and all saved files will be stored there.


{% highlight r %}
mt_dir <- file.path(getwd(), "MirandaTilton_blog8")
if(!dir.exists(mt_dir)) {dir.create(mt_dir)}
{% endhighlight %}

# 1)

**Describe the difference between formats png, svg, and pdf. State your sources with (working!) links (take a look at the RMarkdown cheatsheet for RStudio to learn how to make working links). Make one plot in ggplot2 and save it (using R code) in each of the three file formats you discussed. Comment on the differences you observe in their usage.**

First, it is useful to understand the difference between raster and vector graphics. As described [at this link](https://www.logaster.com/blog/vector-and-raster-graphics/), raster graphics consist of small pieces, like a mosaic. Because the graphics are described pixel-by-pixel, it is easier to use smooth transitions of colors and shades; however, they take up more space to store and lose quality when increasing their size. Vector graphics, on the other hand, are described by continuous lines and curves associated with colors. Vector graphics take up less space and scale nicely, which makes it a better choice for, say, company logos that may need to appear on a business card or a billboard, but they do not allow smooth color transitions.

Of the three formats, PNG is a raster image format while SVG and PDF are vector formats. According to [this source](https://www.logaster.com/blog/jpg-png-svg-pdf-formats/), PNG is compressed without quality loss (as opposed to JPEG, which compresses with loss of quality) and is used for storing graphics with logos and sharp edges. PDFs may contain both raster and vector graphics elements within them. SVG (which aptly stands for "scalable vector graphics") is purely a vector graphics format which allows size increases without loss of quality.


{% highlight r %}
library(ggplot2)
library(magrittr)
if (!require("datasauRus")) {
  devtools::install_github("lockedata/datasauRus")
  library("datasauRus")
}

dino <- datasaurus_dozen[datasaurus_dozen$dataset == "dino", ]

d <- ggplot(dino) +
  geom_point(aes(x = x, y = y), color = "#7CAE00", size = 4) +
  theme_void() +
  theme(legend.position = "none")
d
{% endhighlight %}

![center](../figure/08/TiltonMiranda/unnamed-chunk-2-1.png)

The traditional way to save a plot is to start a device of the desired format, then call the plot and shut off the device.


{% highlight r %}
# PNG
png(filename = file.path(mt_dir, "dino.png"),
    width = 5, height = 4, units = "in", res = 800)
d
dev.off()
{% endhighlight %}



{% highlight text %}
## quartz_off_screen 
##                 3
{% endhighlight %}



{% highlight r %}
# PDF
pdf(file = file.path(mt_dir, "dino.pdf"),
    width = 5, height = 4)
d
dev.off()
{% endhighlight %}



{% highlight text %}
## quartz_off_screen 
##                 3
{% endhighlight %}



{% highlight r %}
# SVG
svg(filename = file.path(mt_dir, "dino.svg"),
    width = 5, height = 4)
d
dev.off()
{% endhighlight %}



{% highlight text %}
## quartz_off_screen 
##                 3
{% endhighlight %}

The package ggplot2 also provides the ggsave() function that saves plots in a number of formats.


{% highlight r %}
ggsave(plot = d, filename = file.path(mt_dir, "dino.png"), device = "png")
ggsave(plot = d, filename = file.path(mt_dir, "dino.pdf"), device = "pdf")
ggsave(plot = d, filename = file.path(mt_dir, "dino.svg"), device = "svg")
{% endhighlight %}

It seems that the SVG format is a bit slower than the pdf and png formats, but I don't otherwise notice a huge difference in quality.


#2)

**Create a sticker using the "magick" and "hexSticker" packages.**

### First sticker


{% highlight r %}
library(hexSticker)
library(magick)
if (!require("sysfonts")) {
  install.packages("sysfonts")
  library("sysfonts")
}

font <- "Cuprum"
font_add_google(font)
#Other font choices: "Amatic SC", "Quicksand", "Pathway Gothic One"

vgg_struct <- image_read("https://github.com/MirandaTilton/shoe_nnet/raw/master/shoe_images/logo_images/CoNNOR_structure_nolabel_bold.png")

st <- sticker(vgg_struct, package = "CoNNOR",
              filename = file.path(mt_dir, "CoNNOR.png"),
              p_size = 28, p_y = 1.5, p_color = "gray40", p_family = font,
              s_x = 1.1, s_y = .85, s_width = 1.6, s_height = 1.4,
              h_fill = "gray95", h_color = "cyan4", h_size = 1.5,
              spotlight = T)

# Display the image by loading the PNG (to fix font scaling issues)
s <- image_read(file.path(mt_dir, "CoNNOR.png")); s
{% endhighlight %}

![center](../figure/08/TiltonMiranda/unnamed-chunk-5-1.png)

### Second sticker

The shoe outline image was found [here](http://www.clker.com/cliparts/i/A/h/U/6/P/shoe-print.svg) and is also hosted [here](https://github.com/MirandaTilton/shoe_nnet/blob/master/shoe_images/logo_images/shoe-print.svg). The neuron background image was found [here](https://pixabay.com/p-2660914/?no_redirect) and is also hosted [here](https://github.com/MirandaTilton/shoe_nnet/blob/master/shoe_images/logo_images/neuron.jpg).


{% highlight r %}
# Function takes magick image and returns string of its dimensions
get_dim <- function(magick_img) {
  stopifnot(class(magick_img) == "magick-image")
  info <- image_info(magick_img)
  return(paste0(info$width, "x", info$height))
}

# Turn original SVG into png with white background
tmp <- image_read_svg("http://www.clker.com/cliparts/i/A/h/U/6/P/shoe-print.svg")
{% endhighlight %}



{% highlight text %}
## Error in loadNamespace(name): there is no package called 'rsvg'
{% endhighlight %}



{% highlight r %}
w <- image_info(tmp)$width
{% endhighlight %}



{% highlight text %}
## Error in assert_image(image): object 'tmp' not found
{% endhighlight %}



{% highlight r %}
h <- image_info(tmp)$height
{% endhighlight %}



{% highlight text %}
## Error in assert_image(image): object 'tmp' not found
{% endhighlight %}



{% highlight r %}
shoe <- image_flatten(c(tmp, image_blank(width = w, height = h))); shoe
{% endhighlight %}



{% highlight text %}
## Error in assert_image(image): object 'tmp' not found
{% endhighlight %}



{% highlight text %}
## Error in eval(expr, envir, enclos): object 'shoe' not found
{% endhighlight %}



{% highlight r %}
# Create mask to go over background image
shoe_outline <- shoe %>%
  image_canny() %>%
  image_negate() %>%
  image_fill("blue", paste0("+", w/6, "+", h/2)) %>%
  image_fill("blue", paste0("+", w*4/5, "+", h*2/5)) %>%
  image_transparent("blue") %>%
  image_scale("600x"); shoe_outline
{% endhighlight %}



{% highlight text %}
## Error in eval(lhs, parent, parent): object 'shoe' not found
{% endhighlight %}



{% highlight text %}
## Error in eval(expr, envir, enclos): object 'shoe_outline' not found
{% endhighlight %}



{% highlight r %}
# Read in background image
neuron <- image_read("https://github.com/MirandaTilton/shoe_nnet/raw/master/shoe_images/logo_images/neuron.jpg"); neuron
{% endhighlight %}

![center](../figure/08/TiltonMiranda/unnamed-chunk-6-1.png)

{% highlight r %}
# Crop background image to size of mask
bg <- neuron %>%
  image_crop(paste0(get_dim(shoe_outline),"+100+55")); bg
{% endhighlight %}



{% highlight text %}
## Error in class(magick_img) == "magick-image": object 'shoe_outline' not found
{% endhighlight %}



{% highlight text %}
## Error in eval(expr, envir, enclos): object 'bg' not found
{% endhighlight %}



{% highlight r %}
# Lay mask over background, rotate to horizontal, and remove white background
nn_shoe <- image_flatten(c(bg, shoe_outline)) %>%
  image_rotate(-11) %>%
  image_transparent("white"); nn_shoe
{% endhighlight %}



{% highlight text %}
## Error in assert_image(image): object 'bg' not found
{% endhighlight %}



{% highlight text %}
## Error in eval(expr, envir, enclos): object 'nn_shoe' not found
{% endhighlight %}


{% highlight r %}
st <- sticker(nn_shoe, package = "CoNNOR",
              filename = file.path(mt_dir, "CoNNOR2.png"),
              p_size = 30, p_y = 1.4, p_color = "gray40",
              p_family = font,
              s_x = 1, s_y = .8, 
              s_width = 1.6, s_height = 1.5,
              h_fill = "gray95", h_color = "aquamarine4", h_size = 1.8)
{% endhighlight %}



{% highlight text %}
## Error in sticker(nn_shoe, package = "CoNNOR", filename = file.path(mt_dir, : object 'nn_shoe' not found
{% endhighlight %}



{% highlight r %}
# Display the image by loading the PNG (to fix font scaling issues)
s <- image_read(file.path(mt_dir, "CoNNOR2.png")); s
{% endhighlight %}



{% highlight text %}
## Error in magick_image_readpath(path, density, depth, strip): Magick: UnableToOpenBlob `/Users/heike/Documents/Teaching/stat 585/Spring 2019/blog-2019/08/MirandaTilton_blog8/CoNNOR2.png': No such file or directory @ error/blob.c/OpenBlob/2761
{% endhighlight %}

![center](../figure/08/TiltonMiranda/unnamed-chunk-7-1.png)




