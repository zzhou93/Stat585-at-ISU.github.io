---
title: "It's magick!"
author: "Min Zhang"
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



Source: [95 VISUAL](https://www.95visual.com/blog/svg-pdf-jpg-png-whats-the-difference)

PNG: Portable Network Graphics, is used almost exclusively for images used on websites. Because of the size of a PNG file, this format is not recommended for photos as JPG is unless file size is not an issue. If you have a mixture of images that have line art and text, the PNG format will make the image look sharper instead of appearing bitmapped. The higher levels of PNG support transparency like GIFs do. This makes the PNG format suitable for web images like logos that you want to include transparency and fading effects too. There is only one PNG format, but it supports 5 color types. PNG-8 refers to palette variant, which supports only 256 colors; PNG-24 refers to true color variant, which supports more colors.

SVG: Scalable Vector Graphics, was developed to be used to represent an image and its elements, which may include objects, drawing, and figures in XML. This type of graphic file can be opened in any browser. SVG is used to create icons that are used on websites. An SVG image can be compressed or stretched without loss of image quality. This format suitable for web pages that are viewed on devices that have a high pixel density, like smartphones or tablets. You can edit the file in an editor to change graphic settings on a website when you use CSS. SVG image element files are smaller than if the image were present in a raster format. However, when using SVG, you need to remember that if an object in the image contains many small elements, the size of the file can grow very fast. A potential issue with SVG is that you cannot read only a part of the graphic object. The entire object must load and it could slow things down with your website.

PDF: Portable Document File, is a file format that can be used to provide an electronic image of text or text and graphic that looks the same as a printed document. A PDF file can be viewed, printed or electronically transmitted by uploading, downloading or attaching it to a message or email. The benefit of using a PDF format is that links can be embedded in the document and the file sizes are usually smaller than if you saved a document in its native format including its graphic files.

A summary table for comparison:


|                      |SVG |PDF |PNG-8 |PNG-24 |
|:---------------------|:---|:---|:-----|:------|
|Raster Image          |    |X   |X     |X      |
|Vector Image          |X   |X   |      |       |
|Small File Size       |X   |    |X     |       |
|High Quality          |X   |X   |      |X      |
|Compression           |X   |    |X     |X      |
|Supports CSS Editting |X   |    |      |       |
|Supports Text         |X   |X   |X     |X      |
|Images                |    |    |      |X      |
|Graphics              |X   |    |X     |X      |
|Transparency          |    |    |X     |X      |
|Layers                |X   |X   |      |       |
|Used in Print         |    |X   |      |       |
|Used in Web           |X   |X   |X     |X      |


{% highlight r %}
amr.png <- image_read("https://minzhang95.github.io/images/amr1.png")
amr.pdf <- image_convert(amr.png, "pdf")
amr.svg <- image_convert(amr.png, "svg")
# image_write(amr.png, path = "amr_png.png", format = "png") # 41 KB
# image_write(amr.pdf, path = "amr_pdf.pdf", format = "pdf") # 29 KB
# image_write(amr.svg, path = "amr_svg.svg", format = "svg") # 56 KB
cmpformat <- rbind(image_info(amr.png), image_info(amr.pdf), image_info(amr.svg))
cmpformat %>% knitr::kable(caption = "Comparison of image_info of SVG, PDF, and PNG")
{% endhighlight %}



|format | width| height|colorspace |matte | filesize|density |
|:------|-----:|------:|:----------|:-----|--------:|:-------|
|PNG    |   630|    330|sRGB       |TRUE  |    24878|38x38   |
|PDF    |   630|    330|sRGB       |TRUE  |        0|38x38   |
|SVG    |   630|    330|sRGB       |TRUE  |        0|38x38   |

Comments: While using the three image formats, I noticed that PDF is friendly to printing. In terms of size, PDF is smaller than PNG, and PNG is smaller than SVG.


2. **Use `magick` functionality to create an image to be used for a hex sticker.**  package `hexSticker` can help you to get started on dimensions of the sticker. **Include all code necessary to produce your sticker.** In case you are using local images, post those in a folder on **your** website and use the URL to link to them.


{% highlight r %}
# Read data
email_campaign_funnel <- read.csv("https://raw.githubusercontent.com/selva86/datasets/master/email_campaign_funnel.csv")

# X Axis Breaks and Labels 
brks <- seq(-15000000, 15000000, 5000000)
lbls = paste0(as.character(c(seq(15, 0, -5), seq(5, 15, 5))), "m")

# Plot
p <- ggplot(email_campaign_funnel, aes(x = Stage, y = Users, fill = Gender)) +  
  geom_bar(stat = "identity", width = .6) + 
  coord_flip() + 
  theme_tufte() + 
  theme(plot.title = element_blank(), axis.title = element_blank(), 
        axis.text = element_blank(), axis.ticks = element_blank(), 
        legend.position = "none") + 
  scale_fill_brewer(palette = "Dark2")
s <- sticker(p, package = "AdsFunnel", p_size=18, p_color = "#f39c12",
             s_x=1, s_y=1.05, s_width=1.2, s_height = 1.6, 
             h_fill="#FFFFFF", h_color="#f39c12")
s
{% endhighlight %}

![center](./../figure/08/ZhangMin/unnamed-chunk-4-1.png)
