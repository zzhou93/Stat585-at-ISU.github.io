---
title: "It's magick!"
author: "Xiyuan Sun"
topic: "08"
layout: post
root: ../../../
---


Write a blog post answering the following questions and detailing the progress: 

1. **Describe the difference between formats png, svg, and pdf. State your sources with (working!) links (take a look at the RMarkdown cheatsheet for RStudio to learn how to make working links). Make one plot in ggplot2 and save it (using R code) in each of the three file formats you discussed. Comment on the differences you observe in their usage.**

source: [image file formats](https://www.95visual.com/blog/svg-pdf-jpg-png-whats-the-difference)

-png: Portable Network Graphics

The PNG format is an open format that was created as an alternative to the GIF format, which required a licensing fee through the company that held a patent for the format. The PNG format offers a better quality graphic than a GIF with better compression and a wider range of color without loss of detail. Most newer browsers can view PNG formats without any problems.

PNG is used almost exclusively for images used on websites. Because of the size of a PNG file, this format is not recommended for photos as JPG is unless file size is not an issue. If you have a mixture of images that have line art and text, the PNG format will make the image look sharper instead of appearing bitmapped. The higher levels of PNG support transparency like GIFs do. This makes the PNG format suitable for web images like logos that you want to include transparency and fading effects too.

It is not unusual to have a mixture of formats of graphics for your various graphic elements because each format has its advantages and disadvantages of when it should be used dependent on your goals for your website.

-svg: Scalable Vector Graphics

The SVG graphic format was developed to be used to represent an image and its elements, which may include objects, drawings, and figures in XML.

This type of graphic file can be opened in any browser. SVG is used to create icons that are used on websites. An SVG image can be compressed or stretched without loss of image quality.

This format suitable for web pages that are viewed on devices that have a high pixel density, like smartphones or tablets. You can edit the file in an editor to change graphic settings on a website when you use CSS.

SVG image element files are smaller than if the image were present in a raster format. However, when using SVG, you need to remember that if an object in the image contains many small elements, the size of the file can grow very fast. A potential issue with SVG is that you cannot read only a part of the graphic object.

The entire object must load and it could slow things down with your website.

-pdf: Portable Document File 

Developed by Adobe, PDF is a file format that can be used to provide an electronic image of text or text and graphic that looks the same as a printed document. A PDF file can be viewed, printed or electronically transmitted by uploading, downloading or attaching it to a message or email. The benefit of using a PDF format is that links can be embedded in the document and the file sizes are usually smaller than if you saved a document in its native format including its graphic files.

PDF files adhere to ISO 32000 standards for electronic document exchange. PDF files can be password protected to restrict access and prevent copying or tampering. They can also be used in instances where a legally binding electronic signature is needed. PDF files can be viewed by all browsers with the help of a plug-in.


{% highlight r %}
saveImg <- function(f, p) {f(paste0("plot.", substitute(f))); suppressMessages(print(p)); dev.off(); invisible()}
p <- ggplot2::qplot(mpg, wt, data = mtcars, geom = c("point"))
saveImg(png, p)
saveImg(svg, p)
saveImg(pdf, p)
{% endhighlight %}

It does not show on the web page. 

2. **Use `magick` functionality to create an image to be used for a hex sticker.**  package `hexSticker` can help you to get started on dimensions of the sticker. **Include all code necessary to produce your sticker.** In case you are using local images, post those in a folder on **your** website and use the URL to link to them.


{% highlight r %}
library(magick)
library(hexSticker)
library(dplyr)

image <- image_read("https://ridleylibrary.org/wp-content/uploads/2018/10/cropped-Ridley-Twp-Library-Logo-Final-1.jpg") %>%
  image_fill("#2CA8FF",fuzz=20) %>%
  image_transparent("#2CA8FF")

sticker <- sticker(image,package="csafe",p_size=25, p_color="white",p_y=1.6,s_x=1,s_y=.85, s_width=1.3,s_height = 1.4,h_fill="#2CA8FF",h_color="#4a8eff")
sticker
{% endhighlight %}

![center](./../figure/08/XiyuanSun/unnamed-chunk-1-1.png)








