---
title: "A Series of Tubes..."
author: "Firstname Lastname"
topic: "09"
layout: post
root: ../../../
output: 
  html_document: 
    css: extra.css
---

The internet may not be [a series of tubes](https://en.wikipedia.org/wiki/Series_of_tubes), but it is made up of a number of different programming and markup languages. It is useful to develop a basic vocabulary and understanding of these languages before attempting to interact with (messy) data stored on the internet. 

<div class="click-to-top">
<a href="https://www.xkcd.com/1144/"><img src="https://imgs.xkcd.com/comics/tags.png" alt="XKCD comic: HTML Tags" /></a>
<span>\<A\>: Like \</a\>this.\&nbsp;"</span>
</div>

As the reading material for this week, you are asked to read through a set of websites on XML and HTML:

- **XML (eXtensible Markup Language):**
XML is a generic markup framework. Many different common file types are based on or related to XML structure (for instance, .docx, .xlsx, .html) <bR>
Read the following sections of w3schools.com's Introduction to XML:

    - [XML Introduction](https://www.w3schools.com/xml/xml_whatis.asp)
    - [XML How to Use](https://www.w3schools.com/xml/xml_usedfor.asp)
    - [XML Tree](https://www.w3schools.com/xml/xml_tree.asp)
    - [XML Syntax](https://www.w3schools.com/xml/xml_syntax.asp)
    - [XML Elements](https://www.w3schools.com/xml/xml_elements.asp)
    - [XML Attributes](https://www.w3schools.com/xml/xml_attributes.asp)

- **HTML (HyperText Markup Language):** HTML focuses on the display of information in a document format. XML is a much more general framework, but most of the concepts (tags, attributes, elements) apply directly to HTML. Open up the [w3schools HTML page](https://www.w3schools.com/html/default.asp) and read the introduction, then look through a few topics in the tutorial that interest you. 


Write a blog post answering the following questions and detailing the progress: 

1. **Describe the difference between formats png, svg, and pdf. State your sources with (working!) links (take a look at the RMarkdown cheatsheet for RStudio to learn how to make working links). Make one plot in ggplot2 and save it (using R code) in each of the three file formats you discussed. Comment on the differences you observe in their usage.**
2. **Use `magick` functionality to create an image to be used for a hex sticker.**  package `hexSticker` can help you to get started on dimensions of the sticker. **Include all code necessary to produce your sticker.** In case you are using local images, post those in a folder on **your** website and use the URL to link to them.


---


The `xml2` R package can be used to work with xml files: 

```r
library(xml2)
read_xml("https://w1.weather.gov/xml/current_obs/KAMW.xml")
```

```
## {xml_document}
## <current_observation version="1.0" noNamespaceSchemaLocation="http://www.weather.gov/view/current_observation.xsd" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
##  [1] <credit>NOAA's National Weather Service</credit>
##  [2] <credit_URL>http://weather.gov/</credit_URL>
##  [3] <image>\n  <url>http://weather.gov/images/xml_logo.gif</url>\n  <ti ...
##  [4] <suggested_pickup>15 minutes after the hour</suggested_pickup>
##  [5] <suggested_pickup_period>60</suggested_pickup_period>
##  [6] <location>Ames, Ames Municipal Airport, IA</location>
##  [7] <station_id>KAMW</station_id>
##  [8] <latitude>41.99056</latitude>
##  [9] <longitude>-93.61889</longitude>
## [10] <observation_time>Last Updated on Apr 3 2019, 12:53 pm CDT</observa ...
## [11] <observation_time_rfc822>Wed, 03 Apr 2019 12:53:00 -0500</observati ...
## [12] <weather>Overcast</weather>
## [13] <temperature_string>54.0 F (12.2 C)</temperature_string>
## [14] <temp_f>54.0</temp_f>
## [15] <temp_c>12.2</temp_c>
## [16] <relative_humidity>45</relative_humidity>
## [17] <wind_string>South at 9.2 MPH (8 KT)</wind_string>
## [18] <wind_dir>South</wind_dir>
## [19] <wind_degrees>180</wind_degrees>
## [20] <wind_mph>9.2</wind_mph>
## ...
```

Write a function, `current_weather` that accepts a 4-letter airport code (KAMW in the code above) and returns a data frame with the airport location (station ID, latitude, longitude), last update time, and current weather information (temperature, weather condition, wind speed and direction) at that airport. The `xml2` functions `read_xml`, `xml_children`, `xml_name`, and `xml_text` will be useful. Remember to handle errors and check inputs, and make sure to return a data frame with appropriate data types. 


```r
library(tidyverse)
get_current_weather <- function(airport = "KAMW") {
  # Return a data frame with at least the following columns, properly formatted:
  # - location(chr)
  # - station_id(chr)
  # - latitude(num)
  # - longitude(num)
  # - weather(chr) (e.g. "Fair")
  # - temp_f(num)
  # - wind_mph(num)
  # - windchill_f(num)
  # - observation_time(POSIXct)
}
```



```r
library(tidyverse)
get_current_weather <- function(airport = "KAMW") {
  checkmate::check_character(x = airport, min.chars = 4)
  
  airport <- str_to_upper(airport)
  
  xml_site <- try(read_xml(paste0("https://w1.weather.gov/xml/current_obs/", airport, ".xml")))
  
  if ("try-error" %in% class(xml_site)) {
    warning("Airport Site not found")
    return(tibble())
  }
  
  kids <- xml_children(xml_site)
  
  kid_names <- purrr::map_chr(kids, xml_name)
  kid_values <- purrr::map_chr(kids, xml_text)
  
  as_tibble(t(kid_values)) %>%
    set_names(kid_names) %>%
    select(-matches("credit|image|suggested|icon|url"), 
           -observation_time, 
           -matches("string"), 
           -matches("_c|_mb|_kt")) %>%
    mutate_at(.vars = vars(-matches("observation_time|weather|wind_dir|location|station")), as.numeric) %>%
    mutate(observation_time = lubridate::parse_date_time(observation_time_rfc822, 
                                                         orders = "dmyHMSz", 
                                                         tz = "America/Chicago")) %>%
    select(-observation_time_rfc822)
}
```





What did you investigate? Describe how to format at least 3 separate pieces of a document using HTML tags:

1. 

2. 

3. 





---

Next, we'll see what HTML generated from Rmarkdown looks like. 

Compile this Rmarkdown document to HTML, then open the HTML file in a web browser. Open the inspector console for your browser (Ctrl-Shift-I in Chrome, Ctrl-Shift-C in Firefox) and look at the HTML code corresponding to various parts of the document. 

---
Answer the following questions:

- What types of tags did you find? 

- How are code chunks formatted in HTML?

- What differences are there in the HTML markup for R code chunks and R output blocks?

---

Remember, just because you have the HTML file doesn't mean you should commit it to your git repository!!! Delete the HTML file now if you're going to be tempted to accidentally commit and push it.

## Navigation: HTML, CSS, XPATH, and more.

In many situations, it is helpful to be able to pick out specific parts of an HTML or XML file - for example, a table with useful data. CSS (Cascading Style Sheets) Selectors and XPATH are two methods commonly used to identify specific nodes in HTML or XML documents. 

- [XPATH Syntax](https://www.w3schools.com/xml/xpath_syntax.asp)
- [CSS Selector Syntax](https://www.w3schools.com/cssref/css_selectors.asp)

In R, the `rvest` package, which is part of the tidyverse, makes it (relatively) easy to pull specific pieces from structured documents. The `html_nodes` function selects nodes using either xpath or css, and additional functions such as `html_attrs`, `html_text`, and `html_table` pull information out of the markup text.

Choose a Wikipedia page that has at least one image to test the `rvest` package out - we'll cover this in class as well. 


```r
library(rvest)

wiki_url <- "https://en.wikipedia.org/wiki/Pembroke_Welsh_Corgi"

wiki_html <- read_html(wiki_url)
```

When using CSS Selectors, some people find [SelectorGadget](https://selectorgadget.com/) to be a helpful tool. You can get CSS or XPATH selectors from your browser inspector as well:

<a href="http://i.imgur.com/UbwrdIN.png">
  <img width="50%" alt="browser inspector selector helper" src="http://imgur.com/UbwrdINl.png" />
</a>

---

Using your wikipedia page of choice, obtain the following using `rvest`:

- a character vector containing the URL of each image on the page

- the url of all links in the page


```r
wiki_html %>% html_nodes(xpath = "//img") %>% html_attr("src")
wiki_html %>% html_nodes(xpath = "//a") %>% html_attr("href")
```


```r
wiki_html %>% html_nodes("img") %>% html_attr("src")
wiki_html %>% html_nodes("a") %>% html_attr("href")
```

---

We will discuss more complicated CSS selectors and XPATH in lecture, but it is helpful to try them out using simple tag elements. 

## Dynamic Web Pages - Javascript, AJAX, PHP, ASP, and more!

Not all web pages are the same. Static web pages have content that is pre-specified, and when the page is loaded all of the content is just... there. These pages are the easiest to scrape, because the HTML file already contains all of the information needed to render the page. Dynamic web pages have a basic HTML layout, and then scripting languages are used to inject content into the pages at some point after the initial page loads. Using `xml2::read_html()` on these pages will get you a different HTML file than the one you see when loading the page in your browser. 

If you are interested in learning more about how to scrape dynamic web pages, take a look at the `Rselenium` or `splashR` packages. These packages emulate a browser (or launch one for you to control using R), allowing the scripting languages to inject page content before providing you with the updated HTML file containing the information you actually wanted in the first place.

Note: Not all websites which use javascript (or other scripting languages) are difficult to scrape (at this point, practically every web page uses javascript somewhere), but when javascript is used to inject data from a database after the page initially loads, it's likely that you'll have to do a bit more work to get at the data. 


## Instructions:

Update your forked version of the 'blog-2019' repository (or re-fork it after deleting your previous repo).

Save a **copy** of this file, replacing "Lastname" and "Firstname" with your own and *leave the original unedited*. (Note: Lastname = your family name, Firstname = your given name)

In **your copy**, replace the `title:` and `author:` fields in the YAML above, while leaving the remaining fields intact. Remove the background and the instructions sections and write your blog post! 

Once you are done, **create a pull request** to upload your changes to the original repository. Do not commit the compiled HTML file to the repository.
