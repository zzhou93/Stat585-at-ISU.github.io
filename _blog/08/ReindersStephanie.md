---
title: "I made a sticker!"
author: "Stephanie Reinders"
topic: "08"
layout: post
root: ../../../
---

## Image Formats

1. **Describe the difference between formats png, svg, and pdf. State your sources with (working!) links (take a look at the RMarkdown cheatsheet for RStudio to learn how to make working links). Make one plot in ggplot2 and save it (using R code) in each of the three file formats you discussed. Comment on the differences you observe in their usage.**

### Raster versus Vector 
[here](https://www.printcnx.com/resources-and-support/addiational-resources/raster-images-vs-vector-graphics/)

Before discussing particular digital image file formats, I would like to discuss the two main types of digital images: raster and vector. 

A raster image consists of a matrix where each entry of the matrix represents a pixel and each pixel has a color value. One way to think about this is that a raster image represents a picture as a collection of tiny dots or squares of color. If you zoom in close enough on a raster image, you can even see the individuals squares of color. Raster images can lose quality if they are resized too much. 

A vector image, instead of storing pixel values, stores geometric shapes such as lines and rectangles. Each shape has a color associated with it. Vector images work well for simpler pictures like illustrastions and logos, and they scale extremely well. 


### PNG
The Portable Network Graphics (PNG) file format is a raster image format. It is a lossless format which means that an image doesn't lose any of its original pixel information if it is saved as a PNG. The PNG format was created as an improvement to the GIF format and intended for use on the internet, not print. The PNG format uses RGB, or grayscale color pallettes, but not CMYK, which is a color pallette typically used in print. 

[source](https://en.wikipedia.org/wiki/Portable_Network_Graphics)

### SVG

The Scalable Vector Graphics (SVG) file format images can contain vector image shapes, raster images, and text. The file format also allows animation. 

[source](https://en.wikipedia.org/wiki/Scalable_Vector_Graphics)

### PDF
The Portable Document Format (PDF) was created so as a universal format that could be viewed on any software, hardware or operating system. A PDF file can contain text, raster images, and vector images. 

[source](https://en.wikipedia.org/wiki/PDF)

### TIFF
TIFF stands for Tagged Image File Format. TIFF is a raster format. TIFF can be lossless or lossy. Lossy means that some of the original image information is not stored in order to make the file size smaller. Unlike the PNG file format, the TIFF format is often used in print. 

[source 1](https://en.wikipedia.org/wiki/TIFF)
[source 2](https://www.peernet.com/image-format-guide/)

### JPEG
JPEG is arguably the most widely used digital image file format. It is a raster image format. JPEG images use lossy compression, which means that some of the original image information is not stored in order to make the file size smaller. I learned from the CSAFE Steganography Project that the native camera apps on both Androids and iPhones save images in the JPEG format.  

[source](https://www.peernet.com/image-format-guide/)

### Comparing Plots



This plot is actually a plot I made for a conference paper. I initally used the JPEG image in the LaTex document, but the image quality was poor. I replaced the JPEG image with the PDF image in the paper and the quality was great. I didn't create a SVG image for the paper, but I did for this exercise. The SVG image has the largest file size of the three file formats, at 199 kb (this is still a really small file though). When I double click on the SVG image, my computer tries to open it in LaTex. Weird. If I open the image in Safari, the image displays, but it is poor quality. 


2. **Use `magick` functionality to create an image to be used for a hex sticker.**  package `hexSticker` can help you to get started on dimensions of the sticker. **Include all code necessary to produce your sticker.** In case you are using local images, post those in a folder on **your** website and use the URL to link to them.


{% highlight r %}
library(magick)
library(hexSticker)

raspberry <- image_read(knitr::include_graphics('https://stephaniereinders.github.io/Images/Raspberry.JPG'))

sticker(raspberry, package="Rasberry",filename="Raspberry.png",p_size=8, s_x=1, s_y=.8, s_width=1.2, s_height=1)
{% endhighlight %}
