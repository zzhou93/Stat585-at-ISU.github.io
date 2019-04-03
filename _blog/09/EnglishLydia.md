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
    library(magrittr)
    library(checkmate)

    # list of all possible weather station codes
    ids <- read_xml("https://w1.weather.gov/xml/current_obs/index.xml")
    all_codes <- xml_text(xml_find_all(ids, ".//station_id")) 

    # function
    current_weather <- function(code){
      checkmate::assert_character(code)
      if (!(code %in% all_codes)) {
        stop("Code is not a valid weatherstation")}
      else {
      # get xml file
        tt <- read_xml(paste0("https://w1.weather.gov/xml/current_obs/",code,".xml"))
      # dataframe names
        nms <- xml_name(xml_children(tt)) %>%
          .[c(7:10, 13, 17, 19)]
      # dataframe information
        inf <- xml_text(xml_children(tt))%>%
          .[c(7:10, 13, 17, 19)]
      # make into table
        cc <- tibble(inf)%>%
                t()%>%
                magrittr::set_colnames(nms)%>%
                as_tibble()
        checkmate::assert_data_frame(cc, min.rows = 1)
        cc
      }
    }

    current_weather("CWBO")

    ## # A tibble: 1 x 7
    ##   station_id latitude longitude observation_time   temp_f wind_dir wind_mph
    ##   <chr>      <chr>    <chr>     <chr>              <chr>  <chr>    <chr>   
    ## 1 CWBO       50.55    -111.85   Last Updated on A… 35.0   Northwe… 3.5

    # current_weather("FFFF") # doesn't work with made up code

This function seems to work however everything in the dataframe is a
character. The next step would be to convert numeric values to numbers.

1.  Which HTML tags did you investigate? Describe how to format at least
    3 separate pieces of a document using HTML tags.
=======
---
title: "Blog 9: A Series of Tubes..."
author: "Lydia English"
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
library(magrittr)
library(checkmate)

# list of all possible weather station codes
ids <- read_xml("https://w1.weather.gov/xml/current_obs/index.xml")
all_codes <- xml_text(xml_find_all(ids, ".//station_id")) 

# function
current_weather <- function(code){
  checkmate::assert_character(code)
  if (!(code %in% all_codes)) {
    stop("Code is not a valid weatherstation")}
  else {
  # get xml file
    tt <- read_xml(paste0("https://w1.weather.gov/xml/current_obs/",code,".xml"))
  # dataframe names
    nms <- xml_name(xml_children(tt)) %>%
      .[c(7:10, 13, 17, 19)]
  # dataframe information
    inf <- xml_text(xml_children(tt))%>%
      .[c(7:10, 13, 17, 19)]
  # make into table
    cc <- tibble(inf)%>%
            t()%>%
            magrittr::set_colnames(nms)%>%
            as_tibble()
    checkmate::assert_data_frame(cc, min.rows = 1)
    cc
  }
}

