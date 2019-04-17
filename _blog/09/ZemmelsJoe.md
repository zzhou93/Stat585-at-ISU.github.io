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
    library(tidyverse)

    current_weather <- function(code){
      checkmate::assertCharacter(code)
      
      weatherData <- read_xml(paste0("https://w1.weather.gov/xml/current_obs/",code,".xml")) %>%
        xml_children() %>%
        xml_text() %>%
        .[c(7,8,9,11,14,18,20)] %>%
        t() %>%
        data.frame() %>%
        setNames(c("stationID","lat","long","lastUpdate","temp(F)","windDirection","windSpeed(MPH)"))
      
      checkmate::assertDataFrame(weatherData,types = c("numeric", "factor"), min.rows = 1, col.names = "named")
      weatherData
    }

    current_weather("KAMW")

    ##   stationID      lat      long                      lastUpdate temp(F)
    ## 1      KAMW 41.99056 -93.61889 Tue, 02 Apr 2019 10:53:00 -0500    39.0
    ##   windDirection windSpeed(MPH)
    ## 1     Northwest           10.4

    current_weather("KSTP") #downtown St. Paul code

    ##   stationID      lat      long                      lastUpdate temp(F)
    ## 1      KSTP 44.93237 -93.05588 Tue, 02 Apr 2019 10:53:00 -0500    41.0
    ##   windDirection windSpeed(MPH)
    ## 1     Southwest           11.5

1.  Which HTML tags did you investigate? Describe how to format at least
    3 separate pieces of a document using HTML tags.
=======
---
title: "A Series of Tubes..."
author: "Joe Zemmels"
topic: "09"
layout: post
root: ../../../
output: 
  html_document: 
    css: extra.css
---

