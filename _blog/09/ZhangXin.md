<<<<<<< HEAD
**Write a blog post answering the following questions and detailing the
progress: **

1.  The `xml2` R package can be used to work with xml files. Write a
    function, `current_weather` that accepts a 4-letter airport code and
    returns a data frame with the airport location (station ID,
    latitude, longitude), last update time, and current weather
    information (temperature, weather condition, wind speed and
    direction) at that airport. The `xml2` functions `read_xml`,
    `xml_children`, `xml_name`, and `xml_text` will be useful. Remember
    to handle errors and check inputs, and make sure to return a data
    frame with appropriate data types.

<!-- -->

    library(xml2)
    library(dplyr)
    current_weather <- function(code) {
      code = as.character(code)
      if(!nchar(code)==4){
        df <- data.frame(station_id=code, latitude=NA, longitude=NA, observation_time=NA, weather=NA, temperature_string=NA, wind_dir=NA, wind_mph=NA)
        return(df)
        warning(paste0('current_weather only accepts 4-letter airport code: ',code,' is not a proper code!'))
      }
      
      URL <- paste0("https://w1.weather.gov/xml/current_obs/", code, ".xml")
      if(testit::has_error(URL %>% read_xml)){
        df <- data.frame(station_id=code, latitude=NA, longitude=NA, observation_time=NA, weather=NA, temperature_string=NA, wind_dir=NA, wind_mph=NA)
        return(df)
        warning(paste0('current_weather only accepts 4-letter airport code: ',code,' is not a proper code!'))
      }
      xml <- URL %>% read_xml
      nodeset <- xml %>% xml_children 
      name <- nodeset %>% xml_name
      content <- nodeset %>% xml_text
      df <- as.data.frame(matrix(content, ncol = length(content), byrow = T), stringsAsFactors = F)
      colnames(df) <- name
      df %>% dplyr::select(station_id, latitude, longitude, observation_time, weather, temperature_string, wind_dir, wind_mph)->df
      checkmate::checkDataFrame(df)
      return(df)
    }
    airport <- list('KAMW','KORD',123,'AB','ABCD')
    lapply(airport,FUN=current_weather)

    ## Error in open.connection(x, "rb") : HTTP error 404.

    ## [[1]]
    ##   station_id latitude longitude                         observation_time
    ## 1       KAMW 41.99056 -93.61889 Last Updated on Apr 2 2019, 10:53 am CDT
    ##         weather temperature_string  wind_dir wind_mph
    ## 1 Mostly Cloudy     39.0 F (3.9 C) Northwest     10.4
    ## 
    ## [[2]]
    ##   station_id latitude longitude                         observation_time
    ## 1       KORD 41.97972 -87.90444 Last Updated on Apr 2 2019, 10:51 am CDT
    ##         weather temperature_string  wind_dir wind_mph
    ## 1 Mostly Cloudy    50.0 F (10.0 C) Southwest     13.8
    ## 
    ## [[3]]
    ##   station_id latitude longitude observation_time weather
    ## 1        123       NA        NA               NA      NA
    ##   temperature_string wind_dir wind_mph
    ## 1                 NA       NA       NA
    ## 
    ## [[4]]
    ##   station_id latitude longitude observation_time weather
    ## 1         AB       NA        NA               NA      NA
    ##   temperature_string wind_dir wind_mph
    ## 1                 NA       NA       NA
    ## 
    ## [[5]]
    ##   station_id latitude longitude observation_time weather
    ## 1       ABCD       NA        NA               NA      NA
    ##   temperature_string wind_dir wind_mph
    ## 1                 NA       NA       NA

1.  Which HTML tags did you investigate? Describe how to format at least
    3 separate pieces of a document using HTML tags.
=======
---
title: "A Series of Tubes..."
author: "Xin Zhang"
topic: "09"
layout: post
root: ../../../
output: 
  html_document: 
    css: extra.css
---

**Write a blog post answering the following questions and detailing the progress: **

1. The `xml2` R package can be used to work with xml files. Write a function, `current_weather` that accepts a 4-letter airport code and returns a data frame with the airport location (station ID, latitude, longitude), last update time, and current weather information (temperature, weather condition, wind speed and direction) at that airport. The `xml2` functions `read_xml`, `xml_children`, `xml_name`, and `xml_text` will be useful. Remember to handle errors and check inputs, and make sure to return a data frame with appropriate data types. 


