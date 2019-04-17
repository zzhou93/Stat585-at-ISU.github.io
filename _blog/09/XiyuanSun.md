<<<<<<< HEAD
**Write a blog post answering the following questions and detailing the
progress: **

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
    library(assertthat)
    #write a function current_weather
    #that accepts a 4-letter airport code
    #and returns a data frame with 
    #(1) the airport location (station ID, latitude, longitude)
    #(2) last update time
    #(3) current weather information (temperature, weather condition, wind speed and direction)

    current_weather <- function(code) {
      assert_that(is.character(code), nchar(code)==4, msg="Code is not a 4 letter char")
      
      url <- paste0("https://w1.weather.gov/xml/current_obs/", code, ".xml")
      xml <- read_xml(url)
      nodeset <- xml %>% xml_children 
      name <- nodeset %>% xml_name
      content <- nodeset %>% xml_text
      dat <- as.data.frame(matrix(content, ncol = length(content), byrow = T), stringsAsFactors = F)
      colnames(dat) <- name
      res <- dat %>% dplyr::select(station_id, latitude, longitude,
        observation_time, weather, temperature_string, wind_dir, wind_mph)
      
      checkmate::checkDataFrame(res)
      return(res)
    }

    #test it
    current_weather("KAMW")

    ##   station_id latitude longitude                         observation_time
    ## 1       KAMW 41.99056 -93.61889 Last Updated on Apr 2 2019, 10:53 am CDT
    ##         weather temperature_string  wind_dir wind_mph
    ## 1 Mostly Cloudy     39.0 F (3.9 C) Northwest     10.4

    current_weather("KSTP")

    ##   station_id latitude longitude                         observation_time
    ## 1       KSTP 44.93237 -93.05588 Last Updated on Apr 2 2019, 10:53 am CDT
    ##         weather temperature_string  wind_dir wind_mph
    ## 1 Mostly Cloudy     41.0 F (5.0 C) Southwest     11.5

1.  Which HTML tags did you investigate? Describe how to format at least
    3 separate pieces of a document using HTML tags.
=======
---
title: "A Series of Tubes..."
author: "Xiyuan Sun"
topic: "09"
layout: post
root: ../../../
output: 
  html_document: 
    css: extra.css
    fig_caption: yes
---

**Write a blog post answering the following questions and detailing the progress: **

