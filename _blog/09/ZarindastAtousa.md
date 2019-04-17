<<<<<<< HEAD
Write a function, current\_weather that accepts a 4-letter airport code
(KAMW in the URL here:
<a href="https://w1.weather.gov/xml/current_obs/KAMW.xml" class="uri">https://w1.weather.gov/xml/current_obs/KAMW.xml</a>)
and returns a data frame with the airport location (station ID,
latitude, longitude), last update time, and current weather information
(temperature, weather condition, wind speed and direction) at that
airport.

    library(xml2)
    library(tidyverse)
    library(dplyr)
    library(assertthat)
    current_weather <-function(code){
      
    url<-paste0("https://w1.weather.gov/xml/current_obs/",code,".xml")
    xml <-read_xml(url) 

    assert_that(nchar(code) == 4,is.character(code))


    #xml <-read_xml("https://w1.weather.gov/xml/current_obs/KAMW.xml") 
    names<-xml_contents(xml)%>%xml_name()  
    content<-  xml%>%xml_children()%>%xml_text
    df <- as.data.frame(matrix(content, ncol = length(content), byrow = T), stringsAsFactors = F)
    colnames(df) <- names
    airport_info<-df[which(colnames(df)%in% c("station_id","latitude","longitude","observation_time","weather","temperature_string","wind_dir","wind_mph"))]
    return(airport_info)

    assert_that(
        is.data.frame(airport_info), # Check input is a data frame
        not_empty(airport_info) # Check that df has at least one row and column
      )

    }

    #example
    current_weather("KAMW")

    ##   station_id latitude longitude                         observation_time
    ## 1       KAMW 41.99056 -93.61889 Last Updated on Apr 2 2019, 10:53 am CDT
    ##         weather temperature_string  wind_dir wind_mph
    ## 1 Mostly Cloudy     39.0 F (3.9 C) Northwest     10.4

Which HTML tags did you investigate? Describe how to format at least 3
separate pieces of a document using HTML tags.

link <a href="https://atousaz.github.io/">Visit my blog</a>

image
<img src="https://github.com/atousaz/atousaz.github.io/blob/master/image/2018.jpg" alt="my image in chicago">

colour
<h1 style="background-color:DodgerBlue;">
atousa zarindast
</h1>
Compile this Rmarkdown document to HTML, then open the HTML file in a
web browser. Open the inspector console for your browser (Ctrl-Shift-I
in Chrome, Ctrl-Shift-C in Firefox) and look at the HTML code
corresponding to various parts of the document. Answer the following
questions:

What types of tags did you find? The
<p>
tag defines a paragraph. The
<pre>
tag defines preformatted text. The <code> tag is a phrase tag. It
defines a piece of computer code. The
<div>
tag defines a division or a section in an HTML document. The
<script>
tag is used to define a client-side script (JavaScript).

    How are code chunks formatted in HTML?

    with <pre class="r">

    What differences are there in the HTML markup for R code chunks and R output blocks?

this is for code chunk
<pre class="r">
=======
---
title: "A Series of Tubes..."
author: "Atousa Zarindast"
topic: "09"
layout: post
root: ../../../
output: 
  html_document: 
    css: extra.css
---


Write a function, current_weather that accepts a 4-letter airport code (KAMW in the URL here: https://w1.weather.gov/xml/current_obs/KAMW.xml) and returns a data frame with the airport location (station ID, latitude, longitude), last update time, and current weather information (temperature, weather condition, wind speed and direction) at that airport. 

```r
library(xml2)
library(tidyverse)
library(dplyr)
library(assertthat)
current_weather <-function(code){
  
url<-paste0("https://w1.weather.gov/xml/current_obs/",code,".xml")
xml <-read_xml(url) 

assert_that(nchar(code) == 4,is.character(code))


#xml <-read_xml("https://w1.weather.gov/xml/current_obs/KAMW.xml") 
names<-xml_contents(xml)%>%xml_name()  
content<-  xml%>%xml_children()%>%xml_text
df <- as.data.frame(matrix(content, ncol = length(content), byrow = T), stringsAsFactors = F)
colnames(df) <- names
airport_info<-df[which(colnames(df)%in% c("station_id","latitude","longitude","observation_time","weather","temperature_string","wind_dir","wind_mph"))]
return(airport_info)

assert_that(
    is.data.frame(airport_info), # Check input is a data frame
    not_empty(airport_info) # Check that df has at least one row and column
  )

}

#example
current_weather("KAMW")
```

```
##   station_id latitude longitude                         observation_time
## 1       KAMW 41.99056 -93.61889 Last Updated on Apr 3 2019, 12:53 pm CDT
##    weather temperature_string wind_dir wind_mph
## 1 Overcast    54.0 F (12.2 C)    South      9.2
```
Which HTML tags did you investigate? Describe how to format at least 3 separate pieces of a document using HTML tags.

link
<a href="https://atousaz.github.io/">Visit my blog</a> 

image
<img src="https://github.com/atousaz/atousaz.github.io/blob/master/image/2018.jpg" alt="my image in chicago"> 

colour
 <h1 style="background-color:DodgerBlue;">atousa zarindast</h1>
 
 
Compile this Rmarkdown document to HTML, then open the HTML file in a web browser. Open the inspector console for your browser (Ctrl-Shift-I in Chrome, Ctrl-Shift-C in Firefox) and look at the HTML code corresponding to various parts of the document.
Answer the following questions:

  What types of tags did you find?
    The <p> tag defines a paragraph.
    The <pre> tag defines preformatted text.
    The <code> tag is a phrase tag. It defines a piece of     computer code. 
    The <div> tag defines a division or a section in an      HTML document.
    The <script> tag is used to define a client-side         script (JavaScript).
    
    
    How are code chunks formatted in HTML?
    
    with <pre class="r">

    What differences are there in the HTML markup for R code chunks and R output blocks?
this is for code chunk
    <pre class="r">
>>>>>>> blog 9 posts up
    <code class="h1js">
    <span class..</span>
    ....
    ....
    ...
    </code>
this is for R output block
    </pre>
     <code class="h1js"> </code>
    </pre>
<<<<<<< HEAD

seems that R code chunk has class=“r”

rvest package, which is part of the tidyverse, makes it (relatively)
easy to pull specific pieces from structured documents. The html\_nodes
function selects nodes using either xpath or css, and additional
functions such as html\_attrs, html\_text, and html\_table pull
information out of the markup text. Choose a Wikipedia page that has at
least one image to test the rvest package out

    library(rvest)
    library(purrr)
    html <-read_html("https://en.wikipedia.org/wiki/Nowruz")
    t<-html%>%html_nodes(".infobox")%>%html_table()%>% flatten %>% map_dfr(data.frame)

    ## Warning in bind_rows_(x, .id): Unequal factor levels: coercing to character

    ## Warning in bind_rows_(x, .id): binding character and factor vector,
    ## coercing into character vector

    ## Warning in bind_rows_(x, .id): binding character and factor vector,
    ## coercing into character vector

    ## Warning in bind_rows_(x, .id): binding character and factor vector,
    ## coercing into character vector

    ## Warning in bind_rows_(x, .id): binding character and factor vector,
    ## coercing into character vector

    #html%>%html_nodes(".image") %>% html_attr("alt")
=======
seems that R code chunk has class="r"
    
rvest package, which is part of the tidyverse, makes it (relatively) easy to pull specific pieces from structured documents. The html_nodes function selects nodes using either xpath or css, and additional functions such as html_attrs, html_text, and html_table pull information out of the markup text.
Choose a Wikipedia page that has at least one image to test the rvest package out

```r
library(rvest)
library(purrr)
html <-read_html("https://en.wikipedia.org/wiki/Nowruz")
t<-html%>%html_nodes(".infobox")%>%html_table()%>% flatten %>% map_dfr(data.frame)
```

```
## Warning in bind_rows_(x, .id): Unequal factor levels: coercing to character
```

```
## Warning in bind_rows_(x, .id): binding character and factor vector,
## coercing into character vector

## Warning in bind_rows_(x, .id): binding character and factor vector,
## coercing into character vector

## Warning in bind_rows_(x, .id): binding character and factor vector,
## coercing into character vector

## Warning in bind_rows_(x, .id): binding character and factor vector,
## coercing into character vector
```

```r
#html%>%html_nodes(".image") %>% html_attr("alt")
```
>>>>>>> blog 9 posts up
