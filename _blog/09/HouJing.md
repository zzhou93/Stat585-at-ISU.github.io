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

    current_weather <- function(code){
      assertthat::assert_that(is.character(code), nchar(code)==4)
      weather <- read_xml(paste0("https://w1.weather.gov/xml/current_obs/",code,".xml"))
      data <- weather %>% xml_children() %>%
              xml_text() %>%
              as.data.frame()
      rownames(data) <- weather %>% xml_children() %>%
              xml_name() %>%
              as.character()
      ind <- c("station_id","latitude","longitude","observation_time",
                "weather","temperature_string","wind_dir","wind_mph")
      new <- as.data.frame(data[ind,])
      colnames(new) <- NULL
      rownames(new) <- ind
      checkmate::checkDataFrame(new)
      return(new)
    }

    current_weather("KAMW")

    ##                                                            
    ## station_id                                             KAMW
    ## latitude                                           41.99056
    ## longitude                                         -93.61889
    ## observation_time   Last Updated on Apr 2 2019, 10:53 am CDT
    ## weather                                       Mostly Cloudy
    ## temperature_string                           39.0 F (3.9 C)
    ## wind_dir                                          Northwest
    ## wind_mph                                               10.4

1.  Which HTML tags did you investigate? Describe how to format at least
    3 separate pieces of a document using HTML tags.

I investigated headings, paragraphs, colors, links, images, and so on.

*Headings*
<h1>
Winter is coming!
</h1>
*color*
<h1 style="background-color:rgb(60, 179, 113);">
Winter is coming!
</h1>
*link* <a href="https://en.wikipedia.org/wiki/Winter_Is_Coming"> Winter
Is Coming</a>

1.  Compile this Rmarkdown document to HTML, then open the HTML file in
    a web browser. Open the inspector console for your browser
    (Ctrl-Shift-I in Chrome, Ctrl-Shift-C in Firefox) and look at the
    HTML code corresponding to various parts of the document. <br>
    Answer the following questions:

    -   What types of tags did you find?

    I found html, head, body, div, style, script, p, ol, and so on.

    -   How are code chunks formatted in HTML?

    The code chunks are formatted with the start tag {pre class=“r”} and
    the end tag {/pre}, with the code inserted in between. The start tag
    of the code is {code class=“hljs”} and the end tag is {/code}.

    -   What differences are there in the HTML markup for R code chunks
        and R output blocks?

    The difference is the format of the start tag {pre}. There is no
    {class=“r”} in the start tag.

2.  In R, the `rvest` package, which is part of the tidyverse, makes it
    (relatively) easy to pull specific pieces from structured documents.
    The `html_nodes` function selects nodes using either xpath or css,
    and additional functions such as `html_attrs`, `html_text`, and
    `html_table` pull information out of the markup text.<br> Choose a
    Wikipedia page that has at least one image to test the `rvest`
    package out

<!-- -->

    library(rvest)
    library(magrittr)

    game<-read_html("https://en.wikipedia.org/wiki/Winter_Is_Coming")
    image<-html_nodes(game,"img") %>% 
      xml_attr(attr="src") %>%
      paste0("https:",.) 
    magick::image_read(image[2])

<img src="../figure/09/HouJing/unnamed-chunk-2-1.png" width="280" />

    table <- data.frame(html_nodes(game ,"table")[3] %>% html_table())
    table[,1:3]

    ##   Year                               Award
    ## 1 2011                        Portal Award
    ## 2 2011               Primetime Emmy Awards
    ## 3 2011 Primetime Creative Arts Emmy Awards
    ## 4 2012                  Golden Reel Awards
    ## 5 2012   Directors Guild of America Awards
    ## 6 2012              Visual Effects Society
    ##                                                                Category
    ## 1                                                          Best Episode
    ## 2                              Outstanding Directing for a Drama Series
    ## 3       Outstanding Make-up for a Single-Camera Series (Non-Prosthetic)
    ## 4 Best Sound Editing — Short Form Sound Effects and Foley in Television
    ## 5                                                       Dramatic Series
    ## 6          Outstanding Supporting Visual Effects in a Broadcast Program
=======
---
title: "A Series of Tubes..."
author: "Jing Hou"
topic: "09"
layout: post
root: ../../../
output: 
  html_document: 
    css: extra.css
---

**Write a blog post answering the following questions and detailing the progress: **

