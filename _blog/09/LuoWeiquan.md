<<<<<<< HEAD
    library(xml2)
    library(tidyverse)
    library(checkmate)
    library(rvest)

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

    station_id <- "KAMW"
    current_weather <- function(station_id){
      url <- paste0("https://w1.weather.gov/xml/current_obs/", station_id ,".xml")
      xml <- try(read_xml(url))
      checkmate::assert_class(xml, c("xml_document", "xml_node"))
      
      nodeset <- xml_children(xml)
      checkmate::assert_class(nodeset, c("xml_nodeset"))
      
      tempname <- xml_name(xml_children(xml))
      text <- lapply(tempname, function(x) xml_text(xml_find_all(nodeset, paste0("//",x)))) %>% 
        unlist() %>% 
        set_names(tempname) %>%
        as.data.frame() %>% 
        set_names(c("Info")) %>% 
        t() %>% 
        as.data.frame()
      checkmate::assert_class(text, c("data.frame"))
      checkmate::assert_true(nrow(text) == 1)
      
      weather <- text %>% select(station_id, latitude, longitude, 
                                 observation_time, 
                                 temperature_string, weather, wind_mph, wind_degrees)
      checkmate::assert_class(weather, c("data.frame"))
      checkmate::assert_true(nrow(weather) == 1)
      
      return(weather)
    }
    station_id <- "KAMW"
    cw <- current_weather(station_id)
    print(cw)

    ##      station_id latitude longitude
    ## Info       KAMW 41.99056 -93.61889
    ##                              observation_time temperature_string
    ## Info Last Updated on Apr 2 2019, 10:53 am CDT     39.0 F (3.9 C)
    ##            weather wind_mph wind_degrees
    ## Info Mostly Cloudy     10.4          300

1.  Which HTML tags did you investigate? Describe how to format at least
    3 separate pieces of a document using HTML tags.

-   HTML The class Attribute: The HTML class attribute is used to define
    equal styles for elements with the same class name. So, all HTML
    elements with the same class attribute will have the same format and
    style. All element can be assigned with with class attribute.

<!-- -->

    <!DOCTYPE html>
    <html>
    <head>
    <style>
    span.note {
      font-size: 120%;
      color: red;
    }
    </style>
    </head>
    <body>

    <h1>My <span class="note">Important</span> Heading</h1>
    <p>This is some <span class="note">important</span> text.</p>

    </body>
    </html>

-   HTML Styles - CSS: Cascading Style Sheets. can be added to HTML
    elements in Inline, Internal, External. It is used to describes how
    HTML elements are to be displayed on screen, paper, or in other
    media. It save a lot of work by taking over some use of HTML `style`
    attribute

<!-- -->

    <h1 style="color:blue;">This is a Blue Heading</h1>

-   HTML Tables: the HTML has the `th` element for table header, the
    `tr` element for table row, the `caption` element for caption of the
    table. All the element can be describes be CSS.

<!-- -->

    <!DOCTYPE html>
    <html>
    <body>

    <h2>Basic HTML Table</h2>

    <table style="width:100%">
      <tr>
        <th>Firstname</th>
        <th>Lastname</th> 
        <th>Age</th>
      </tr>
      <tr>
        <td>Jill</td>
        <td>Smith</td>
        <td>50</td>
      </tr>
      <tr>
        <td>Eve</td>
        <td>Jackson</td>
        <td>94</td>
      </tr>
      <tr>
        <td>John</td>
        <td>Doe</td>
        <td>80</td>
      </tr>
    </table>

    </body>
    </html>

1.  Compile this Rmarkdown document to HTML, then open the HTML file in
    a web browser. Open the inspector console for your browser
    (Ctrl-Shift-I in Chrome, Ctrl-Shift-C in Firefox) and look at the
    HTML code corresponding to various parts of the document. <br>
    Answer the following questions:

What types of tags did you find?

-   &lt;html&gt;: define the whole
-   &lt;h1&gt;, &lt;h4&gt;: heading for title and author's name
-   &lt;body&gt;: main
-   &lt;div&gt;: division
-   &lt;li&gt;: list
-   &lt;p&gt;: paragraph
-   &lt;ul&gt;: I guess unit list?
-   &lt;pre&gt;: parent node of the `code` node
-   &lt;code&gt;: code chunk

How are code chunks formatted in HTML?

-   It use &lt;pre class=“r”&gt; or &lt;pre class=“txt”&gt; depend on
    the designate formate of the code chunk.

What differences are there in the HTML markup for R code chunks and R
output blocks?