1. The `xml2` R package can be used to work with xml files. Write a function, `current_weather` that accepts a 4-letter airport code (KAMW in the URL here: https://w1.weather.gov/xml/current_obs/KAMW.xml) and returns a data frame with the airport location (station ID, latitude, longitude), last update time, and current weather information (temperature, weather condition, wind speed and direction) at that airport. The `xml2` functions `read_xml`, `xml_children`, `xml_name`, and `xml_text` will be useful. Remember to handle errors and check inputs, and make sure to return a data frame with appropriate data types. 


```r
library(xml2)
library(tidyverse)
library(assertthat)
#write a function current_weather
#that accepts a 4-letter airport code
#and returns a data frame with 
#(1) the airport location (station ID, latitude, longitude)
#(2) last update time
#(3) current weather information (temperature, weather condition, wind speed and direction)

current_weather <- function(code) {
  assert_that(is.character(code), nchar(code)==4, msg="Code is not a 4 letter char")
  
  url <- paste0("https://w1.weather.gov/xml/current_obs/", code, ".xml")
  xml <- read_xml(url)
  nodeset <- xml %>% xml_children 
  name <- nodeset %>% xml_name
  content <- nodeset %>% xml_text
  dat <- as.data.frame(matrix(content, ncol = length(content), byrow = T), stringsAsFactors = F)
  colnames(dat) <- name
  res <- dat %>% dplyr::select(station_id, latitude, longitude,
    observation_time, weather, temperature_string, wind_dir, wind_mph)
  
  checkmate::checkDataFrame(res)
  return(res)
}

#test it
current_weather("KAMW")
```

```
##   station_id latitude longitude                         observation_time
## 1       KAMW 41.99056 -93.61889 Last Updated on Apr 3 2019, 12:53 pm CDT
##    weather temperature_string wind_dir wind_mph
## 1 Overcast    54.0 F (12.2 C)    South      9.2
```

```r
current_weather("KSTP")
```

```
##   station_id latitude longitude                         observation_time
## 1       KSTP 44.93237 -93.05588 Last Updated on Apr 3 2019, 12:53 pm CDT
##   weather temperature_string wind_dir wind_mph
## 1    Fair     46.0 F (7.8 C)     West      8.1
```


2. Which HTML tags did you investigate? Describe how to format at least 3 separate pieces of a document using HTML tags.
>>>>>>> blog 9 posts up

Colors

<!--html_preserve-->
<<<<<<< HEAD
<h1 style="background-color:rgb(60, 19, 110);color:Yellow;border:10px dashed #F10909">
Smokey is a cat.
</h1>
<!--/html_preserve-->
=======
<h1 style="background-color:rgb(60, 19, 110);color:Yellow;border:10px dashed #F10909">Smokey is a cat.</h1>
<!--/html_preserve-->

>>>>>>> blog 9 posts up
Table

<!--html_preserve-->
<table style="width:50%">
<<<<<<< HEAD
<tr>
<th>
Language
</th>
<th>
Interests
</th>
</tr>
<tr>
<td>
English
</td>
<td>
Natural Language Processing.
</td>
</tr>
<tr>
<td>
Spanish
</td>
<td>
Procesamiento natural del lenguaje.
</td>
</tr>
</table>
<!--/html_preserve-->
1.  Compile this Rmarkdown document to HTML, then open the HTML file in
    a web browser. Open the inspector console for your browser
    (Ctrl-Shift-I in Chrome, Ctrl-Shift-C in Firefox) and look at the
    HTML code corresponding to various parts of the document. <br>
    Answer the following questions:

    -   What types of tags did you find?

        Width, height of frame broader and font sizes.

    -   How are code chunks formatted in HTML?

        R code chunks are with pre class=“r” tags

        The actual text is within a class=“hljs” tag

    -   What differences are there in the HTML markup for R code chunks
        and R output blocks?

    output color of attaching packages

2.  In R, the `rvest` package, which is part of the tidyverse, makes it
    (relatively) easy to pull specific pieces from structured documents.
    The `html_nodes` function selects nodes using either xpath or css,
    and additional functions such as `html_attrs`, `html_text`, and
    `html_table` pull information out of the markup text.<br> Choose a
    Wikipedia page that has at least one image to test the `rvest`
    package out

<!-- -->

    library(rvest)
    yammie <- read_html("https://en.wikipedia.org/wiki/Yammie_Lam")

    html_node(yammie,"img") %>% 
      xml_attr(attr="src") %>%
      paste0("https:",.) %>%
      magick::image_read()

<img src="../figure/09/XiyuanSun/unnamed-chunk-2-1.png" width="220" />

    html_nodes(yammie,"table")[3] %>%
      html_attr("class")

    ## [1] "wikitable"

    html_nodes(yammie,"table")[3] %>%
      html_table()

    ## [[1]]
    ##    Year                             English title
    ## 1  1985                         The Unwritten Law
    ## 2  1986                          Witch from Nepal
    ## 3  1987                            Happy Go Lucky
    ## 4  1989                They Came to Rob Hong Kong
    ## 5  1991                                The Tigers
    ## 6  1992                         The Unleaded Love
    ## 7  1993                 The Bride with White Hair
    ## 8  1993                          Flirting Scholar
    ## 9  1994 A Chinese Odyssey Part One: Pandora's Box
    ## 10 1994    A Chinese Odyssey Part Two: Cinderella
    ## 11 1999                                Aids Heart
    ## 12 2002                      Troublesome Night 16
    ##                   Chinese title                          Role Notes
    ## 1                        法外情                         Annie    NA
    ## 2                          奇緣                           Ada    NA
    ## 3                    開心快活人                          Mina    NA
    ## 4                      八寶奇兵                           May    NA
    ## 5                  五虎將之決裂                    Wah's Wife    NA
    ## 6                          花貨                          Mary    NA
    ## 7                    白髮魔女傳                       He Ehua    NA
    ## 8                  唐伯虎點秋香                   Tang's wife    NA
    ## 9  西遊記第壹佰零壹回之月光寶盒 Chunsansiniang/ Spider goblin    NA
    ## 10       西遊記大結局之仙履奇緣                 Spider goblin    NA
    ## 11                   愛滋初體驗                       Ah Qian    NA
    ## 12     陰陽路十六之回到武俠時代                   Pan Jinlian    NA
=======
  <tr>
    <th>Language</th>
    <th>Interests</th>
  </tr>
  <tr>
    <td>English</td>
    <td>Natural Language Processing.</td>
  </tr>
  <tr>
    <td>Spanish</td>
    <td>Procesamiento natural del lenguaje.</td>
  </tr>
</table>
<!--/html_preserve-->


3. Compile this Rmarkdown document to HTML, then open the HTML file in a web browser. Open the inspector console for your browser (Ctrl-Shift-I in Chrome, Ctrl-Shift-C in Firefox) and look at the HTML code corresponding to various parts of the document. <br>
Answer the following questions:

    - What types of tags did you find? 
    
      Width, height of frame broader and font sizes.
      
    - How are code chunks formatted in HTML?
      
      R code chunks are with pre class="r" tags
      
      The actual text is within a class="hljs" tag

    - What differences are there in the HTML markup for R code chunks and R output blocks?
    
    output color of attaching packages
    
    
    
4. In R, the `rvest` package, which is part of the tidyverse, makes it (relatively) easy to pull specific pieces from structured documents. The `html_nodes` function selects nodes using either xpath or css, and additional functions such as `html_attrs`, `html_text`, and `html_table` pull information out of the markup text.<br>
Choose a Wikipedia page that has at least one image to test the `rvest` package out


```r
library(rvest)
yammie <- read_html("https://en.wikipedia.org/wiki/Yammie_Lam")

html_node(yammie,"img") %>% 
  xml_attr(attr="src") %>%
  paste0("https:",.) %>%
  magick::image_read()
```

![center](./../figure/09/XiyuanSun/unnamed-chunk-2-1.png)

```r
html_nodes(yammie,"table")[3] %>%
  html_attr("class")
```

```
## [1] "wikitable"
```

```r
html_nodes(yammie,"table")[3] %>%
  html_table()
```

```
## [[1]]
##    Year                             English title
## 1  1985                         The Unwritten Law
## 2  1986                          Witch from Nepal
## 3  1987                            Happy Go Lucky
## 4  1989                They Came to Rob Hong Kong
## 5  1991                                The Tigers
## 6  1992                         The Unleaded Love
## 7  1993                 The Bride with White Hair
## 8  1993                          Flirting Scholar
## 9  1994 A Chinese Odyssey Part One: Pandora's Box
## 10 1994    A Chinese Odyssey Part Two: Cinderella
## 11 1999                                Aids Heart
## 12 2002                      Troublesome Night 16
##                   Chinese title                          Role Notes
## 1                        法外情                         Annie    NA
## 2                          奇緣                           Ada    NA
## 3                    開心快活人                          Mina    NA
## 4                      八寶奇兵                           May    NA
## 5                  五虎將之決裂                    Wah's Wife    NA
## 6                          花貨                          Mary    NA
## 7                    白髮魔女傳                       He Ehua    NA
## 8                  唐伯虎點秋香                   Tang's wife    NA
## 9  西遊記第壹佰零壹回之月光寶盒 Chunsansiniang/ Spider goblin    NA
## 10       西遊記大結局之仙履奇緣                 Spider goblin    NA
## 11                   愛滋初體驗                       Ah Qian    NA
## 12     陰陽路十六之回到武俠時代                   Pan Jinlian    NA
```






>>>>>>> blog 9 posts up
