<<<<<<< HEAD
\#\#\#1. Write a function, `current_weather` that accepts a 4-letter
airport code (KAMW in the URL here:
<a href="https://w1.weather.gov/xml/current_obs/KAMW.xml" class="uri">https://w1.weather.gov/xml/current_obs/KAMW.xml</a>)
and returns a data frame with the airport location (station ID,
latitude, longitude), last update time, and current weather information
(temperature, weather condition, wind speed and direction) at that
airport.

    library(xml2)
    library(assertthat)
    library(tidyverse)
    library(purrr)
    current_weather <- function(airport_code){
      assert_that(is.character(airport_code), nchar(airport_code)==4, msg="Code is not a character string of length 4")
      
      #read data and extract useful info
      wdat <- read_xml(paste0("https://w1.weather.gov/xml/current_obs/",airport_code,".xml"))
      namew <- wdat %>% xml_children %>% xml_name
      wdatname <- paste0("//",namew[c(6:9,11,14:16,18:20)])
      dfo<- wdatname %>% purrr::map(xml_find_all, x=wdat) %>% purrr::map_chr(xml_text)  %>%
        t() %>%  data.frame()
      
      #rename everything and coerce it to correct data types
      names(dfo) <- namew[c(6:9,11,14:16,18:20)]
      dfo <-   dfo <- dfo %>% mutate_all(as.character) %>%
        mutate_at(c("latitude","longitude","temp_f","temp_c","relative_humidity","wind_degrees","wind_mph"), as.double) %>% 
        mutate_at(c("location", "station_id", "observation_time_rfc822", "wind_dir"), as.character)
      
      assert_that(is.data.frame(dfo), msg="error: output not data frame. Check station_id to make sure it's valid")
      return(dfo)
    }

    #check to make sure the function works
    current_weather("KBBW")

    ##                                       location station_id latitude
    ## 1 Broken Bow, Broken Bow Municipal Airport, NE       KBBW 41.43333
    ##   longitude         observation_time_rfc822 temp_f temp_c
    ## 1    -99.65 Tue, 02 Apr 2019 10:53:00 -0500     44    6.7
    ##   relative_humidity wind_dir wind_degrees wind_mph
    ## 1                65     West          270      8.1

\#\#\#2. Which HTML tags did you investigate? Describe how to format at
least 3 separate pieces of a document using HTML tags.
<ol type="I">
<li>
&lt;h1&gt; and &lt;p&gt; provide the simplest tags in that they format
headers and paragraphs, respectively. All we need to do is put them when
we start and then &lt;/h1&gt; and &lt;/p&gt; when we end them, with
whatever the body is between the tags.
</li>
<li>
There are also text formatting tags, like <b> bold </b>, which can
change the text style between the tags. Examples include &lt;b&gt; for
bold and &lt;sub&gt; for subscripts.
</li>
<li>
The last one I looked at is lists, and I used that to create the list
used for this section by starting with &lt;ol&gt; and ending with
&lt;/ol&gt; tags, and tagging each element with &lt;li&gt; and
&lt;/li&gt;.
</li>
</ol>
\#\#\#3. Compile this Rmarkdown document to HTML, then open the HTML
file in a web browser. Open the inspector console for your browser
(Ctrl-Shift-I in Chrome, Ctrl-Shift-C in Firefox) and look at the HTML
code corresponding to various parts of the document. <br>

\#\#\#\#*What types of tags did you find?*

There are mainly body and div tags for formatting, as well as a few
style tags and headers

\#\#\#\#*How are code chunks formatted in HTML?*

It appears that code chunks are formatted in a container of style “R”
with a &lt;pre: class = “r”&gt; tag, which is then followed by a
&lt;code&gt; tag. Each individual line of code is then contained within
a &lt;span&gt; block that takes up an unspecified width on each line.

\#\#\#\#*What differences are there in the HTML markup for R code chunks
and R output blocks?*

The output blocks do not fall under the &lt;pre class=“r”&gt; tag as
above, and follow the default class. The individual lines are not
contained within &lt;span&gt; blocks like in the code chunks. For my
output, there is no real formatting to the output but it is kept in a
container.

\#\#\#4. In R, the `rvest` package, which is part of the tidyverse,
makes it (relatively) easy to pull specific pieces from structured
documents.

I will just extract the poster from the page from one of my favorite
recent movies, Paul Thomas Anderson’s “Inherent Vice”:

    library(rvest)
    library(magick)
    #read in the page
    iv <- read_html("https://en.wikipedia.org/wiki/Inherent_Vice_(film)")
    #get the link of the image
    posterlink <- iv %>% html_nodes(".thumbborder") %>% html_attr("src")
    #read it in using magick package
    image_read(paste0("https:",posterlink))

<img src="../figure/09/HarmsSteve/unnamed-chunk-2-1.png" width="220" />
=======
---
title: "A Series of Tubes..."
author: "Steve Harms"
topic: "09"
layout: post
root: ../../../
output: 
  html_document: 
    css: extra.css
---

###1.  Write a function, `current_weather` that accepts a 4-letter airport code (KAMW in the URL here: https://w1.weather.gov/xml/current_obs/KAMW.xml) and returns a data frame with the airport location (station ID, latitude, longitude), last update time, and current weather information (temperature, weather condition, wind speed and direction) at that airport.


```r
library(xml2)
library(assertthat)
library(tidyverse)
library(purrr)
current_weather <- function(airport_code){
  assert_that(is.character(airport_code), nchar(airport_code)==4, msg="Code is not a character string of length 4")
  
  #read data and extract useful info
  wdat <- read_xml(paste0("https://w1.weather.gov/xml/current_obs/",airport_code,".xml"))
  namew <- wdat %>% xml_children %>% xml_name
  wdatname <- paste0("//",namew[c(6:9,11,14:16,18:20)])
  dfo<- wdatname %>% purrr::map(xml_find_all, x=wdat) %>% purrr::map_chr(xml_text)  %>%
    t() %>%  data.frame()
  
  #rename everything and coerce it to correct data types
  names(dfo) <- namew[c(6:9,11,14:16,18:20)]
  dfo <-   dfo <- dfo %>% mutate_all(as.character) %>%
    mutate_at(c("latitude","longitude","temp_f","temp_c","relative_humidity","wind_degrees","wind_mph"), as.double) %>% 
    mutate_at(c("location", "station_id", "observation_time_rfc822", "wind_dir"), as.character)
  
  assert_that(is.data.frame(dfo), msg="error: output not data frame. Check station_id to make sure it's valid")
  return(dfo)
}

#check to make sure the function works
current_weather("KBBW")
```

```
##                                       location station_id latitude
## 1 Broken Bow, Broken Bow Municipal Airport, NE       KBBW 41.43333
##   longitude         observation_time_rfc822 temp_f temp_c
## 1    -99.65 Wed, 03 Apr 2019 12:53:00 -0500     49    9.4
##   relative_humidity wind_dir wind_degrees wind_mph
## 1                69     East          110     18.4
```



###2. Which HTML tags did you investigate? Describe how to format at least 3 separate pieces of a document using HTML tags.
 <ol type="I">

<li> \<h1> and \<p> provide the simplest tags in that they format headers and paragraphs, respectively. All we need to do is put them when we start and then \</h1> and \</p> when we end them, with whatever the body is between the tags.</li>
<li> There are also text formatting tags, like  <b> bold </b>, which can change the text style between the tags. Examples include \<b> for bold and \<sub> for subscripts.</li>
<li> The last one I looked at is lists, and I used that to create the list used for this section by starting with \<ol> and ending with \</ol> tags, and tagging each element with \<li> and \</li>. </li>

</ol> 

###3. Compile this Rmarkdown document to HTML, then open the HTML file in a web browser. Open the inspector console for your browser (Ctrl-Shift-I in Chrome, Ctrl-Shift-C in Firefox) and look at the HTML code corresponding to various parts of the document. <br>

####*What types of tags did you find?* 
    
  There are mainly body and div tags for formatting, as well as a few style tags and headers
    
####*How are code chunks formatted in HTML?*
    
  It appears that code chunks are formatted in a container of style "R" with a \<pre: class = "r"> tag, which is then followed by a \<code> tag. Each individual line of code is then contained within a \<span> block that takes up an unspecified width on each line.
    
####*What differences are there in the HTML markup for R code chunks and R output blocks?*
  
  The output blocks do not fall under the \<pre class="r"> tag as above, and follow the default class. The individual lines are not contained within \<span> blocks like in the code chunks. For my output, there is no real formatting to the output but it is kept in a container. 

###4. In R, the `rvest` package, which is part of the tidyverse, makes it (relatively) easy to pull specific pieces from structured documents.

I will just extract the poster from the page from one of my favorite recent movies, Paul Thomas Anderson's "Inherent Vice":


```r
library(rvest)
library(magick)
```

```
## Linking to ImageMagick 6.9.9.39
## Enabled features: cairo, fontconfig, freetype, lcms, pango, rsvg, webp
## Disabled features: fftw, ghostscript, x11
```

```r
#read in the page
iv <- read_html("https://en.wikipedia.org/wiki/Inherent_Vice_(film)")
#get the link of the image
posterlink <- iv %>% html_nodes(".thumbborder") %>% html_attr("src")
#read it in using magick package
image_read(paste0("https:",posterlink))
```

![center](./../figure/09/HarmsSteve/unnamed-chunk-2-1.png)

>>>>>>> blog 9 posts up
