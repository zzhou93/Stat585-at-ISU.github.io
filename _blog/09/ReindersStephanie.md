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

    ##   station_id longitude latitude    observation_time temperature
    ## 1       KAMW -93.61889 41.99056 2019-04-02 10:53:00          39
    ##   weather_condition wind_speed direction
    ## 1     Mostly Cloudy       10.4 Northwest

1.  Which HTML tags did you investigate? Describe how to format at least
    3 separate pieces of a document using HTML tags.

Text can be formatted a variety of ways: - We can make text <b>
bold</b>. - We can make text <i> italic</i>. - We can
<mark>highlight</mark> text.

Pagraphs can be formatted differently.
<p>
This is the default paragraph style. Regardless of how many extra spaces
or line breaks I make when I type. This paragraph style will remove
extra spaces and ignore my line breaks.
</p>
<pre>This is a different paragraph style. It will preserve    extra     spaces  and 
  my
  line
  breaks.</pre>
=======
---
title: "A Series of Tubes..."
author: "Stephanie Reinders"
topic: "09"
layout: post
root: ../../../
output: 
  html_document: 
    css: extra.css
---

**Write a blog post answering the following questions and detailing the progress: **

1. The `xml2` R package can be used to work with xml files. Write a function, `current_weather` that accepts a 4-letter airport code (KAMW in the URL here: https://w1.weather.gov/xml/current_obs/KAMW.xml) and returns a data frame with the airport location (station ID, latitude, longitude), last update time, and current weather information (temperature, weather condition, wind speed and direction) at that airport. The `xml2` functions `read_xml`, `xml_children`, `xml_name`, and `xml_text` will be useful. Remember to handle errors and check inputs, and make sure to return a data frame with appropriate data types. 




```
##   station_id longitude latitude    observation_time temperature
## 1       KAMW -93.61889 41.99056 2019-04-03 12:53:00          54
##   weather_condition wind_speed direction
## 1          Overcast        9.2     South
```


2. Which HTML tags did you investigate? Describe how to format at least 3 separate pieces of a document using HTML tags.

Text can be formatted a variety of ways: 
    - We can make text <b> bold</b>. 
    - We can make text <i> italic</i>.
    - We can <mark>highlight</mark> text.

Pagraphs can be formatted differently.
  <p>This is the default paragraph style. Regardless of how many     extra spaces    or line breaks I 
  make when I type. This paragraph style will remove extra spaces and ignore my line breaks. </p>
  <pre>This is a different paragraph style. It will preserve    extra     spaces  and 
  my
  line
  breaks.</pre> 

>>>>>>> blog 9 posts up
Lists also have a variety of formatting options:

Basic list
<ul>
<<<<<<< HEAD
<li>
item 1
</li>
<li>
item 2
</li>
<li>
item 3
</li>
</ul>
List with open circles
<ul style="list-style-type:circle;">
<li>
item 1
</li>
<li>
item 2
</li>
<li>
item 3
</li>
</ul>
List with squares
<ul style="list-style-type:square;">
<li>
item 1
</li>
<li>
item 2
</li>
<li>
item 3
</li>
</ul>
List without bullets
<ul style="list-style-type:none;">
<li>
item 1
</li>
<li>
item 2
</li>
<li>
item 3
</li>
</ul>
1.  Compile this Rmarkdown document to HTML, then open the HTML file in
    a web browser. Open the inspector console for your browser
    (Ctrl-Shift-I in Chrome, Ctrl-Shift-C in Firefox) and look at the
    HTML code corresponding to various parts of the document. <br>
    Answer the following questions:

    -   What types of tags did you find? I found all sorts of headings
        and paragraph tags as well as quite a few `<div> </div>` tags to
        denote sections.

    -   How are code chunks formatted in HTML?

        The tags used to display the R code are
        `<pre class="r"> <code class="hljs">`

    -   What differences are there in the HTML markup for R code chunks
        and R output blocks?

        The tags used to display the R output blocks is the same as for
        the R code chucks expect it doesn’t specify ‘class = “r”’ in the
        paragraph tag
        <pre>
        .

2.  In R, the `rvest` package, which is part of the tidyverse, makes it
    (relatively) easy to pull specific pieces from structured documents.
    The `html_nodes` function selects nodes using either xpath or css,
    and additional functions such as `html_attrs`, `html_text`, and
    `html_table` pull information out of the markup text.<br> Choose a
    Wikipedia page that has at least one image to test the `rvest`
    package out

<!-- -->

    ## {xml_nodeset (1)}
    ## [1] <img alt="Page semi-protected" src="//upload.wikimedia.org/wikipedia ...

    ##                                Helen Keller
    ## 1 Helen Keller holding a magnolia, ca. 1920
    ## 2                                      Born
    ## 3                                      Died
    ## 4                             Resting place
    ## 5                                Occupation
    ## 6                                 Education
    ## 7                             Notable works
    ## 8                                          
    ## 9                                 Signature
    ##                                                             Helen Keller
    ## 1                              Helen Keller holding a magnolia, ca. 1920
    ## 2    Helen Adams Keller(1880-06-27)June 27, 1880Tuscumbia, Alabama, U.S.
    ## 3 June 1, 1968(1968-06-01) (aged 87)Arcan RidgeEaston, Connecticut, U.S.
    ## 4                          Washington National CathedralWashington, D.C.
    ## 5                                   Author, political activist, lecturer
    ## 6                                                Harvard University (BA)
    ## 7                                                   The Story of My Life
    ## 8                                                                       
    ## 9
=======
  <li>item 1</li>
  <li>item 2</li>
  <li>item 3</li>
</ul>  

List with open circles
<ul style="list-style-type:circle;">
  <li>item 1</li>
  <li>item 2</li>
  <li>item 3</li>
</ul> 

List with squares
<ul style="list-style-type:square;">
  <li>item 1</li>
  <li>item 2</li>
  <li>item 3</li>
</ul> 
  
List without bullets
<ul style="list-style-type:none;">
  <li>item 1</li>
  <li>item 2</li>
  <li>item 3</li>
</ul>  
  

3. Compile this Rmarkdown document to HTML, then open the HTML file in a web browser. Open the inspector console for your browser (Ctrl-Shift-I in Chrome, Ctrl-Shift-C in Firefox) and look at the HTML code corresponding to various parts of the document. <br>
Answer the following questions:

    - What types of tags did you find?
        I found all sorts of headings and paragraph tags as well as quite a few `<div> </div>` tags to denote sections. 

    - How are code chunks formatted in HTML?
    
      The tags used to display the R code are `<pre class="r"> <code class="hljs">`

    - What differences are there in the HTML markup for R code chunks and R output blocks?
    
      The tags used to display the R output blocks is the same as for the R code chucks expect it doesn't specify 'class = "r"' in the paragraph tag <pre>.
    
4. In R, the `rvest` package, which is part of the tidyverse, makes it (relatively) easy to pull specific pieces from structured documents. The `html_nodes` function selects nodes using either xpath or css, and additional functions such as `html_attrs`, `html_text`, and `html_table` pull information out of the markup text.<br>
Choose a Wikipedia page that has at least one image to test the `rvest` package out


```
## {xml_nodeset (1)}
## [1] <img alt="Page semi-protected" src="//upload.wikimedia.org/wikipedia ...
```


```
##                                Helen Keller
## 1 Helen Keller holding a magnolia, ca. 1920
## 2                                      Born
## 3                                      Died
## 4                             Resting place
## 5                                Occupation
## 6                                 Education
## 7                             Notable works
## 8                                          
## 9                                 Signature
##                                                             Helen Keller
## 1                              Helen Keller holding a magnolia, ca. 1920
## 2    Helen Adams Keller(1880-06-27)June 27, 1880Tuscumbia, Alabama, U.S.
## 3 June 1, 1968(1968-06-01) (aged 87)Arcan RidgeEaston, Connecticut, U.S.
## 4                          Washington National CathedralWashington, D.C.
## 5                                   Author, political activist, lecturer
## 6                                                Harvard University (BA)
## 7                                                   The Story of My Life
## 8                                                                       
## 9
```

>>>>>>> blog 9 posts up
