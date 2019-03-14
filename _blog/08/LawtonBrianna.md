---
title: "Blog 8: It's magick!"
author: "Brianna Lawton"
topic: "08"
layout: post
root: ../../../
---

Write a blog post answering the following questions and detailing the progress: 

1. **Describe the difference between formats png, svg, and pdf. State your sources with (working!) links (take a look at the RMarkdown cheatsheet for RStudio to learn how to make working links). Make one plot in ggplot2 and save it (using R code) in each of the three file formats you discussed. Comment on the differences you observe in their usage.**

## PNG
PNG stands for Portable Network Graphics. 
PNG was created to improve GIF image-file formats; removing copyright and patent license permissions and removing 256 color limitations. PNGs are high quality raster/pixel-based file formats. Some advanatages about PNGs is that it is a widely accepted image format, its "lossless" quality and ability to change the degree of transparency. Some disadvantages about PNGs is that it has more complex and larger image files can be large, only supports web colors (RGB), and limited compatibility. PNG files are not grainy or blurred when you upload or use them. To export a PNG properly, its good to make sure the file dimensions are large enough and the resolution is set to at least 300 dpi (dots per inch). Another perk about PNGs is their sharp image quality and small file size; they allow 5-25% more compression. PNGs also support image [interlacing](https://graphicdesign.stackexchange.com/questions/6677/what-does-the-interlaced-option-in-photoshop-do). PNGs are commonly used for icons, simple web graphics like logos, illustrations, or raster text and chart rendering. Browsers that support PNG formating w/o plug-ins are Internet Explorer, Opera, Safari, Google Chrome, & Firefox.

## SVG
SVG stands for Scalable Vector Graphics
SVG is an XML based file format, which can be edited with any text editor. SVGs are vector-based images that can be scaled infinitely without pixelation. A vector image file consists of lines that never get pixelated and is able to be scaled to any size. SVGs allow creation of very high quality graphics and animations that do not lose detail as their size increases or decreases. SVGs are also good for cross-device quality control. Some pros about SVGs is their ability to expand infinitely without quality loss, can be edited with a text editor, "lossless" quality, and its animation, transparency, and layer support. A drawback of SVGs are their unpurposed intentions to be printed. SVGs are amazing file types for websites and commonly used for scalable graphics. This file type can be used for graphic iconic elements on websites. SVGs are extremely lightweight for file size--usually less than a kilobyte; which allows it to load faster. Browsers that support SVGs w/o a plug-in are Internet Explorer, Opera, Safari, Google Chrome, & Firefox. 

## PDF
PDf stands for Portable Document Format. 
PDF is a file format used to present documents in a manner independent of application software, hardware, and operating systems. Each PDF file encapsulates a complete description of a fixed-layout flat document, including the text, fonts, graphics, and other information needed to display it. PDFs are also vector-based files with high print quality and more flexibility. PDFs were made to capture and review rich information from any application, on any computer, with anyone/anywhere. PDF's "lossless" quality, protection of intellectual property, and maintenance of its printed format are some of the reasons why its considered one of the best universal tools for sharing graphics. Some disadvantages are longer browser loading times, non-editable content, not great for complex graphics printing, and not really useful as a graphic image. An individual also needs a license from Adobe to use PDF. PDFs are commonly used for logos, marketing materials, and fixed layout flat documents. Browsers that support PDF w/o plug-in are Internet Explorer, Opera, Google Chrome, & Firefox.

#Sources Referenced

[Common Image File Formats](http://socialcompare.com/en/comparison/image-file-formats)
[The File Guide](https://builtbytophat.com/file-guide-differences-between-jpg-png-eps-pdf-psd-ai-gif-tiff/)
[10 Types of Image File Extensions and When to Use Them](https://blog.hubspot.com/insiders/different-types-of-image-files)
[Image Formats](https://www.practicalecommerce.com/Image-Formats-What-s-the-Difference-Between-JPG-GIF-PNG)
[Differences Between File Formats](https://www.photoup.net/differences-between-file-formats-raw-dng-tiff-gif-png-jpeg/)
[Image Formats Compared](https://www.aivosto.com/articles/imageformats.html)


{% highlight r %}
library(dplyr)
library(ggplot2)

travel_modes <- read.csv("C:/Users/lawto/Desktop/Spring2019/CE557/mini-project-2/MODEBIN3.csv")
{% endhighlight %}



{% highlight text %}
## Warning in file(file, "rt"): cannot open file 'C:/Users/lawto/Desktop/
## Spring2019/CE557/mini-project-2/MODEBIN3.csv': No such file or directory
{% endhighlight %}



{% highlight text %}
## Error in file(file, "rt"): cannot open the connection
{% endhighlight %}



{% highlight r %}
View(travel_modes)
{% endhighlight %}



{% highlight text %}
## Error in View : object 'travel_modes' not found
{% endhighlight %}



{% highlight r %}
#head(travel_modes) #check out data
#nrow(travel_modes) #number of rows
#length(unique(travel_modes$PERSID)) #how many individuals?
#table(is.na(travel_modes)) #is there any missing data

travel_modes %>% 
  ggplot(aes(x= AGE, y= TOTCOST, color=MODE)) +
  geom_point() +
  facet_wrap(~MODE)
{% endhighlight %}



{% highlight text %}
## Error in eval(lhs, parent, parent): object 'travel_modes' not found
{% endhighlight %}



{% highlight r %}
#travel_modes %>% ggplot(aes(x = AGE, y = TOTCOST, colour = `MODE`)) + geom_point() + geom_line(aes(group = `MODE`))

ggsave("travel.pdf", width = 4, height = 4)

# This will save a 400x400 file at 300 ppi
ggsave("travel.png", width = 4, height = 4, dpi = 300)

ggsave("travel.svg")
{% endhighlight %}



{% highlight text %}
## Saving 7 x 7 in image
{% endhighlight %}
## Different Formats for the same ggplot2 image
Although, the size of the file is different. All three formats of the image look the same to me; not sure if thats correct. 


{% highlight r %}
knitr::include_graphics("https://brlaw17.github.io/travel.svg")
{% endhighlight %}

![center](./https://brlaw17.github.io/travel.svg)

{% highlight r %}
knitr::include_graphics("https://brlaw17.github.io/travel.pdf")
{% endhighlight %}

![center](./https://brlaw17.github.io/travel.pdf)

{% highlight r %}
knitr::include_graphics("https://brlaw17.github.io/travel.png")
{% endhighlight %}

![center](./https://brlaw17.github.io/travel.png)

2. **Use `magick` functionality to create an image to be used for a hex sticker.**  package `hexSticker` can help you to get started on dimensions of the sticker. **Include all code necessary to produce your sticker.** In case you are using local images, post those in a folder on **your** website and use the URL to link to them.


{% highlight r %}
library(magick)
library(hexSticker)

#str(magick::magick_config())

#import image in fron my 
pisa <- image_read("https://brlaw17.github.io/leaning_tower_pisa.JPG")
print(pisa)
{% endhighlight %}



{% highlight text %}
## # A tibble: 1 x 7
##   format width height colorspace matte filesize density
##   <chr>  <int>  <int> <chr>      <lgl>    <int> <chr>  
## 1 JPEG    3024   4032 sRGB       FALSE  2793400 72x72
{% endhighlight %}

![center](./../figure/08/LawtonBrianna/unnamed-chunk-3-1.png)

{% highlight r %}
#convert image format from JPG to PNG
pisa_png <- image_convert(pisa, "png")
image_info(pisa_png)
{% endhighlight %}



{% highlight text %}
## # A tibble: 1 x 7
##   format width height colorspace matte filesize density
##   <chr>  <int>  <int> <chr>      <lgl>    <int> <chr>  
## 1 PNG     3024   4032 sRGB       FALSE        0 72x72
{% endhighlight %}



{% highlight r %}
#scale image down
image_scale(pisa, "x400") # height: 300px
{% endhighlight %}

![center](./../figure/08/LawtonBrianna/unnamed-chunk-3-2.png)

{% highlight r %}
sticker(pisa, package = "Brianna's hexSticker",  p_size=8, s_x=1, s_y=.75, s_width=1.3, s_height=1,
        filename="pisa.png")
{% endhighlight %}

## Check out my sticker! 


{% highlight r %}
knitr::include_graphics("https://brlaw17.github.io/pisa.png")
{% endhighlight %}

![center](./https://brlaw17.github.io/pisa.png)
