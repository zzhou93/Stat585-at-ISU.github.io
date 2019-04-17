<<<<<<< HEAD
\#\#1. Weather Function

Sorry for the long variable names

    library(tidyverse)
    library(rvest)
    library(xml2)

    weather_today <- function(code){
      
      #input check
      if(length(code) > 1) stop("can't accept vector")
      
      #read the xml
      xmlurl <- paste0("https://w1.weather.gov/xml/current_obs/", code, ".xml")
      
      weather <- tryCatch(read_xml(xmlurl), 
                          error = function(c) "error")
      
      if(identical(weather, "error")) stop("invaid input, please check the code")
      
      temp2 <- xml_children(weather)
      name <- xml_name(temp2)
      
      #select the useful information
      searchlist <- c("location", "station_id", "latitude", "longitude",
                      "observation_time", "temp_f", "temp_c", "weather", 
                      "wind_mph", "wind_dir")
      usedinformation <- temp2[which(name %in% searchlist)]
      
      #construct a data.frame
      usedname <- xml_name(usedinformation)
      if(!all(searchlist %in% usedname)) warning("some information not avilable")
      
      usedcontent <- as.character(xml_contents(usedinformation))
      usedcontent <- as.data.frame(t(usedcontent), stringsAsFactors = F)
      colnames(usedcontent) <- usedname
      
      #fix the output type
      usedcontent$latitude <- as.numeric(usedcontent$latitude)
      usedcontent$longitude <- as.numeric(usedcontent$longitude)
      usedcontent$temp_f <- as.numeric(usedcontent$temp_f)
      usedcontent$temp_c <- as.numeric(usedcontent$temp_c)
      usedcontent$wind_mph <- as.numeric(usedcontent$wind_mph)
      usedcontent$observation_time <- lubridate::mdy_hm(usedcontent$observation_time)
      
      return(usedcontent)
    }

    # check the function with the following code
    # this function depends on "xml2", I assumed it is attached

    weather_today(c("KAAA", "KAMW"))
    weather_today("ABC")

    str(weather_today("KAMW"))

    ## 'data.frame':    1 obs. of  10 variables:
    ##  $ location        : chr "Ames, Ames Municipal Airport, IA"
    ##  $ station_id      : chr "KAMW"
    ##  $ latitude        : num 42
    ##  $ longitude       : num -93.6
    ##  $ observation_time: POSIXct, format: "2019-04-02 10:53:00"
    ##  $ weather         : chr "Mostly Cloudy"
    ##  $ temp_f          : num 39
    ##  $ temp_c          : num 3.9
    ##  $ wind_dir        : chr "Northwest"
    ##  $ wind_mph        : num 10.4

\#\#2. Which HTML tags did you investigate? Describe how to format at
least 3 separate pieces of a document using HTML tags.

I investigated the *&lt;head&gt;*, *&lt;body&gt;* and *&lt;p&gt;* tags.

If you want to have 3 separate paragraphs, you need three *&lt;p&gt;*
and *&lt;/p&gt;* pairs for each paragraph. If you want to have 3
separate patches, you may want three *&lt;div&gt;* and *&lt;/div&gt;*
pairs for each of them.

\#\#3. In my html file

I found *&lt;html&gt;*, *&lt;head&gt;*, *&lt;body&gt;*, *&lt;div&gt;*,
*&lt;pre&gt;*, *&lt;h1&gt;*, *&lt;h4&gt;*, *&lt;code&gt;*, and
*&lt;style&gt;*.

The code chunk is within a *&lt;div&gt;* tag with title as *id* and
heading, then it is within *&lt;pre&gt;* and *&lt;code&gt;* tags.

\#\#4. `rvest` package

link:<a href="https://en.wikipedia.org/wiki/Iowa_State_University" class="uri">https://en.wikipedia.org/wiki/Iowa_State_University</a>

    isu <- read_html("https://en.wikipedia.org/wiki/Iowa_State_University")

    isu_text <- isu %>%
    html_nodes("#mw-content-text") %>%
    html_nodes("div:first-child") %>%
    html_nodes("p:nth-child(3)") %>%
    html_text()

    isu_text

    ## [1] "Iowa State University of Science and Technology, generally referred to as Iowa State, is a public land-grant and space-grant research university located in Ames, Iowa, United States. It is the largest university in the state of Iowa and the third largest university in the Big 12 athletic conference.  Iowa State is classified as a research university with \"highest research activity\" by the Carnegie Foundation for the Advancement of Teaching.[4] Iowa State is also a member of the Association of American Universities (AAU), which consists of 60 leading research universities in North America.[5]"