current_weather("CWBO")
```

```
## # A tibble: 1 x 7
##   station_id latitude longitude observation_time   temp_f wind_dir wind_mph
##   <chr>      <chr>    <chr>     <chr>              <chr>  <chr>    <chr>   
## 1 CWBO       50.55    -111.85   Last Updated on A… 47.0   South    13.8
```

```r
# current_weather("FFFF") # doesn't work with made up code
```

This function seems to work however everything in the dataframe is a character. The next step would be to convert numeric values to numbers. 


2. Which HTML tags did you investigate? Describe how to format at least 3 separate pieces of a document using HTML tags.
>>>>>>> blog 9 posts up

**Here is an embedded link:**
<a href="https://lydiapenglish.github.io/">Here is my website </a>

**Here are headings and paragraphs (with colors):**
<<<<<<< HEAD
<h1 style="color:DodgerBlue;">
Example Attention Grabber
</h1>
<p style="background-color:DodgerBlue;">
Hopefully this header grabbed your attention
</p>
=======
<h1 style = "color:DodgerBlue;">Example Attention Grabber</h1>
<p style = "background-color:DodgerBlue;">Hopefully this header grabbed your attention </p>

>>>>>>> blog 9 posts up
**Here is an image**

<img src="http://www.illinoiswildflowers.info/prairie/photox/bt_gentian3.jpg" alt = "Closed Bottle Gentian">

<<<<<<< HEAD
1.  Compile this Rmarkdown document to HTML, then open the HTML file in
    a web browser. Open the inspector console for your browser
    (Ctrl-Shift-I in Chrome, Ctrl-Shift-C in Firefox) and look at the
    HTML code corresponding to various parts of the document.<br> Answer
    the following questions:

    -   *What types of tags did you find?*

    The html output for my Rmarkdown document is way more confusing than
    I thought! Even if just focus in on the paragraph outlining question
    1, there are tags like “li” and “ol” that seem to dicate how that
    paragraph is indented. Text that refers to r functions is tagged
    with “code”.

    -   *How are code chunks formatted in HTML?*

    The entire code chunk is class = “r”, however the individual pieces
    have class “hljs-XXX” and I’m not sure what that means. Functions
    vs. character strings vs. comments all have different “hljs-”
    references. All the tags are “span”.

    -   *What differences are there in the HTML markup for R code chunks
        and R output blocks?*

    Both the R code chunks and output blocks have class “hljs” under the
    “code” tag, however code chunks have class = “r” in the “pre” tags,
    which perhaps accounts for the different color background (white vs
    light grey). I don’t have much output in this html so it’s possible
    there are more differences than that.

2.  In R, the `rvest` package, which is part of the tidyverse, makes it
    (relatively) easy to pull specific pieces from structured documents.
    The `html_nodes` function selects nodes using either xpath or css,
    and additional functions such as `html_attrs`, `html_text`, and
    `html_table` pull information out of the markup text. <br> Choose a
    Wikipedia page that has at least one image to test the `rvest`
    package out

<!-- -->

    library(rvest)

    barley <- read_html("https://en.wikipedia.org/wiki/Barley")
    all_pics <- html_nodes(barley, "img") %>%
      html_attr(name = "src")
    # I think I need picture 5
    my_pic <-all_pics[[5]] %>%
      paste0("https:", .)
    knitr::include_graphics(my_pic)

![](https://upload.wikimedia.org/wikipedia/commons/thumb/2/20/Barley_%28Hordeum_vulgare%29_-_United_States_National_Arboretum_-_24_May_2009.jpg/220px-Barley_%28Hordeum_vulgare%29_-_United_States_National_Arboretum_-_24_May_2009.jpg)
=======
3. Compile this Rmarkdown document to HTML, then open the HTML file in a web browser. Open the inspector console for your browser (Ctrl-Shift-I in Chrome, Ctrl-Shift-C in Firefox) and look at the HTML code corresponding to various parts of the document.<br>
Answer the following questions:

    - *What types of tags did you find?* 
    
    
    The html output for my Rmarkdown document is way more confusing than I thought! Even if just focus in on the paragraph outlining question 1, there are tags like "li" and "ol" that seem to dicate how that paragraph is indented. Text that refers to r functions is tagged with "code". 

    - *How are code chunks formatted in HTML?*
    
    
    The entire code chunk is class = "r", however the individual pieces have class "hljs-XXX" and I'm not sure what that means. Functions vs. character strings vs. comments all have different "hljs-" references. All the tags are "span".

    - *What differences are there in the HTML markup for R code chunks and R output blocks?*
    
    
    Both the R code chunks and output blocks have class "hljs" under the "code" tag, however code chunks have class = "r" in the "pre" tags, which perhaps accounts for the different color background (white vs light grey). I don't have much output in this html so it's possible there are more differences than that.  
    
4. In R, the `rvest` package, which is part of the tidyverse, makes it (relatively) easy to pull specific pieces from structured documents. The `html_nodes` function selects nodes using either xpath or css, and additional functions such as `html_attrs`, `html_text`, and `html_table` pull information out of the markup text. <br>
Choose a Wikipedia page that has at least one image to test the `rvest` package out


```r
library(rvest)

barley <- read_html("https://en.wikipedia.org/wiki/Barley")
all_pics <- html_nodes(barley, "img") %>%
  html_attr(name = "src")
# I think I need picture 5
my_pic <-all_pics[[5]] %>%
  paste0("https:", .)
knitr::include_graphics(my_pic)
```

![center](./https://upload.wikimedia.org/wikipedia/commons/thumb/2/20/Barley_%28Hordeum_vulgare%29_-_United_States_National_Arboretum_-_24_May_2009.jpg/220px-Barley_%28Hordeum_vulgare%29_-_United_States_National_Arboretum_-_24_May_2009.jpg)



>>>>>>> blog 9 posts up