1. The `xml2` R package can be used to work with xml files. Write a function, `current_weather` that accepts a 4-letter airport code (KAMW in the URL here: https://w1.weather.gov/xml/current_obs/KAMW.xml) and returns a data frame with the airport location (station ID, latitude, longitude), last update time, and current weather information (temperature, weather condition, wind speed and direction) at that airport. The `xml2` functions `read_xml`, `xml_children`, `xml_name`, and `xml_text` will be useful. Remember to handle errors and check inputs, and make sure to return a data frame with appropriate data types. 


```r
library(xml2)
library(tidyverse)

current_weather <- function(code){
  assertthat::assert_that(is.character(code), nchar(code)==4)
  weather <- read_xml(paste0("https://w1.weather.gov/xml/current_obs/",code,".xml"))
  data <- weather %>% xml_children() %>%
          xml_text() %>%
          as.data.frame()
  rownames(data) <- weather %>% xml_children() %>%
          xml_name() %>%
          as.character()
  ind <- c("station_id","latitude","longitude","observation_time",
            "weather","temperature_string","wind_dir","wind_mph")
  new <- as.data.frame(data[ind,])
  colnames(new) <- NULL
  rownames(new) <- ind
  checkmate::checkDataFrame(new)
  return(new)
}

current_weather("KAMW")
```

```
##                                                            
## station_id                                             KAMW
## latitude                                           41.99056
## longitude                                         -93.61889
## observation_time   Last Updated on Apr 3 2019, 12:53 pm CDT
## weather                                            Overcast
## temperature_string                          54.0 F (12.2 C)
## wind_dir                                              South
## wind_mph                                                9.2
```

2. Which HTML tags did you investigate? Describe how to format at least 3 separate pieces of a document using HTML tags.

I investigated headings, paragraphs, colors, links, images, and so on. 

*Headings*
<h1>Winter is coming!</h1>
*color*
<h1 style="background-color:rgb(60, 179, 113);">Winter is coming!</h1>
*link*
<a href="https://en.wikipedia.org/wiki/Winter_Is_Coming"> Winter Is Coming</a>

3. Compile this Rmarkdown document to HTML, then open the HTML file in a web browser. Open the inspector console for your browser (Ctrl-Shift-I in Chrome, Ctrl-Shift-C in Firefox) and look at the HTML code corresponding to various parts of the document. <br>
Answer the following questions:

    - What types of tags did you find?
    
    I found html, head, body, div, style, script, p, ol, and so on.

    - How are code chunks formatted in HTML?
    
    The code chunks are formatted with the start tag {pre class="r"} and the end tag {/pre}, with the code inserted in between. The start tag of the code is {code class="hljs"} and the end tag is {/code}.
    
    - What differences are there in the HTML markup for R code chunks and R output blocks?
    
    The difference is the format of the start tag {pre}. There is no {class="r"} in the start tag.
    
4. In R, the `rvest` package, which is part of the tidyverse, makes it (relatively) easy to pull specific pieces from structured documents. The `html_nodes` function selects nodes using either xpath or css, and additional functions such as `html_attrs`, `html_text`, and `html_table` pull information out of the markup text.<br>
Choose a Wikipedia page that has at least one image to test the `rvest` package out


```r
library(rvest)
library(magrittr)

game<-read_html("https://en.wikipedia.org/wiki/Winter_Is_Coming")
image<-html_nodes(game,"img") %>% 
  xml_attr(attr="src") %>%
  paste0("https:",.) 
magick::image_read(image[2])
```

![center](./../figure/09/HouJing/unnamed-chunk-2-1.png)

```r
table <- data.frame(html_nodes(game ,"table")[3] %>% html_table())
table[,1:3]
```

```
##   Year                               Award
## 1 2011                        Portal Award
## 2 2011               Primetime Emmy Awards
## 3 2011 Primetime Creative Arts Emmy Awards
## 4 2012                  Golden Reel Awards
## 5 2012   Directors Guild of America Awards
## 6 2012              Visual Effects Society
##                                                                Category
## 1                                                          Best Episode
## 2                              Outstanding Directing for a Drama Series
## 3       Outstanding Make-up for a Single-Camera Series (Non-Prosthetic)
## 4 Best Sound Editing — Short Form Sound Effects and Foley in Television
## 5                                                       Dramatic Series
## 6          Outstanding Supporting Visual Effects in a Broadcast Program
```
>>>>>>> blog 9 posts up