=======
---
title: "A Series of Tubes..."
author: "Yawei Ge"
topic: "09"
layout: post
root: ../../../
output: 
  html_document: 
    css: extra.css
---


##1. Weather Function

Sorry for the long variable names

```r
library(tidyverse)
library(rvest)
library(xml2)

weather_today <- function(code){
  
  #input check
  if(length(code) > 1) stop("can't accept vector")
  
  #read the xml
  xmlurl <- paste0("https://w1.weather.gov/xml/current_obs/", code, ".xml")
  
  weather <- tryCatch(read_xml(xmlurl), 
                      error = function(c) "error")
  
  if(identical(weather, "error")) stop("invaid input, please check the code")
  
  temp2 <- xml_children(weather)
  name <- xml_name(temp2)
  
  #select the useful information
  searchlist <- c("location", "station_id", "latitude", "longitude",
                  "observation_time", "temp_f", "temp_c", "weather", 
                  "wind_mph", "wind_dir")
  usedinformation <- temp2[which(name %in% searchlist)]
  
  #construct a data.frame
  usedname <- xml_name(usedinformation)
  if(!all(searchlist %in% usedname)) warning("some information not avilable")
  
  usedcontent <- as.character(xml_contents(usedinformation))
  usedcontent <- as.data.frame(t(usedcontent), stringsAsFactors = F)
  colnames(usedcontent) <- usedname
  
  #fix the output type
  usedcontent$latitude <- as.numeric(usedcontent$latitude)
  usedcontent$longitude <- as.numeric(usedcontent$longitude)
  usedcontent$temp_f <- as.numeric(usedcontent$temp_f)
  usedcontent$temp_c <- as.numeric(usedcontent$temp_c)
  usedcontent$wind_mph <- as.numeric(usedcontent$wind_mph)
  usedcontent$observation_time <- lubridate::mdy_hm(usedcontent$observation_time)
  
  return(usedcontent)
}
```


```r
# check the function with the following code
# this function depends on "xml2", I assumed it is attached

weather_today(c("KAAA", "KAMW"))
weather_today("ABC")
```


```r
str(weather_today("KAMW"))
```

```
## 'data.frame':	1 obs. of  10 variables:
##  $ location        : chr "Ames, Ames Municipal Airport, IA"
##  $ station_id      : chr "KAMW"
##  $ latitude        : num 42
##  $ longitude       : num -93.6
##  $ observation_time: POSIXct, format: "2019-04-03 12:53:00"
##  $ weather         : chr "Overcast"
##  $ temp_f          : num 54
##  $ temp_c          : num 12.2
##  $ wind_dir        : chr "South"
##  $ wind_mph        : num 9.2
```

##2. Which HTML tags did you investigate? Describe how to format at least 3 separate pieces of a document using HTML tags.

I investigated the *\<head\>*, *\<body\>* and *\<p\>* tags. 

If you want to have 3 separate paragraphs, you need three *\<p\>* and *\</p\>* pairs for each paragraph. If you want to have 3 separate patches, you may want three *\<div\>* and *\</div\>* pairs for each of them.

##3. In my html file

I found *\<html\>*, *\<head\>*, *\<body\>*, *\<div\>*, *\<pre\>*, *\<h1\>*, *\<h4\>*, *\<code\>*, and *\<style\>*.

The code chunk is within a *\<div\>* tag with title as *id* and heading, then it is within *\<pre\>* and *\<code\>* tags.


##4. `rvest` package 

link:<https://en.wikipedia.org/wiki/Iowa_State_University>


```r
isu <- read_html("https://en.wikipedia.org/wiki/Iowa_State_University")

isu_text <- isu %>%
html_nodes("#mw-content-text") %>%
html_nodes("div:first-child") %>%
html_nodes("p:nth-child(3)") %>%
html_text()

isu_text
```

```
## [1] "Iowa State University of Science and Technology, generally referred to as Iowa State, is a public land-grant and space-grant research university located in Ames, Iowa, United States. It is the largest university in the state of Iowa and the third largest university in the Big 12 athletic conference.  Iowa State is classified as a research university with \"highest research activity\" by the Carnegie Foundation for the Advancement of Teaching.[4] Iowa State is also a member of the Association of American Universities (AAU), which consists of 60 leading research universities in North America.[5]"
```











>>>>>>> blog 9 posts up
