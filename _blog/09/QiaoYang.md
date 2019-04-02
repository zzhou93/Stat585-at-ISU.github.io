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

    library(dplyr)
    library(xml2)

    fun <- function(ICAO_code) {
      checkmate::assert_string(ICAO_code, pattern = "^[A-Z]{4}$")
      xml <- paste0("https://w1.weather.gov/xml/current_obs/", ICAO_code, ".xml") %>% read_xml()
      data <- xml_children(xml) %>% {setNames(xml_text(.), xml_name(.))} %>%
        t() %>% data.frame() %>%
        select(station_id, latitude, longitude, observation_time_rfc822, weather, temp_c, wind_dir, wind_mph) %>%
        rename(observation_time = observation_time_rfc822)
      checkmate::assert_data_frame(data, nrows = 1)
      data
    }

    fun("KAMW")

    ##   station_id latitude longitude                observation_time
    ## 1       KAMW 41.99056 -93.61889 Tue, 02 Apr 2019 10:53:00 -0500
    ##         weather temp_c  wind_dir wind_mph
    ## 1 Mostly Cloudy    3.9 Northwest     10.4

1.  Which HTML tags did you investigate? Describe how to format at least
    3 separate pieces of a document using HTML tags.

    <strong>Link</strong>  
    <a href="https://stat585-at-isu.github.io/">STAT 585 Homepage</a>

    <strong>List</strong>
    <ol type="a">
    <li>
    Coffee
    </li>
    <li>
    Tea
    <ul style="list-style-type:square;">
    <li>
    Red Tea
    </li>
    <li>
    Green Tea
    </li>
    </ul>
    </li>
    <li>
    Milk
    </li>
    </ol>
    <strong>JavaScript</strong>  
    <button type="button" onclick="document.getElementById('demo').innerHTML = Date()">
    Click me!</button>
    <p id="demo" style="color:DodgerBlue;">
    Hello world!
    </p>
2.  Compile this Rmarkdown document to HTML, then open the HTML file in
    a web browser. Open the inspector console for your browser
    (Ctrl-Shift-I in Chrome, Ctrl-Shift-C in Firefox) and look at the
    HTML code corresponding to various parts of the document. <br>
    Answer the following questions:

    -   What types of tags did you find?

        &lt;pre&gt;, &lt;code&gt;, &lt;strong&gt;, etc.

    -   How are code chunks formatted in HTML?

        Wrapped by &lt;pre&gt; and &lt;code&gt;.

    -   What differences are there in the HTML markup for R code chunks
        and R output blocks?

        R code chunks use &lt;pre class=“r”&gt;, while R output blocks
        use &lt;pre&gt;.

3.  In R, the `rvest` package, which is part of the tidyverse, makes it
    (relatively) easy to pull specific pieces from structured documents.
    The `html_nodes` function selects nodes using either xpath or css,
    and additional functions such as `html_attrs`, `html_text`, and
    `html_table` pull information out of the markup text.<br> Choose a
    Wikipedia page that has at least one image to test the `rvest`
    package out

<!-- -->

    library(rvest)

    html <- "https://en.wikipedia.org/wiki/Mandelbrot_set" %>% read_html()
    img_url <- html %>%
      html_nodes(".thumbimage") %>% html_attr(name = "srcset") %>%
      stringr::str_subset("(?=.*Mandelbrot_sequence_new)(?=.*\\.gif)") %>%
      paste0("https:", .) %>% stringr::word()
    magick::image_read(img_url)

![](../figure/09/QiaoYang/unnamed-chunk-2-1.gif)
