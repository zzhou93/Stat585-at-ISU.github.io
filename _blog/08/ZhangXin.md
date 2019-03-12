
---
title: "It's magick!"
author: "Xin Zhang"
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

I find the material in the following links: 

[Solved - Best Image Format for the Web? PNG, JPG, GIF, and SVG.](https://www.pagecloud.com/blog/web-images-png-vs-jpg-vs-gif-vs-svg)

[SVG, PDF, JPG, PNG; WHAT'S THE DIFFERENCE?](https://www.95visual.com/blog/svg-pdf-jpg-png-whats-the-difference)

[PDF: wikipedia](https://en.wikipedia.org/wiki/PDF)

[PNG: wikipedia](https://en.wikipedia.org/wiki/Portable_Network_Graphics)

[SVG: wikipedia](https://en.wikipedia.org/wiki/Scalable_Vector_Graphics)

[SVG vs. PNG, Which is the Best in 2017?](https://blog.mrdaniels.ch/warz/png-vs-svg-2017/)

[JPG vs PNG vs PDF: Which File Format Should You Use?](https://www.shutterstock.com/blog/jpg-vs-png-vs-pdf)

- PNG: short for Portable Network Graphics, was invented in 1995.  PNG use lossless compression of data. The format compress the images so that you will not be able to detect degradation of quality. PNG file can support both 8-bit or 24-bit colors, using a lossless compression approach.

- SVG: known as Scalable Vector Graphics, is a vector image file format released in 2001. SVG is an XML-based vector image format for two-dimensional graphics with support for interactivity and animation. The SVG images can be searched, indexed, scripted, and compressed. As XML files, SVG images can be created and edited with any text editor, as well as with drawing software.

- PDF: Portable Document File, is a file format developed by Adobe in the 1990s. The PDF file can be viewed, printed or electronically transmitted by uploading, downloading or attaching it to a message or email. The advantage of the PDF format is that links can be embedded in the document and the file sizes are usually smaller than if you saved a document in its native format including its graphic files.

The rule to choose PNG or SVG or PDF:  

1). If the image has vector artefacts that are easy to scale, SVG is a good choice. Plus, SVG can be exported as code, meaning you can use CSS or JavaScript to edit the image dynamically.

2). PDF is a good format for printing, especially for graphic design, posters, and flyers. PDF images are also an ideal choice for storing images online for being downloaded. 

3). PNG images are ideal for web graphics, especially logos, illustrations, and graphs. They can shrink to very small file sizes when colors and elements are limited. Also, PNG can be fully transparent, allowing you to place illustrations and designs atop backgrounds effortlessly.






