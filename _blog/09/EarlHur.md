<<<<<<< HEAD
1.  The `xml2` R package can be used to work with xml files. Write a
    function, `current_weather` that accepts a 4-letter airport code
    (KAMW in the URL here:
    <a href="https://w1.weather.gov/xml/current_obs/KAMW.xml" class="uri">https://w1.weather.gov/xml/current_obs/KAMW.xml</a>)
    and returns a data frame with the airport location (station ID,
    latitude, longitude), last update time, and current weather
    information (temperature, weather condition, wind speed and
    direction) at that airport. The `xml2` functions `read_xml`,
    `xml_children`, `xml_name`, and `xml_text` will be useful. Remember
    to handle errors and check inputs, and make sure to return a data
    frame with appropriate data types.

<!-- -->

    library(xml2)
    library(tidyverse)
    library(checkmate)
    library(knitr)

    current_weather <- function(code){
      checkmate::assertCharacter(code)
      url <- "https://w1.weather.gov/xml/current_obs/"

      weather_url <- read_xml(paste0(url, code, ".xml"))
      
      weather_all <- xml_text(xml_children(weather_url))[c(7,8,9,13,12,20,18)]

      weatherDat <- data.frame(stationID = weather_all[1],
                               latitude = weather_all[2],
                               longitude = weather_all[3],
                               temperature = weather_all[4],
                               weather = weather_all[5],
                               wind_speed = weather_all[6],
                               wind_direction = weather_all[7])
      
      checkmate::assert_data_frame(weatherDat, min.rows = 1)
      
      kable(weatherDat)
    }

    current_weather("KAMW")

<table>
<thead>
<tr class="header">
<th style="text-align: left;">stationID</th>
<th style="text-align: left;">latitude</th>
<th style="text-align: left;">longitude</th>
<th style="text-align: left;">temperature</th>
<th style="text-align: left;">weather</th>
<th style="text-align: left;">wind_speed</th>
<th style="text-align: left;">wind_direction</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: left;">KAMW</td>
<td style="text-align: left;">41.99056</td>
<td style="text-align: left;">-93.61889</td>
<td style="text-align: left;">39.0 F (3.9 C)</td>
<td style="text-align: left;">Mostly Cloudy</td>
<td style="text-align: left;">10.4</td>
<td style="text-align: left;">Northwest</td>
</tr>
</tbody>
</table>

1.  Which HTML tags did you investigate? Describe how to format at least
    3 separate pieces of a document using HTML tags.

<p style="font-size:20px;">
The first tag that I was investigated was image. The format of attaching
an image is shown below as:
</p>
&lt;img src=“image url or path of image file” alt=“name of the image”
width=“width of image” height=“height of image”&gt;
=======
---
title: "Blog 9: A Series of Tubes..."
author: "Earl Hur"
topic: "09"
layout: post
root: ../../../
output: 
  html_document: 
    css: extra.css
    fig_caption: yes
---

1. The `xml2` R package can be used to work with xml files. Write a function, `current_weather` that accepts a 4-letter airport code (KAMW in the URL here: https://w1.weather.gov/xml/current_obs/KAMW.xml) and returns a data frame with the airport location (station ID, latitude, longitude), last update time, and current weather information (temperature, weather condition, wind speed and direction) at that airport. The `xml2` functions `read_xml`, `xml_children`, `xml_name`, and `xml_text` will be useful. Remember to handle errors and check inputs, and make sure to return a data frame with appropriate data types.


```r
library(xml2)
library(tidyverse)
library(checkmate)
library(knitr)
```


```r
current_weather <- function(code){
  checkmate::assertCharacter(code)
  url <- "https://w1.weather.gov/xml/current_obs/"

  weather_url <- read_xml(paste0(url, code, ".xml"))
  
  weather_all <- xml_text(xml_children(weather_url))[c(7,8,9,13,12,20,18)]

  weatherDat <- data.frame(stationID = weather_all[1],
                           latitude = weather_all[2],
                           longitude = weather_all[3],
                           temperature = weather_all[4],
                           weather = weather_all[5],
                           wind_speed = weather_all[6],
                           wind_direction = weather_all[7])
  
  checkmate::assert_data_frame(weatherDat, min.rows = 1)
  
  kable(weatherDat)
}

current_weather("KAMW")
```



|stationID |latitude |longitude |temperature     |weather  |wind_speed |wind_direction |
|:---------|:--------|:---------|:---------------|:--------|:----------|:--------------|
|KAMW      |41.99056 |-93.61889 |54.0 F (12.2 C) |Overcast |9.2        |South          |

2. Which HTML tags did you investigate? Describe how to format at least 3 separate pieces of a document using HTML tags.

<p style="font-size:20px;">The first tag that I was investigated was image. The format of attaching an image is shown below as:</p>

\<img src="image url or path of image file" alt="name of the image" width="width of image" height="height of image">
>>>>>>> blog 9 posts up

Example Image:

<img src="https://assets.atlasobscura.com/media/W1siZiIsInVwbG9hZHMvcGxhY2VfaW1hZ2VzL2RlOTI0ODAxYTJiYjg0NjI2Y18xMDc2OTI4NDg4NV83NzJjZmEzODQxX28uanBnIl0sWyJwIiwidGh1bWIiLCIxMjAweD4iXSxbInAiLCJjb252ZXJ0IiwiLXF1YWxpdHkgODEgLWF1dG8tb3JpZW50Il1d" alt="Blue Mustang" width="500" height="600">

<<<<<<< HEAD
<p style="font-size:20px;">
The second tag was symbols.
<p style="font-size:20px;">
This would be very useful if I want to post an html file with
mathematical notations such as,
</p>
&lt;p&gt;Summation: &sum;
<p>
Summation: ∑

&lt;p&gt;Product: &prod;
<p>
Product: ∏

&lt;p&gt;Element of: &isin;
<p>
Element of: ∈

&lt;p&gt;Integral: &int;
<p>
Integral: ∫

<p style="font-size:20px;">
The last one was colors and the format was:
</p>
&lt;p style=“background-color:Tomato;:Tomato;”&gt;
<p style="background-color:Tomato;:Tomato;">
Stat585, Blog 9 (This is background color)
</p>
&lt;p style=“color:DodgerBlue;”&gt;
<p style="color:DodgerBlue;">
We can do many things using HTML!!! (This is paragraph color)
</p>
1.  Compile this Rmarkdown document to HTML, then open the HTML file in
    a web browser. Open the inspector console for your browser
    (Ctrl-Shift-I in Chrome, Ctrl-Shift-C in Firefox) and look at the
    HTML code corresponding to various parts of the document. Answer the
    following questions:

    What types of tags did you find? &lt;html&gt; &lt;head&gt;
    &lt;body&gt; &lt;style&gt; &lt;script&gt;

    How are code chunks formatted in HTML? The code chunk is in the
    &lt;div class=“container-fluid main-container&gt; with the tag as
    &lt;pre class=”r"&gt;

    What differences are there in the HTML markup for R code chunks and
    R output blocks? The output from the code chunk of the first
    question is shown in the &lt;class=“table table-condensed”&gt;

2.  In R, the rvest package, which is part of the tidyverse, makes it
    (relatively) easy to pull specific pieces from structured documents.
    The html\_nodes function selects nodes using either xpath or css,
    and additional functions such as html\_attrs, html\_text, and
    html\_table pull information out of the markup text. Choose a
    Wikipedia page that has at least one image to test the rvest package
    out

Link chosen:
<a href="https://en.wikipedia.org/wiki/Denver_Broncos" class="uri">https://en.wikipedia.org/wiki/Denver_Broncos</a>

    library(rvest)

    broncos <- read_html("https://en.wikipedia.org/wiki/Blue_Mustang")

    broncos_attr <- broncos %>% html_nodes("img") %>%
      html_attr(name = "src")

    broncos_attr[[1]]

    ## [1] "//upload.wikimedia.org/wikipedia/en/thumb/9/90/Blucifer_Sculpture.png/200px-Blucifer_Sculpture.png"

    image_link <-broncos_attr[[1]] %>%
      paste0("https:", .)
    knitr::include_graphics(image_link)

![](https://upload.wikimedia.org/wikipedia/en/thumb/9/90/Blucifer_Sculpture.png/200px-Blucifer_Sculpture.png)
=======
<p style="font-size:20px;">The second tag was symbols. 
<p style="font-size:20px;">This would be very useful if I want to post an html file with mathematical notations such as,</p>

\<p>Summation: \&sum;
<p>Summation: &sum;

\<p>Product: \&prod;
<p>Product: &prod;

\<p>Element of: \&isin;
<p>Element of: &isin;

\<p>Integral: \&int;
<p>Integral: &int;

<p style="font-size:20px;">The last one was colors and the format was:</p>
\<p style="background-color:Tomato;:Tomato;">
<p style="background-color:Tomato;:Tomato;">Stat585, Blog 9 (This is background color)</p>
\<p style="color:DodgerBlue;">
<p style="color:DodgerBlue;">We can do many things using HTML!!! (This is paragraph color)</p>

3. Compile this Rmarkdown document to HTML, then open the HTML file in a web browser. Open the inspector console for your browser (Ctrl-Shift-I in Chrome, Ctrl-Shift-C in Firefox) and look at the HTML code corresponding to various parts of the document. 
Answer the following questions:

    What types of tags did you find?
    \<html>
    \<head>
    \<body>
    \<style>
    \<script>

    How are code chunks formatted in HTML?
    The code chunk is in the \<div class="container-fluid main-container> with the tag as \<pre class="r">
    
    What differences are there in the HTML markup for R code chunks and R output blocks?
    The output from the code chunk of the first question is shown in the \<class="table table-condensed">
    
4. In R, the rvest package, which is part of the tidyverse, makes it (relatively) easy to pull specific pieces from structured documents. The html_nodes function selects nodes using either xpath or css, and additional functions such as html_attrs, html_text, and html_table pull information out of the markup text.
Choose a Wikipedia page that has at least one image to test the rvest package out

Link chosen: https://en.wikipedia.org/wiki/Denver_Broncos

```r
library(rvest)

broncos <- read_html("https://en.wikipedia.org/wiki/Blue_Mustang")

broncos_attr <- broncos %>% html_nodes("img") %>%
  html_attr(name = "src")

broncos_attr[[1]]
```

```
## [1] "//upload.wikimedia.org/wikipedia/en/thumb/9/90/Blucifer_Sculpture.png/200px-Blucifer_Sculpture.png"
```

```r
image_link <-broncos_attr[[1]] %>%
  paste0("https:", .)
knitr::include_graphics(image_link)
```

![center](./https://upload.wikimedia.org/wikipedia/en/thumb/9/90/Blucifer_Sculpture.png/200px-Blucifer_Sculpture.png)


>>>>>>> blog 9 posts up
