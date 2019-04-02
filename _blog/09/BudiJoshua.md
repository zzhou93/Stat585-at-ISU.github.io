the function

    library(xml2)
    library(tidyverse)
    current_weather <- function(url){
      xmlhead <-xml2::read_xml(url)
      long = NULL 
      for (i in 7:20){
        xmlname <- xml_children(xmlhead)[i] %>% xml_name 
        xmltext <- xml_children(xmlhead)[i] %>% xml_text
        weather.df <- data.frame(xmlname, xmltext)
        long=rbind(long,weather.df)
      }
      long
      }

the dataframe result

    amesweather <- "https://w1.weather.gov/xml/current_obs/KAMW.xml"
    current_weather(amesweather)

    ##                    xmlname                                  xmltext
    ## 1               station_id                                     KAMW
    ## 2                 latitude                                 41.99056
    ## 3                longitude                                -93.61889
    ## 4         observation_time Last Updated on Apr 2 2019, 10:53 am CDT
    ## 5  observation_time_rfc822          Tue, 02 Apr 2019 10:53:00 -0500
    ## 6                  weather                            Mostly Cloudy
    ## 7       temperature_string                           39.0 F (3.9 C)
    ## 8                   temp_f                                     39.0
    ## 9                   temp_c                                      3.9
    ## 10       relative_humidity                                       76
    ## 11             wind_string             Northwest at 10.4 MPH (9 KT)
    ## 12                wind_dir                                Northwest
    ## 13            wind_degrees                                      300
    ## 14                wind_mph                                     10.4

1.  test out the html tags headings use h1, h2, h3, and so on, css=h1
    span  
    images use img, css= a img  
    table use css=div table

use `read_html` to read the url, then use `html_nodes` to collect out
the components then use `html_text` to parse out just the text of
interest

1.  

<!-- -->

1.  `<code> </code>, <pre> </pre>, <div> </div>`
2.  together for one chunk to appear as customized, based on how it is
    desired to look like
3.  xml code chunks are more free and customizable based on coffee. html
    code chunks more geared towards public showing, not specific
    templates ’

<!-- -->

1.  rvest

<!-- -->

    library(tidyverse)
    library(rvest)

    breadfruit <- read_html("https://en.wikipedia.org/wiki/Breadfruit") 
    h2<- breadfruit %>% html_nodes("h2 span") %>%  html_text
    h2

    ##  [1] "History"        "[edit]"         "["              "]"             
    ##  [5] "Description"    "[edit]"         "["              "]"             
    ##  [9] "Habitat"        "[edit]"         "["              "]"             
    ## [13] "Nutrition"      "[edit]"         "["              "]"             
    ## [17] "Uses"           "[edit]"         "["              "]"             
    ## [21] "In culture"     "[edit]"         "["              "]"             
    ## [25] "Propagation"    "[edit]"         "["              "]"             
    ## [29] "Gallery"        "[edit]"         "["              "]"             
    ## [33] "See also"       "[edit]"         "["              "]"             
    ## [37] "References"     "[edit]"         "["              "]"             
    ## [41] "External links" "[edit]"         "["              "]"

    h2a<- h2 %>% subset(h2!="[edit]")
    h2b<- h2a %>% subset(h2a!="[")
    h2c<- h2b %>% subset(h2b!="]")

    h2c

    ##  [1] "History"        "Description"    "Habitat"        "Nutrition"     
    ##  [5] "Uses"           "In culture"     "Propagation"    "Gallery"       
    ##  [9] "See also"       "References"     "External links"

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
types. 2. Which HTML tags did you investigate? Describe how to format at
least 3 separate pieces of a document using HTML tags. 3. Compile this
Rmarkdown document to HTML, then open the HTML file in a web browser.
Open the inspector console for your browser (Ctrl-Shift-I in Chrome,
Ctrl-Shift-C in Firefox) and look at the HTML code corresponding to
various parts of the document. <br> Answer the following questions: -
What types of tags did you find? - How are code chunks formatted in
HTML? - What differences are there in the HTML markup for R code chunks
and R output blocks? 4. In R, the `rvest` package, which is part of the
tidyverse, makes it (relatively) easy to pull specific pieces from
structured documents. The `html_nodes` function selects nodes using
either xpath or css, and additional functions such as `html_attrs`,
`html_text`, and `html_table` pull information out of the markup
text.<br> Choose a Wikipedia page that has at least one image to test
the `rvest` package out Remember, just because you have the HTML file
doesn’t mean you should commit it to your git repository!!! Delete the
HTML file now if you’re going to be tempted to accidentally commit and
push it.