```r
library(xml2)
library(dplyr)
current_weather <- function(code) {
  code = as.character(code)
  if(!nchar(code)==4){
    df <- data.frame(station_id=code, latitude=NA, longitude=NA, observation_time=NA, weather=NA, temperature_string=NA, wind_dir=NA, wind_mph=NA)
    return(df)
    warning(paste0('current_weather only accepts 4-letter airport code: ',code,' is not a proper code!'))
  }
  
  URL <- paste0("https://w1.weather.gov/xml/current_obs/", code, ".xml")
  if(testit::has_error(URL %>% read_xml)){
    df <- data.frame(station_id=code, latitude=NA, longitude=NA, observation_time=NA, weather=NA, temperature_string=NA, wind_dir=NA, wind_mph=NA)
    return(df)
    warning(paste0('current_weather only accepts 4-letter airport code: ',code,' is not a proper code!'))
  }
  xml <- URL %>% read_xml
  nodeset <- xml %>% xml_children 
  name <- nodeset %>% xml_name
  content <- nodeset %>% xml_text
  df <- as.data.frame(matrix(content, ncol = length(content), byrow = T), stringsAsFactors = F)
  colnames(df) <- name
  df %>% dplyr::select(station_id, latitude, longitude, observation_time, weather, temperature_string, wind_dir, wind_mph)->df
  checkmate::checkDataFrame(df)
  return(df)
}
airport <- list('KAMW','KORD',123,'AB','ABCD')
lapply(airport,FUN=current_weather)
```

```
## Error in open.connection(x, "rb") : HTTP error 404.
```

```
## [[1]]
##   station_id latitude longitude                         observation_time
## 1       KAMW 41.99056 -93.61889 Last Updated on Apr 3 2019, 12:53 pm CDT
##    weather temperature_string wind_dir wind_mph
## 1 Overcast    54.0 F (12.2 C)    South      9.2
## 
## [[2]]
##   station_id latitude longitude                         observation_time
## 1       KORD 41.97972 -87.90444 Last Updated on Apr 3 2019, 12:51 pm CDT
##         weather temperature_string  wind_dir wind_mph
## 1 Mostly Cloudy    54.0 F (12.2 C) Southwest     10.4
## 
## [[3]]
##   station_id latitude longitude observation_time weather
## 1        123       NA        NA               NA      NA
##   temperature_string wind_dir wind_mph
## 1                 NA       NA       NA
## 
## [[4]]
##   station_id latitude longitude observation_time weather
## 1         AB       NA        NA               NA      NA
##   temperature_string wind_dir wind_mph
## 1                 NA       NA       NA
## 
## [[5]]
##   station_id latitude longitude observation_time weather
## 1       ABCD       NA        NA               NA      NA
##   temperature_string wind_dir wind_mph
## 1                 NA       NA       NA
```

2. Which HTML tags did you investigate? Describe how to format at least 3 separate pieces of a document using HTML tags.
>>>>>>> blog 9 posts up

-Lists:

<html>
<body>
<<<<<<< HEAD
<h5 style="background-color:MediumSeaGreen;">
Iowa
</h5>
<ul style="list-style-type:circle;">
<li style="background-color:DodgerBlue;">
Iowa State University
</li>
<li style="background-color:Tomato;">
University of Iowa
</li>
</ul>
</body>
</html>
=======

<h5 style="background-color:MediumSeaGreen;">Iowa</h5>

<ul style="list-style-type:circle;">
  <li style="background-color:DodgerBlue;"> Iowa State University</li>
  <li style="background-color:Tomato;"> University of Iowa</li>
</ul>  

</body>
</html>


>>>>>>> blog 9 posts up
-Links:

<html>
<body>
<head>
<style>
a:link, a:visited {
  background-color: Tomato;
  color: ligthgray;
  padding: 5px 10px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
}

a:hover, a:active {
  background-color: SlateBlue;
  color: white;
}
</style>
</head>
<<<<<<< HEAD
<a href="https://www.iastate.edu" target="_blank"> Iowa State
University</a> <a href="https://uiowa.edu" target="_blank"> University
of Iowa</a>

</body>
</html>
=======

<a href="https://www.iastate.edu" target="_blank"> Iowa State University</a>
<a href="https://uiowa.edu" target="_blank"> University of Iowa</a>


</body>
</html>


>>>>>>> blog 9 posts up
-Quotations

<html>
<body>
<address>
<<<<<<< HEAD
Written by Xin Zhang.<br> Visit us at:<br> www.stat.iastate.edu<br>
Ames, IA<br> USA
</address>
</body>
</html>
1.  Compile this Rmarkdown document to HTML, then open the HTML file in
    a web browser. Open the inspector console for your browser
    (Ctrl-Shift-I in Chrome, Ctrl-Shift-C in Firefox) and look at the
    HTML code corresponding to various parts of the document. <br>
    Answer the following questions:

