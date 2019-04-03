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
    current_weather <- function(code){
      assertthat::assert_that(is.character(code))
      assertthat::assert_that(nchar(code)==4)
      url <- paste0("https://w1.weather.gov/xml/current_obs/",code,".xml")
      xml <- read_xml(url)
      a <- xml_children(xml)
      dat <- data.frame(xml_text(a))
      rownames(dat) <- xml_name(a)
      dat[,1] <- as.character(dat[,1])
      info <- c("station_id","latitude","longitude","observation_time",
                "temperature_string","weather","wind_dir","wind_mph")
      dat <- data.frame(dat[info,])
      rownames(dat) <- info
      colnames(dat) <- code
      return(dat)
    }
    current_weather("KAMW")

    ##                                                        KAMW
    ## station_id                                             KAMW
    ## latitude                                           41.99056
    ## longitude                                         -93.61889
    ## observation_time   Last Updated on Apr 2 2019, 10:53 am CDT
    ## temperature_string                           39.0 F (3.9 C)
    ## weather                                       Mostly Cloudy
    ## wind_dir                                          Northwest
    ## wind_mph                                               10.4

1.  Which HTML tags did you investigate? Describe how to format at least
    3 separate pieces of a document using HTML tags. I investigated
    color, links, image.

-color
<h1 style="background-color: Tomato; color:Blue;">
STAT585 BLOG 9
</h1>
-links
<a href="https://github.com/Stat585-at-ISU/blog-2019/tree/master/09">Blog
9 folder</a>
=======
---
title: "A Series of Tubes..."
author: "Jing Li"
topic: "09"
layout: post
root: ../../../
---



1. The `xml2` R package can be used to work with xml files. Write a function, `current_weather` that accepts a 4-letter airport code (KAMW in the URL here: https://w1.weather.gov/xml/current_obs/KAMW.xml) and returns a data frame with the airport location (station ID, latitude, longitude), last update time, and current weather information (temperature, weather condition, wind speed and direction) at that airport. The `xml2` functions `read_xml`, `xml_children`, `xml_name`, and `xml_text` will be useful. Remember to handle errors and check inputs, and make sure to return a data frame with appropriate data types. 


```r
library(xml2)
current_weather <- function(code){
  assertthat::assert_that(is.character(code))
  assertthat::assert_that(nchar(code)==4)
  url <- paste0("https://w1.weather.gov/xml/current_obs/",code,".xml")
  xml <- read_xml(url)
  a <- xml_children(xml)
  dat <- data.frame(xml_text(a))
  rownames(dat) <- xml_name(a)
  dat[,1] <- as.character(dat[,1])
  info <- c("station_id","latitude","longitude","observation_time",
            "temperature_string","weather","wind_dir","wind_mph")
  dat <- data.frame(dat[info,])
  rownames(dat) <- info
  colnames(dat) <- code
  return(dat)
}
current_weather("KAMW")
```

```
##                                                        KAMW
## station_id                                             KAMW
## latitude                                           41.99056
## longitude                                         -93.61889
## observation_time   Last Updated on Apr 3 2019, 12:53 pm CDT
## temperature_string                          54.0 F (12.2 C)
## weather                                            Overcast
## wind_dir                                              South
## wind_mph                                                9.2
```

2. Which HTML tags did you investigate? Describe how to format at least 3 separate pieces of a document using HTML tags.
I investigated color, links, image.

-color
<h1 style="background-color: Tomato; color:Blue;">STAT585 BLOG 9</h1> 

-links
<a href="https://github.com/Stat585-at-ISU/blog-2019/tree/master/09">Blog 9 folder</a>
>>>>>>> blog 9 posts up

-image
<img src="https://hips.hearstapps.com/hmg-prod.s3.amazonaws.com/images/gettyimages-182880589-1493334765.jpg" alt="flower">

<<<<<<< HEAD
1.  Compile this Rmarkdown document to HTML, then open the HTML file in
    a web browser. Open the inspector console for your browser
    (Ctrl-Shift-I in Chrome, Ctrl-Shift-C in Firefox) and look at the
    HTML code corresponding to various parts of the document. <br>
    Answer the following questions:

    -   What types of tags did you find? color, backgroud color, image,
        link, list, class, id, etc

    -   How are code chunks formatted in HTML?
        <pre class="r">
          <code class="hljs">...</code>
         </pre>
    -   What differences are there in the HTML markup for R code chunks
        and R output blocks? R code chuncs begin with
        <pre class="r">
        , R output begin with
        <pre>

2.  In R, the `rvest` package, which is part of the tidyverse, makes it
    (relatively) easy to pull specific pieces from structured documents.
    The `html_nodes` function selects nodes using either xpath or css,
    and additional functions such as `html_attrs`, `html_text`, and
    `html_table` pull information out of the markup text.<br> Choose a
    Wikipedia page that has at least one image to test the `rvest`
    package out

<!-- -->

    library(rvest)
    image <- read_html(url) %>% 
      html_nodes("img") %>%
      html_attr("src") %>%
      paste0("http:",.) 
    magick::image_read(image[2])
=======
3. Compile this Rmarkdown document to HTML, then open the HTML file in a web browser. Open the inspector console for your browser (Ctrl-Shift-I in Chrome, Ctrl-Shift-C in Firefox) and look at the HTML code corresponding to various parts of the document. <br>
Answer the following questions:

    - What types of tags did you find? 
    color, backgroud color, image, link, list, class, id, etc

    - How are code chunks formatted in HTML?
    <pre class="r">
     <code class="hljs">...</code>
    </pre>

    - What differences are there in the HTML markup for R code chunks and R output blocks?
    R code chuncs begin with <pre class="r">, R output begin with <pre>
    
4. In R, the `rvest` package, which is part of the tidyverse, makes it (relatively) easy to pull specific pieces from structured documents. The `html_nodes` function selects nodes using either xpath or css, and additional functions such as `html_attrs`, `html_text`, and `html_table` pull information out of the markup text.<br>
Choose a Wikipedia page that has at least one image to test the `rvest` package out


```r
library(rvest)
image <- read_html(url) %>% 
  html_nodes("img") %>%
  html_attr("src") %>%
  paste0("http:",.) 
magick::image_read(image[2])
```


>>>>>>> blog 9 posts up