-   R output blocks is formated with paragrahp using &lt;p&gt;
-   R code chunks is formated with &lt;pre&gt; and &lt;code&gt;

1.  In R, the `rvest` package, which is part of the tidyverse, makes it
    (relatively) easy to pull specific pieces from structured documents.
    The `html_nodes` function selects nodes using either xpath or css,
    and additional functions such as `html_attrs`, `html_text`, and
    `html_table` pull information out of the markup text.<br> Choose a
    Wikipedia page that has at least one image to test the `rvest`
    package out

<!-- -->

    url <- "https://en.wikipedia.org/wiki/List_of_cognitive_biases"
    html <- read_html(url)

    listTable <- html %>% html_nodes(".wikitable") %>% html_table() # scrape table
    tempname <- html %>% html_nodes(".mw-headline") %>% html_text # scrape table name
    tempname <-  gsub('([[:punct:]])|\\s+','_',tempname)
    for (i in 1:3) assign(tempname[i], listTable[[i]]) # assign name to each table
    # view table
    # str(listTable)
    head(get(tempname[1]))

    ##                                  Name
    ## 1                    Ambiguity effect
    ## 2               Anchoring or focalism
    ## 3            Anthropocentric thinking
    ## 4 Anthropomorphism or personification
    ## 5                    Attentional bias
    ## 6                     Automation bias
    ##                                                                                                                                                                            Description
    ## 1                                                                                       The tendency to avoid options for which the probability of a favorable outcome is unknown.[10]
    ## 2 The tendency to rely too heavily, or "anchor", on one trait or piece of information when making decisions (usually the first piece of information acquired on that subject).[11][12]
    ## 3                                                                   The tendency to use human analogies as a basis for reasoning about other, less familiar, biological phenomena.[13]
    ## 4                                                  The tendency to characterize animals, objects, and abstract concepts as possessing human-like traits, emotions, and intentions.[14]
    ## 5                                                                                                                 The tendency of perception to be affected by recurring thoughts.[15]
    ## 6                                          The tendency to depend excessively on automated systems which can lead to erroneous automated information overriding correct decisions.[16]
=======
---
title: "A Series of Tubes..."
author: "Weiquan Luo"
topic: "09"
layout: post
root: ../../../
output: 
  html_document: 
    # css: extra.css
---


```r
library(xml2)
library(tidyverse)
library(checkmate)
library(rvest)
```

