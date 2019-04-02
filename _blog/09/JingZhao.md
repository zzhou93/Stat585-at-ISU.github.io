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

    library(xml2)
    library(tidyverse)
    ##letter were needed to be put in quation e.g., "KAMW"
    current_weather <- function (letter) {
      #input check
      if(length(letter) > 1) stop("put quation and rerun again")
      
      d <- read_xml(paste0("https://w1.weather.gov/xml/current_obs/", letter, ".xml"))
     
      name <- c("location","station_id","latitude","longitude","observation_time","weather","wind_mph","wind_dir")
      data <- data.frame()
      extract_data <- vector()
      for (i in 1: length(name)) {
        extract_data [i] <- d %>% xml_find_all(name[i]) %>% xml_text()
        # data <- data.frame(name[i])
      } 
      df <-rbind(data,extract_data)
      colnames(df) <- name
      
      checkmate::checkDataFrame(df)
      
      return(df)
      }
    ## test function using data from "https://w1.weather.gov/xml/current_obs/KAMW.xml"
    current_weather("KAMW")

    ##                           location station_id latitude longitude
    ## 1 Ames, Ames Municipal Airport, IA       KAMW 41.99056 -93.61889
    ##                           observation_time       weather wind_mph
    ## 1 Last Updated on Apr 2 2019, 10:53 am CDT Mostly Cloudy     10.4
    ##    wind_dir
    ## 1 Northwest

1.  Which HTML tags did you investigate? Describe how to format at least
    3 separate pieces of a document using HTML tags. I investigate the
    following HTML tags: The *&lt;body&gt;* element contains the visible
    page content The *&lt;h1&gt;* element defines a large heading The
    *&lt;p&gt;* element defines a paragraph\\

If 3 separate piece of a document need to be combined into three
separate paragrah, then we should use thre pairs of *&lt;p&gt;* and
*&lt;/p&gt;* for each paragraph.\\

1.  Compile this Rmarkdown document to HTML, then open the HTML file in
    a web browser. Open the inspector console for your browser
    (Ctrl-Shift-I in Chrome, Ctrl-Shift-C in Firefox) and look at the
    HTML code corresponding to various parts of the document. Answer the
    following questions:

    -   What types of tags did you find?

    *&lt;html&gt;* *&lt;head&gt;* *&lt;body&gt;* *&lt;div&gt;*
    *&lt;h1&gt;* *&lt;code&gt;* *&lt;pre&gt;*

    -   How are code chunks formatted in HTML?

    <pre class="r">
    -   What differences are there in the HTML markup for R code chunks
        and R output blocks?

    <pre>
2.  In R, the `rvest` package, which is part of the tidyverse, makes it
    (relatively) easy to pull specific pieces from structured documents.
    The `html_nodes` function selects nodes using either xpath or css,
    and additional functions such as `html_attrs`, `html_text`, and
    `html_table` pull information out of the markup text.<br> Choose a
    Wikipedia page that has at least one image to test the `rvest`
    package out

<!-- -->

    library(rvest)
    ## This is an example to get the ratting score of the movie from "http://www.imdb.com/title/tt1490017/"
    lego_movie <- read_html("http://www.imdb.com/title/tt1490017/")
    lego_movie %>%
      html_node("strong span") %>%
      html_text() %>%
      as.numeric()

    ## [1] 7.8

Remember, just because you have the HTML file doesn’t mean you should
commit it to your git repository!!! Delete the HTML file now if you’re
going to be tempted to accidentally commit and push it.

------------------------------------------------------------------------
