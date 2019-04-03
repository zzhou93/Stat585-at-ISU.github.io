<<<<<<< HEAD
**Write a blog post answering the following questions and detailing the
progress: ** 1. The `xml2` R package can be used to work with xml files.
Write a function, `current_weather` that accepts a 4-letter airport code
(KAMW in the URL here:
<a href="https://w1.weather.gov/xml/current_obs/KAMW.xml" class="uri">https://w1.weather.gov/xml/current_obs/KAMW.xml</a>)
and returns a data frame with the airport location (station ID,
latitude, longitude), last update time, and current weather information
(temperature, weather condition, wind speed and direction) at that
airport. The `xml2` functions `read_xml`, `xml_children`, `xml_name`,
and `xml_text` will be useful. Remember to handle errors and check
inputs, and make sure to return a data frame with appropriate data
types.

    library("xml2")
    library("dplyr")
    library("checkmate")

    current_weather <- function(code) {
      checkmate::assert_string(code, pattern = "^[A-Z]{4}$")
      url <- paste0("https://w1.weather.gov/xml/current_obs/", code, ".xml")
      xml <- read_xml(url)
      df <- xml %>% 
        xml_children() %>% 
        {setNames(object = xml_text(.), xml_name(.))} %>% 
        t() %>% data.frame(stringsAsFactors = F) %>% 
        select(station_id, latitude, longitude, observation_time, 
               temp_c, weather, wind_mph, wind_dir) %>%
        mutate(latitude = as.numeric(latitude),
               longitude = as.numeric(longitude),
               temp_c = as.numeric(temp_c),
               wind_mph = as.numeric(wind_mph))
      checkmate::checkDataFrame(df, nrows = 1, ncols = 8)
      return(df)
    }
    df <- current_weather("KAMW")
    df %>% knitr::kable()

<table>
<thead>
<tr class="header">
<th style="text-align: left;">station_id</th>
<th style="text-align: right;">latitude</th>
<th style="text-align: right;">longitude</th>
<th style="text-align: left;">observation_time</th>
<th style="text-align: right;">temp_c</th>
<th style="text-align: left;">weather</th>
<th style="text-align: right;">wind_mph</th>
<th style="text-align: left;">wind_dir</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: left;">KAMW</td>
<td style="text-align: right;">41.99056</td>
<td style="text-align: right;">-93.61889</td>
<td style="text-align: left;">Last Updated on Apr 2 2019, 10:53 am CDT</td>
<td style="text-align: right;">3.9</td>
<td style="text-align: left;">Mostly Cloudy</td>
<td style="text-align: right;">10.4</td>
<td style="text-align: left;">Northwest</td>
</tr>
</tbody>
</table>

1.  Which HTML tags did you investigate? Describe how to format at least
    3 separate pieces of a document using HTML tags.

I looked into `Headings`, `Paragraphs`, and `Comments`. Here is a mini
example to demostrate the usage of these three tags:

—–start of example—–

&lt;!DOCTYPE html&gt;
<html>
<body>
<h1>
STAT 585 BLOG 9
</h1>
<p>
It is useful to develop a basic vocabulary and understanding of these
languages before attempting to interact with (messy) data stored on the
internet.
</p>
<!-- Remember to add more instructions here -->
</body>
</html>
—–end of example—–

1.  Compile this Rmarkdown document to HTML, then open the HTML file in
    a web browser. Open the inspector console for your browser
    (Ctrl-Shift-I in Chrome, Ctrl-Shift-C in Firefox) and look at the
    HTML code corresponding to various parts of the document. <br>
    Answer the following questions:
    -   What types of tags did you find?

        &lt;head&gt;, &lt;body&gt;, &lt;div&gt;, &lt;style&gt;,
        &lt;pre&gt;, etc.

    -   How are code chunks formatted in HTML?

        The code chunks are written under tags &lt;pre class=“r”&gt;
        whose elements include &lt;code&gt;, &lt;span&gt;.

    -   What differences are there in the HTML markup for R code chunks
        and R output blocks?

        The tags for outputs are &lt;pre&gt;, which do not specify the
        attributes like code chunks do.

2.  In R, the `rvest` package, which is part of the tidyverse, makes it
    (relatively) easy to pull specific pieces from structured documents.
    The `html_nodes` function selects nodes using either xpath or css,
    and additional functions such as `html_attrs`, `html_text`, and
    `html_table` pull information out of the markup text.<br> Choose a
    Wikipedia page that has at least one image to test the `rvest`
    package out Remember, just because you have the HTML file doesn’t
    mean you should commit it to your git repository!!! Delete the HTML
    file now if you’re going to be tempted to accidentally commit and
    push it.

<!-- -->

    library("rvest")
    url <- "https://en.wikipedia.org/wiki/Shiba_Inu"
    shiba <- read_html(url) %>% html_nodes(".image img") %>% html_attr("src")
    knitr::include_graphics(shiba[1])

![](//upload.wikimedia.org/wikipedia/commons/thumb/6/6b/Taka_Shiba.jpg/220px-Taka_Shiba.jpg)
=======
---
title: "A Series of Tubes..."
author: "Min Zhang"
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
library("xml2")
library("dplyr")
library("checkmate")

current_weather <- function(code) {
  checkmate::assert_string(code, pattern = "^[A-Z]{4}$")
  url <- paste0("https://w1.weather.gov/xml/current_obs/", code, ".xml")
  xml <- read_xml(url)
  df <- xml %>% 
    xml_children() %>% 
    {setNames(object = xml_text(.), xml_name(.))} %>% 
    t() %>% data.frame(stringsAsFactors = F) %>% 
    select(station_id, latitude, longitude, observation_time, 
           temp_c, weather, wind_mph, wind_dir) %>%
    mutate(latitude = as.numeric(latitude),
           longitude = as.numeric(longitude),
           temp_c = as.numeric(temp_c),
           wind_mph = as.numeric(wind_mph))
  checkmate::checkDataFrame(df, nrows = 1, ncols = 8)
  return(df)
}
df <- current_weather("KAMW")
df %>% knitr::kable()
```



|station_id | latitude| longitude|observation_time                         | temp_c|weather  | wind_mph|wind_dir |
|:----------|--------:|---------:|:----------------------------------------|------:|:--------|--------:|:--------|
|KAMW       | 41.99056| -93.61889|Last Updated on Apr 3 2019, 12:53 pm CDT |   12.2|Overcast |      9.2|South    |


2. Which HTML tags did you investigate? Describe how to format at least 3 separate pieces of a document using HTML tags.

I looked into `Headings`, `Paragraphs`, and `Comments`. Here is a mini example to demostrate the usage of these three tags:

-----start of example-----

<!DOCTYPE html>
<html>
<body>

<h1>STAT 585 BLOG 9</h1>
<p>It is useful to develop a basic vocabulary and understanding of these languages before attempting to interact with (messy) data stored on the internet.</p>

<!-- Remember to add more instructions here -->

</body>
</html>

-----end of example-----

3. Compile this Rmarkdown document to HTML, then open the HTML file in a web browser. Open the inspector console for your browser (Ctrl-Shift-I in Chrome, Ctrl-Shift-C in Firefox) and look at the HTML code corresponding to various parts of the document. <br>
Answer the following questions:
    - What types of tags did you find? 
    
      \<head\>, \<body\>, \<div\>, \<style\>, \<pre\>, etc. 
    
    - How are code chunks formatted in HTML?
    
      The code chunks are written under tags \<pre class="r"\> whose elements include \<code\>, \<span\>.
      
    - What differences are there in the HTML markup for R code chunks and R output blocks?
    
      The tags for outputs are \<pre\>, which do not specify the attributes like code chunks do. 
    
4. In R, the `rvest` package, which is part of the tidyverse, makes it (relatively) easy to pull specific pieces from structured documents. The `html_nodes` function selects nodes using either xpath or css, and additional functions such as `html_attrs`, `html_text`, and `html_table` pull information out of the markup text.<br>
Choose a Wikipedia page that has at least one image to test the `rvest` package out
Remember, just because you have the HTML file doesn't mean you should commit it to your git repository!!! Delete the HTML file now if you're going to be tempted to accidentally commit and push it.


```r
library("rvest")
url <- "https://en.wikipedia.org/wiki/Shiba_Inu"
shiba <- read_html(url) %>% html_nodes(".image img") %>% html_attr("src")
knitr::include_graphics(shiba[1])
```

![center](.///upload.wikimedia.org/wikipedia/commons/thumb/6/6b/Taka_Shiba.jpg/220px-Taka_Shiba.jpg)
>>>>>>> blog 9 posts up