1. The `xml2` R package can be used to work with xml files. Write a function, `current_weather` that accepts a 4-letter airport code (KAMW in the URL here: https://w1.weather.gov/xml/current_obs/KAMW.xml) and returns a data frame with the airport location (station ID, latitude, longitude), last update time, and current weather information (temperature, weather condition, wind speed and direction) at that airport. The `xml2` functions `read_xml`, `xml_children`, `xml_name`, and `xml_text` will be useful. Remember to handle errors and check inputs, and make sure to return a data frame with appropriate data types. 


```r
station_id <- "KAMW"
current_weather <- function(station_id){
  url <- paste0("https://w1.weather.gov/xml/current_obs/", station_id ,".xml")
  xml <- try(read_xml(url))
  checkmate::assert_class(xml, c("xml_document", "xml_node"))
  
  nodeset <- xml_children(xml)
  checkmate::assert_class(nodeset, c("xml_nodeset"))
  
  tempname <- xml_name(xml_children(xml))
  text <- lapply(tempname, function(x) xml_text(xml_find_all(nodeset, paste0("//",x)))) %>% 
    unlist() %>% 
    set_names(tempname) %>%
    as.data.frame() %>% 
    set_names(c("Info")) %>% 
    t() %>% 
    as.data.frame()
  checkmate::assert_class(text, c("data.frame"))
  checkmate::assert_true(nrow(text) == 1)
  
  weather <- text %>% select(station_id, latitude, longitude, 
                             observation_time, 
                             temperature_string, weather, wind_mph, wind_degrees)
  checkmate::assert_class(weather, c("data.frame"))
  checkmate::assert_true(nrow(weather) == 1)
  
  return(weather)
}
station_id <- "KAMW"
cw <- current_weather(station_id)
print(cw)
```

```
##      station_id latitude longitude
## Info       KAMW 41.99056 -93.61889
##                              observation_time temperature_string  weather
## Info Last Updated on Apr 3 2019, 12:53 pm CDT    54.0 F (12.2 C) Overcast
##      wind_mph wind_degrees
## Info      9.2          180
```

2. Which HTML tags did you investigate? Describe how to format at least 3 separate pieces of a document using HTML tags.

* HTML The class Attribute: The HTML class attribute is used to define equal styles for elements with the same class name. So, all HTML elements with the same class attribute will have the same format and style. All element can be assigned with with class attribute. 

```{.txt}
<!DOCTYPE html>
<html>
<head>
<style>
span.note {
  font-size: 120%;
  color: red;
}
</style>
</head>
<body>

<h1>My <span class="note">Important</span> Heading</h1>
<p>This is some <span class="note">important</span> text.</p>

</body>
</html>
```

* HTML Styles - CSS: Cascading Style Sheets. can be added to HTML elements in Inline, Internal, External. It is used to describes how HTML elements are to be displayed on screen, paper, or in other media. It save a lot of work by taking over some use of HTML `style` attribute

```{.txt}
<h1 style="color:blue;">This is a Blue Heading</h1>
```


* HTML Tables: the HTML has the `th` element for table header, the `tr` element for table row, the `caption`  element for caption of the table. All the element can be describes be CSS.

```{.txt}
<!DOCTYPE html>
<html>
<body>

<h2>Basic HTML Table</h2>

<table style="width:100%">
  <tr>
    <th>Firstname</th>
    <th>Lastname</th> 
    <th>Age</th>
  </tr>
  <tr>
    <td>Jill</td>
    <td>Smith</td>
    <td>50</td>
  </tr>
  <tr>
    <td>Eve</td>
    <td>Jackson</td>
    <td>94</td>
  </tr>
  <tr>
    <td>John</td>
    <td>Doe</td>
    <td>80</td>
  </tr>
</table>

</body>
</html>
```
3. Compile this Rmarkdown document to HTML, then open the HTML file in a web browser. Open the inspector console for your browser (Ctrl-Shift-I in Chrome, Ctrl-Shift-C in Firefox) and look at the HTML code corresponding to various parts of the document. <br>
Answer the following questions:

 What types of tags did you find? 
    
* \<html>: define the whole
* \<h1>, \<h4>: heading for title and author\'s name
* \<body>: main
* \<div>: division
* \<li>: list
* \<p>: paragraph
* \<ul>: I guess unit list? 
* \<pre>: parent node of the `code` node
* \<code>: code chunk
    
 How are code chunks formatted in HTML?
    
* It use  \<pre class="r"> or  \<pre class="txt"> depend on the designate formate of the code chunk.

 What differences are there in the HTML markup for R code chunks and R output blocks?
    
* R output blocks is formated with paragrahp using \<p>
* R code chunks is formated with \<pre> and \<code>
    
4. In R, the `rvest` package, which is part of the tidyverse, makes it (relatively) easy to pull specific pieces from structured documents. The `html_nodes` function selects nodes using either xpath or css, and additional functions such as `html_attrs`, `html_text`, and `html_table` pull information out of the markup text.<br>
Choose a Wikipedia page that has at least one image to test the `rvest` package out


```r
url <- "https://en.wikipedia.org/wiki/List_of_cognitive_biases"
html <- read_html(url)

listTable <- html %>% html_nodes(".wikitable") %>% html_table() # scrape table
tempname <- html %>% html_nodes(".mw-headline") %>% html_text # scrape table name
tempname <-  gsub('([[:punct:]])|\\s+','_',tempname)
for (i in 1:3) assign(tempname[i], listTable[[i]]) # assign name to each table
# view table
# str(listTable)
head(get(tempname[1]))
```

```
##                                  Name
## 1                    Ambiguity effect
## 2               Anchoring or focalism
## 3            Anthropocentric thinking
## 4 Anthropomorphism or personification
## 5                    Attentional bias
## 6                     Automation bias
##                                                                                                                                                                            Description
## 1                                                                                       The tendency to avoid options for which the probability of a favorable outcome is unknown.[10]
## 2 The tendency to rely too heavily, or "anchor", on one trait or piece of information when making decisions (usually the first piece of information acquired on that subject).[11][12]
## 3                                                                   The tendency to use human analogies as a basis for reasoning about other, less familiar, biological phenomena.[13]
## 4                                                  The tendency to characterize animals, objects, and abstract concepts as possessing human-like traits, emotions, and intentions.[14]
## 5                                                                                                                 The tendency of perception to be affected by recurring thoughts.[15]
## 6                                          The tendency to depend excessively on automated systems which can lead to erroneous automated information overriding correct decisions.[16]
```


>>>>>>> blog 9 posts up
