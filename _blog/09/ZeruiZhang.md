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

    library(tidyverse)
    library(xml2)
    library(assertthat)
    current_weather <- function(code){
      ids <- read_xml("https://w1.weather.gov/xml/current_obs/index.xml")
      all_codes <- xml_find_all(ids, ".//station_id") %>% xml_text()
      assert_that(is.character(code), nchar(code)==4, msg="Code is not a 4-letter character")
      if(!(code %in% all_codes)){
        stop("Code is invalid.")
      }
      xml <- paste0("https://w1.weather.gov/xml/current_obs/", code, ".xml") %>% read_xml()
      node <- xml %>% xml_children()
      names <- node %>% xml_name()
      texts <- node %>% xml_text()
      index <- which(names %in% c("station_id", 
                                      "latitude", 
                                      "longitude", 
                                      "observation_time",
                                      "weather", 
                                      "temperature_string", 
                                      "wind_dir", 
                                      "wind_mph"))
      df <- cbind(names[index], texts[index]) %>% as.data.frame()
      colnames(df) <- c("category", "information")
      checkmate::checkDataFrame(df)
      df
    }
    current_weather("KAMW")

    ##             category                              information
    ## 1         station_id                                     KAMW
    ## 2           latitude                                 41.99056
    ## 3          longitude                                -93.61889
    ## 4   observation_time Last Updated on Apr 2 2019, 10:53 am CDT
    ## 5            weather                            Mostly Cloudy
    ## 6 temperature_string                           39.0 F (3.9 C)
    ## 7           wind_dir                                Northwest
    ## 8           wind_mph                                     10.4

1.  Which HTML tags did you investigate? Describe how to format at least
    3 separate pieces of a document using HTML tags.

Color:

<!--html_preserve-->
<h1 style="background-color:rgb(131, 116, 196); color:rgb(238, 130, 238);">
Once upon a time, a princess named Hello World…
</h1>
<!--/html_preserve-->
Link:

<!--html_preserve-->
<style>
a:link, a:visited {
  background-color: #f44336;
  color: white;
  padding: 15px 25px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
}

a:hover, a:active {
  background-color: orange;
}
</style>
<a href="https://en.wikipedia.org/wiki/Harry_Potter" target="_blank">Harry
Potter’s wiki</a> <!--/html_preserve-->

List:

<!--html_preserve-->
<html>
<body>
<p>
Choose something to eat
</p>
<ul style="list-style-type:circle;">
<li>
Thai curry
</li>
<ul>
<li>
Chicken
</li>
<li>
Seafood
</li>
</ul>
<li>
Sweet and Sour Tofu
</li>
<li>
Broccoli
</li>
</ul>
</body>
</html>
<!--/html_preserve-->
1.  Compile this Rmarkdown document to HTML, then open the HTML file in
    a web browser. Open the inspector console for your browser
    (Ctrl-Shift-I in Chrome, Ctrl-Shift-C in Firefox) and look at the
    HTML code corresponding to various parts of the document. <br>
    Answer the following questions:
    -   What types of tags did you find?

    Tags for color, line, block, e.g.,*head*, *body*, *style*, *div*,
    *p*, *ol*, *pre*, etc.

    -   How are code chunks formatted in HTML?

    The code is embedded in the tag *pre class=“r”*.

    -   What differences are there in the HTML markup for R code chunks
        and R output blocks?

    The code chunks have the tag *pre class=“r”*, while the output
    blocks have the tag *pre*.

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

    library(rvest)

    web <- read_html("https://en.wikipedia.org/wiki/Harry_Potter")
    table <- web %>% 
      html_table(fill=T, header = T) %>%
      .[[1]]
    table %>% pander::pander()

<table style="width:92%;">
<colgroup>
<col style="width: 45%" />
<col style="width: 45%" />
</colgroup>
<thead>
<tr class="header">
<th style="text-align: center;"> </th>
<th style="text-align: center;"> </th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: center;">The Philosopher’s Stone (1997) The Chamber of Secrets (1998) The Prisoner of Azkaban (1999) The Goblet of Fire (2000) The Order of the Phoenix (2003) The Half-Blood Prince (2005) The Deathly Hallows (2007)</td>
<td style="text-align: center;">The Philosopher’s Stone (1997) The Chamber of Secrets (1998) The Prisoner of Azkaban (1999) The Goblet of Fire (2000) The Order of the Phoenix (2003) The Half-Blood Prince (2005) The Deathly Hallows (2007)</td>
</tr>
<tr class="even">
<td style="text-align: center;">Author</td>
<td style="text-align: center;">J. K. Rowling</td>
</tr>
<tr class="odd">
<td style="text-align: center;">Country</td>
<td style="text-align: center;">United Kingdom</td>
</tr>
<tr class="even">
<td style="text-align: center;">Language</td>
<td style="text-align: center;">English</td>
</tr>
<tr class="odd">
<td style="text-align: center;">Genre</td>
<td style="text-align: center;">Fantasy, drama, young adult fiction, mystery, thriller, Bildungsroman</td>
</tr>
<tr class="even">
<td style="text-align: center;">Publisher</td>
<td style="text-align: center;">Bloomsbury Publishing (UK)Pottermore (e-books; all languages)</td>
</tr>
<tr class="odd">
<td style="text-align: center;">Published</td>
<td style="text-align: center;">26 June 1997 – 21 July 2007 (initial publication)</td>
</tr>
<tr class="even">
<td style="text-align: center;">Media type</td>
<td style="text-align: center;">Print (hardback &amp; paperback)AudiobookE-book (as of March 2012[update])[1]</td>
</tr>
<tr class="odd">
<td style="text-align: center;">No. of books</td>
<td style="text-align: center;">7</td>
</tr>
<tr class="even">
<td style="text-align: center;">Website</td>
<td style="text-align: center;">www.pottermore.com</td>
</tr>
</tbody>
</table>

    img <- web %>% 
      html_nodes("#mw-content-text > div > div:nth-child(168) > div > a > img") %>% 
      html_attr("srcset") %>% 
      strsplit(" ") %>% 
      .[[1]] %>%
      .[3] %>% 
      paste0("https:",.) %>% 
      magick::image_read()
    img

<img src="../figure/09/ZeruiZhang/unnamed-chunk-2-1.png" width="440" />
