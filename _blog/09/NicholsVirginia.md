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
    direction) at that airport.

The `xml2` functions `read_xml`, `xml_children`, `xml_name`, and
`xml_text` will be useful. Remember to handle errors and check inputs,
and make sure to return a data frame with appropriate data types.

    library(xml2)
    library(tidyverse)
    library(assertthat)
    library(stringr)


    current_weather <- function(mycode){

      
      mycode <- "KAMW"
      assertthat::assert_that(stringr::str_length(mycode) == 4)
      assertthat::assert_that(is.character(mycode))
      
      # Proceeed....
      a <- xml2::read_xml(paste0("https://w1.weather.gov/xml/current_obs/", mycode, ".xml"))
    chldrn <- xml_children(a)
    cnms <- xml_name(chldrn)
    ctxt <- xml_text(chldrn)

    dat <- tibble(mynames = cnms,
               mytxt = ctxt) %>%
      filter(mynames %in% c("station_id", "latitude", "longitude", "observation_time",
                            "temperature_string", "weather", "wind_string")) %>%
      as.data.frame()

    assertthat::assert_that(is.data.frame(dat))

    return(dat)
    }


    current_weather("KAMW")

    ##              mynames                                    mytxt
    ## 1         station_id                                     KAMW
    ## 2           latitude                                 41.99056
    ## 3          longitude                                -93.61889
    ## 4   observation_time Last Updated on Apr 2 2019, 10:53 am CDT
    ## 5            weather                            Mostly Cloudy
    ## 6 temperature_string                           39.0 F (3.9 C)
    ## 7        wind_string             Northwest at 10.4 MPH (9 KT)

1.  Which HTML tags did you investigate? Describe how to format at least
    3 separate pieces of a document using HTML tags.

**Images** They do not have a closing tag.

    <img src="img_dog.jpg" alt="Not a cat">

**Color** I can set text color

    <h1 style="color:Tomato;">Hello World</h1>

with the style attribute.

**Style** Here I learned about the style attribute in contexts outside
of just color.

    <h1 style="font-size:300%;">This is a heading</h1>

1.  Compile this Rmarkdown document to HTML, then open the HTML file in
    a web browser. Open the inspector console for your browser
    (Ctrl-Shift-I in Chrome, Ctrl-Shift-C in Firefox) and look at the
    HTML code corresponding to various parts of the document. <br>
    Answer the following questions:

    -   What types of tags did you find?

code, span, div…body, p, and html are things I recognize.

    - How are code chunks formatted in HTML?

As pre class = ‘r’ tags?

    - What differences are there in the HTML markup for R code chunks and R output blocks?

I think it’s just the class. class = ‘r’ indicates code, while….I don’t
know.

1.  In R, the `rvest` package, which is part of the tidyverse, makes it
    (relatively) easy to pull specific pieces from structured documents.
    The `html_nodes` function selects nodes using either xpath or css,
    and additional functions such as `html_attrs`, `html_text`, and
    `html_table` pull information out of the markup text.<br> Choose a
    Wikipedia page that has at least one image to test the `rvest`
    package out

<!-- -->

    library(rvest)
    wpie <- xml2::read_html("https://en.wikipedia.org/wiki/Apple_pie")

    wpie_img <- wpie %>% 
      rvest::html_node("img")

I don’t know what to do with the image now that I have it.
=======
---
title: "A Series of Tubes..."
author: "Virginia (Gina) Nichols"
topic: "09"
layout: post
root: ../../../
output: 
  html_document: 
    css: extra.css
---

**Write a blog post answering the following questions and detailing the progress: **

1. The `xml2` R package can be used to work with xml files. Write a function, `current_weather` that accepts a 4-letter airport code (KAMW in the URL here: https://w1.weather.gov/xml/current_obs/KAMW.xml) and returns a data frame with the airport location (station ID, latitude, longitude), last update time, and current weather information (temperature, weather condition, wind speed and direction) at that airport. 

The `xml2` functions `read_xml`, `xml_children`, `xml_name`, and `xml_text` will be useful. Remember to handle errors and check inputs, and make sure to return a data frame with appropriate data types. 


```r
library(xml2)
library(tidyverse)
library(assertthat)
library(stringr)


current_weather <- function(mycode){

  
  mycode <- "KAMW"
  assertthat::assert_that(stringr::str_length(mycode) == 4)
  assertthat::assert_that(is.character(mycode))
  
  # Proceeed....
  a <- xml2::read_xml(paste0("https://w1.weather.gov/xml/current_obs/", mycode, ".xml"))
chldrn <- xml_children(a)
cnms <- xml_name(chldrn)
ctxt <- xml_text(chldrn)

dat <- tibble(mynames = cnms,
           mytxt = ctxt) %>%
  filter(mynames %in% c("station_id", "latitude", "longitude", "observation_time",
                        "temperature_string", "weather", "wind_string")) %>%
  as.data.frame()

assertthat::assert_that(is.data.frame(dat))

return(dat)
}


current_weather("KAMW")
```

```
##              mynames                                    mytxt
## 1         station_id                                     KAMW
## 2           latitude                                 41.99056
## 3          longitude                                -93.61889
## 4   observation_time Last Updated on Apr 3 2019, 12:53 pm CDT
## 5            weather                                 Overcast
## 6 temperature_string                          54.0 F (12.2 C)
## 7        wind_string                  South at 9.2 MPH (8 KT)
```


2. Which HTML tags did you investigate? Describe how to format at least 3 separate pieces of a document using HTML tags.

**Images**
They do not have a closing tag. 

```r
<img src="img_dog.jpg" alt="Not a cat">
```

**Color**
I can set text color

```r
<h1 style="color:Tomato;">Hello World</h1>
```
with the style attribute. 

**Style**
Here I learned about the style attribute in contexts outside of just color. 

```r
<h1 style="font-size:300%;">This is a heading</h1>
```

3. Compile this Rmarkdown document to HTML, then open the HTML file in a web browser. Open the inspector console for your browser (Ctrl-Shift-I in Chrome, Ctrl-Shift-C in Firefox) and look at the HTML code corresponding to various parts of the document. <br>
Answer the following questions:

    - What types of tags did you find? 

code, span, div...body, p, and html are things I recognize. 

    - How are code chunks formatted in HTML?

As pre class = 'r' tags?

    - What differences are there in the HTML markup for R code chunks and R output blocks?
    
I think it's just the class. class = 'r' indicates code, while....I don't know.     
    
4. In R, the `rvest` package, which is part of the tidyverse, makes it (relatively) easy to pull specific pieces from structured documents. The `html_nodes` function selects nodes using either xpath or css, and additional functions such as `html_attrs`, `html_text`, and `html_table` pull information out of the markup text.<br>
Choose a Wikipedia page that has at least one image to test the `rvest` package out


```r
library(rvest)
wpie <- xml2::read_html("https://en.wikipedia.org/wiki/Apple_pie")

wpie_img <- wpie %>% 
  rvest::html_node("img")
```
I don't know what to do with the image now that I have it. 
>>>>>>> blog 9 posts up