-   What types of tags did you find?

    I find these tags: head, html, body, style, div, script, ul etc.

-   How are code chunks formatted in HTML?

    with the tag: pre class=“r”

-   What differences are there in the HTML markup for R code chunks and
    R output blocks?

    In the HTML, the R code chunks are in the: pre class=“r” code
    class=‘hljs’… /code /pre; and there are several tags for the
    different variables, such span class=’hljs-keywords, which makes the
    code unreadable.

    In the R blocks, the code is still the R code. There are differenbt
    colours for different variables, which make the code
    easy-understanding.

1.  In R, the `rvest` package, which is part of the tidyverse, makes it
    (relatively) easy to pull specific pieces from structured documents.
    The `html_nodes` function selects nodes using either xpath or css,
    and additional functions such as `html_attrs`, `html_text`, and
    `html_table` pull information out of the markup text.<br> Choose a
    Wikipedia page that has at least one image to test the `rvest`
    package out

<!-- -->

    library(rvest)
    haha <- read_html("https://en.wikipedia.org/wiki/Jiang_Zemin")
    html_node(haha ,"img") %>% 
      xml_attr(attr="src") %>%
      paste0("https:",.) %>%
      magick::image_read()

<img src="../figure/09/ZhangXin/unnamed-chunk-2-1.png" width="220" />

    html_nodes(haha ,"table")[3] %>%
      html_table()

    ## [[1]]
    ##       Transcriptions    Transcriptions
    ## 1  Standard Mandarin Standard Mandarin
    ## 2       Hanyu Pinyin       Jiāng Zémín
    ## 3         Wade–Giles Chiang1 Tzê2-min2
    ## 4                IPA   [tɕjáŋ tsɤ̌.mǐn]
    ## 5     Yue: Cantonese    Yue: Cantonese
    ## 6  Yale Romanization  Gōng Jaahk-màahn
    ## 7                IPA [kɔ́ːŋ tsàːk̚.mȁːn]
    ## 8           Jyutping Gong1 Zaak6-maan4
    ## 9       Southern Min      Southern Min
    ## 10       Hokkien POJ      Kang Tik-bîn
=======
Written by Xin Zhang.<br> 
Visit us at:<br>
www.stat.iastate.edu<br>
Ames, IA<br>
USA
</address>

</body>
</html>

3. Compile this Rmarkdown document to HTML, then open the HTML file in a web browser. Open the inspector console for your browser (Ctrl-Shift-I in Chrome, Ctrl-Shift-C in Firefox) and look at the HTML code corresponding to various parts of the document. <br>
Answer the following questions:

- What types of tags did you find? 

    I find these tags: head, html, body, style, div, script, ul etc.
 
- How are code chunks formatted in HTML?

    with the tag: pre class="r"

- What differences are there in the HTML markup for R code chunks and R output blocks?

    In the HTML, the R code chunks are in the: pre class="r" code class='hljs'... /code /pre; and there are several tags for the different variables, such span class='hljs-keywords, which makes the code unreadable.
    
    In the R blocks, the code is still the R code. There are differenbt colours for different variables, which make the code easy-understanding. 
    
4. In R, the `rvest` package, which is part of the tidyverse, makes it (relatively) easy to pull specific pieces from structured documents. The `html_nodes` function selects nodes using either xpath or css, and additional functions such as `html_attrs`, `html_text`, and `html_table` pull information out of the markup text.<br>
Choose a Wikipedia page that has at least one image to test the `rvest` package out



```r
library(rvest)
haha <- read_html("https://en.wikipedia.org/wiki/Jiang_Zemin")
html_node(haha ,"img") %>% 
  xml_attr(attr="src") %>%
  paste0("https:",.) %>%
  magick::image_read()
```

![center](./../figure/09/ZhangXin/unnamed-chunk-2-1.png)

```r
html_nodes(haha ,"table")[3] %>%
  html_table()
```

```
## [[1]]
##       Transcriptions    Transcriptions
## 1  Standard Mandarin Standard Mandarin
## 2       Hanyu Pinyin       Jiāng Zémín
## 3         Wade–Giles Chiang1 Tzê2-min2
## 4                IPA   [tɕjáŋ tsɤ̌.mǐn]
## 5     Yue: Cantonese    Yue: Cantonese
## 6  Yale Romanization  Gōng Jaahk-màahn
## 7                IPA [kɔ́ːŋ tsàːk̚.mȁːn]
## 8           Jyutping Gong1 Zaak6-maan4
## 9       Southern Min      Southern Min
## 10       Hokkien POJ      Kang Tik-bîn
```

>>>>>>> blog 9 posts up