1. The `xml2` R package can be used to work with xml files. Write a function, `current_weather` that accepts a 4-letter airport code (KAMW in the URL here: https://w1.weather.gov/xml/current_obs/KAMW.xml) and returns a data frame with the airport location (station ID, latitude, longitude), last update time, and current weather information (temperature, weather condition, wind speed and direction) at that airport. The `xml2` functions `read_xml`, `xml_children`, `xml_name`, and `xml_text` will be useful. Remember to handle errors and check inputs, and make sure to return a data frame with appropriate data types. 


```r
library(xml2)
library(tidyverse)

current_weather <- function(code){
  checkmate::assertCharacter(code)
  
  weatherData <- read_xml(paste0("https://w1.weather.gov/xml/current_obs/",code,".xml")) %>%
    xml_children() %>%
    xml_text() %>%
    .[c(7,8,9,11,14,18,20)] %>%
    t() %>%
    data.frame() %>%
    setNames(c("stationID","lat","long","lastUpdate","temp(F)","windDirection","windSpeed(MPH)"))
  
  checkmate::assertDataFrame(weatherData,types = c("numeric", "factor"), min.rows = 1, col.names = "named")
  weatherData
}

current_weather("KAMW")
```

```
##   stationID      lat      long                      lastUpdate temp(F)
## 1      KAMW 41.99056 -93.61889 Wed, 03 Apr 2019 12:53:00 -0500    54.0
##   windDirection windSpeed(MPH)
## 1         South            9.2
```

```r
current_weather("KSTP") #downtown St. Paul code
```

```
##   stationID      lat      long                      lastUpdate temp(F)
## 1      KSTP 44.93237 -93.05588 Wed, 03 Apr 2019 12:53:00 -0500    46.0
##   windDirection windSpeed(MPH)
## 1          West            8.1
```

2. Which HTML tags did you investigate? Describe how to format at least 3 separate pieces of a document using HTML tags.
>>>>>>> blog 9 posts up

Color:

<!--html_preserve-->
<<<<<<< HEAD
<h1 style="background-color:rgb(60, 179, 113);color:Yellow;border:10px dashed #F10909">
Joe is cool.
</h1>
<!--/html_preserve-->
Links: <!--html_preserve-->
=======
<h1 style="background-color:rgb(60, 179, 113);color:Yellow;border:10px dashed #F10909">Joe is cool.</h1>
<!--/html_preserve-->

Links:
<!--html_preserve-->
>>>>>>> blog 9 posts up
<style>
a:link, a:visited {
  background-color: rgb(60, 179, 113);
  color: white;
  padding: 15px 25px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
}

a:hover, a:active {
  background-color: #F10909;
}
</style>
<<<<<<< HEAD
<a href="https://jzemmels.github.io" target="_blank">Cool dude’s
website</a> <!--/html_preserve-->
=======

<a href="https://jzemmels.github.io" target="_blank">Cool dude's website</a>
<!--/html_preserve-->
>>>>>>> blog 9 posts up

Tables:

<!--html_preserve-->
<table style="width:50%">
<<<<<<< HEAD
<tr>
<th>
Language
</th>
<th>
Fact
</th>
</tr>
<tr>
<td>
English
</td>
<td>
Joe is cool.
</td>
</tr>
<tr>
<td>
Spanish
</td>
<td>
Joe es guay.
</td>
</tr>
<tr>
<td>
Yoda
</td>
<td>
Cool Joe is.
</td>
</tr>
</table>
<!--/html_preserve-->
1.  Compile this Rmarkdown document to HTML, then open the HTML file in
    a web browser. Open the inspector console for your browser
    (Ctrl-Shift-I in Chrome, Ctrl-Shift-C in Firefox) and look at the
    HTML code corresponding to various parts of the document. <br>
    Answer the following questions:

    -   What types of tags did you find?

    I found tags including line height, which appears to remove line
    spacing in text, width, which removes horizontal spacing in the
    table I created above, and font size, which changes the font size to
    some default, smaller font size.

    -   How are code chunks formatted in HTML?

    It appears like R code chunks are formatted with pre class=“r” tags.
    Within these tags are style parameters including “background color”,
    which is a light gray, and “border”, which defines the 1 pixel, dark
    gray border around the code chunk. The actual text is stored within
    a span class=“hljs” tag, which has a number of style parameters to
    indicate the color and emphasis of the text.

    -   What differences are there in the HTML markup for R code chunks
        and R output blocks?

    Code output blocks are stored in a pre tag and the text in another
    code class=“hljs” tag. The style parameters are similar to the R
    code chunks except for, for example, changing the background color
    to be transparent rather than the light gray.

2.  In R, the `rvest` package, which is part of the tidyverse, makes it
    (relatively) easy to pull specific pieces from structured documents.
    The `html_nodes` function selects nodes using either xpath or css,
    and additional functions such as `html_attrs`, `html_text`, and
    `html_table` pull information out of the markup text.<br> Choose a
    Wikipedia page that has at least one image to test the `rvest`
    package out

<!-- -->

    library(rvest)
    joe_cool <- read_html("https://en.wikipedia.org/wiki/Joe_Cool_(song)")

    html_node(joe_cool,"img") %>% 
      xml_attr(attr="src") %>%
      paste0("https:",.) %>%
      magick::image_read()

<img src="../figure/09/ZemmelsJoe/unnamed-chunk-2-1.png" width="220" />

    html_nodes(joe_cool,"table")[3] %>%
      html_attr("class")

    ## [1] "tracklist"

    html_nodes(joe_cool,"table")[3] %>%
      html_table()

    ## [[1]]
    ##   No.       Title      Writer(s) Length
    ## 1   1  "Joe Cool" Sherry Rich[1]   3:23
    ## 2   2 "Egomaniac"  Anne McCue[3]   3:38

Remember, just because you have the HTML file doesn’t mean you should
commit it to your git repository!!! Delete the HTML file now if you’re
going to be tempted to accidentally commit and push it.

------------------------------------------------------------------------

### Going further (Optional Reading): Dynamic Web Pages - Javascript, AJAX, PHP, ASP, and more!

Not all web pages are the same. Static web pages have content that is
pre-specified, and when the page is loaded all of the content is just…
there. These pages are the easiest to scrape, because the HTML file
already contains all of the information needed to render the page.
Dynamic web pages have a basic HTML layout, and then scripting languages
are used to inject content into the pages at some point after the
initial page loads. Using `xml2::read_html()` on these pages will get
you a different HTML file than the one you see when loading the page in
your browser.

If you are interested in learning more about how to scrape dynamic web
pages, take a look at the `Rselenium` or `splashR` packages. These
packages emulate a browser (or launch one for you to control using R),
allowing the scripting languages to inject page content before providing
you with the updated HTML file containing the information you actually
wanted in the first place.

Note: Not all websites which use javascript (or other scripting
languages) are difficult to scrape (at this point, practically every web
page uses javascript somewhere), but when javascript is used to inject
data from a database after the page initially loads, it’s likely that
you’ll have to do a bit more work to get at the data.
=======
  <tr>
    <th>Language</th>
    <th>Fact</th>
  </tr>
  <tr>
    <td>English</td>
    <td>Joe is cool.</td>
  </tr>
  <tr>
    <td>Spanish</td>
    <td>Joe es guay.</td>
  </tr>
  <tr>
    <td>Yoda</td>
    <td>Cool Joe is.</td>
  </tr>
</table>
<!--/html_preserve-->

3. Compile this Rmarkdown document to HTML, then open the HTML file in a web browser. Open the inspector console for your browser (Ctrl-Shift-I in Chrome, Ctrl-Shift-C in Firefox) and look at the HTML code corresponding to various parts of the document. <br>
Answer the following questions:

    - What types of tags did you find? 
    
    I found tags including line height, which appears to remove line spacing in text, width, which removes horizontal spacing in the table I created above, and font size, which changes the font size to some default, smaller font size.

    - How are code chunks formatted in HTML?
    
    It appears like R code chunks are formatted with pre class="r" tags. Within these tags are style parameters including "background color", which is a light gray, and "border", which defines the 1 pixel, dark gray border around the code chunk. The actual text is stored within a span class="hljs" tag, which has a number of style parameters to indicate the color and emphasis of the text.

    - What differences are there in the HTML markup for R code chunks and R output blocks?
    
    Code output blocks are stored in a pre tag and the text in another code class="hljs" tag. The style parameters are similar to the R code chunks except for, for example, changing the background color to be transparent rather than the light gray.
    
    
4. In R, the `rvest` package, which is part of the tidyverse, makes it (relatively) easy to pull specific pieces from structured documents. The `html_nodes` function selects nodes using either xpath or css, and additional functions such as `html_attrs`, `html_text`, and `html_table` pull information out of the markup text.<br>
Choose a Wikipedia page that has at least one image to test the `rvest` package out


```r
library(rvest)
joe_cool <- read_html("https://en.wikipedia.org/wiki/Joe_Cool_(song)")

html_node(joe_cool,"img") %>% 
  xml_attr(attr="src") %>%
  paste0("https:",.) %>%
  magick::image_read()
```

![center](./../figure/09/ZemmelsJoe/unnamed-chunk-2-1.png)

```r
html_nodes(joe_cool,"table")[3] %>%
  html_attr("class")
```

```
## [1] "tracklist"
```

```r
html_nodes(joe_cool,"table")[3] %>%
  html_table()
```

```
## [[1]]
##   No.       Title      Writer(s) Length
## 1   1  "Joe Cool" Sherry Rich[1]   3:23
## 2   2 "Egomaniac"  Anne McCue[3]   3:38
```

Remember, just because you have the HTML file doesn't mean you should commit it to your git repository!!! Delete the HTML file now if you're going to be tempted to accidentally commit and push it.

---

### Going further (Optional Reading): Dynamic Web Pages - Javascript, AJAX, PHP, ASP, and more!

Not all web pages are the same. Static web pages have content that is pre-specified, and when the page is loaded all of the content is just... there. These pages are the easiest to scrape, because the HTML file already contains all of the information needed to render the page. Dynamic web pages have a basic HTML layout, and then scripting languages are used to inject content into the pages at some point after the initial page loads. Using `xml2::read_html()` on these pages will get you a different HTML file than the one you see when loading the page in your browser. 

If you are interested in learning more about how to scrape dynamic web pages, take a look at the `Rselenium` or `splashR` packages. These packages emulate a browser (or launch one for you to control using R), allowing the scripting languages to inject page content before providing you with the updated HTML file containing the information you actually wanted in the first place.

Note: Not all websites which use javascript (or other scripting languages) are difficult to scrape (at this point, practically every web page uses javascript somewhere), but when javascript is used to inject data from a database after the page initially loads, it's likely that you'll have to do a bit more work to get at the data. 
>>>>>>> blog 9 posts up
