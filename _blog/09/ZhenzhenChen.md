**Write a blog post answering the following questions and detailing the
progress: **

1.  

<!-- -->

    library(tidyverse)
    library(xml2)

    current_weather <- function(airport){
      
      checkmate::assertCharacter(airport)
      ## read the data and select corresponding elements
      airport <- read_xml(paste0("https://w1.weather.gov/xml/current_obs/", airport, ".xml" ))
      dataname <- airport %>% xml_children() %>% xml_name() %>% .[c(7, 8, 9, 10, 14, 15, 20, 18)]
      seldata <- airport %>% xml_children() %>% xml_text %>% .[c(7, 8, 9, 10, 14, 15, 20, 18)]
      
      ## construct a data.frame
      dat <- as.data.frame(matrix(seldata, ncol = length(seldata)), stringsAsFactors = F)
      colnames(dat) <- dataname
      
      checkmate::check_data_frame(data) # check whether the output is a data.frame
      return(dat)
    }

    current_weather("KAMW")

    ##   station_id latitude longitude                         observation_time
    ## 1       KAMW 41.99056 -93.61889 Last Updated on Apr 2 2019, 10:53 am CDT
    ##   temp_f temp_c wind_mph  wind_dir
    ## 1   39.0    3.9     10.4 Northwest

    current_weather("KCNC") 

    ##   station_id latitude longitude                         observation_time
    ## 1       KCNC 41.03333 -93.36667 Last Updated on Apr 2 2019, 10:55 am CDT
    ##   temp_f temp_c wind_mph  wind_dir
    ## 1   37.0    3.0     11.5 Northwest

1.  Which HTML tags did you investigate? Describe how to format at least
    3 separate pieces of a document using HTML tags.

The three HTML tags I investigate are

-image: &lt;img src =
“<a href="https://www.uniquevenues.com/sites/uniquevenues.com/files/imagecache/2015_venue_flexslider/venues/slideshow/Central_Campus.jpg" class="uri">https://www.uniquevenues.com/sites/uniquevenues.com/files/imagecache/2015_venue_flexslider/venues/slideshow/Central_Campus.jpg</a>”
width = “500”, height = “600”&gt;

-   title
    <p title="Here is my paper">
    Long long a ago, there is a little girl.
    </p>
-   document
    <html>
    <body>

<h1>
Statistical Inference
</h1>
<h2>
Probability distribution
</h2>
<p>
The first objective is to develop the first principles of statistical
inference.
</p>
</body>
</html>
1.  Compile this Rmarkdown document to HTML, then open the HTML file in
    a web browser. Open the inspector console for your browser
    (Ctrl-Shift-I in Chrome, Ctrl-Shift-C in Firefox) and look at the
    HTML code corresponding to various parts of the document. <br>
    Answer the following questions:
    -   What types of tags did you find? Background color, color ,
        font-size
    -   How are code chunks formatted in HTML?
        <pre class="r">
    -   What differences are there in the HTML markup for R code chunks
        and R output blocks? The R code chunks has class “r” under the
        “code” tag. The R output blocks has class “hljs” tags.
2.  

<!-- -->

    library(rvest)
    ggp <- read_html("https://en.wikipedia.org/wiki/Ggplot2")

    read_ima <- ggp %>% html_nodes("img") %>%
       html_attr("src") %>%
       paste0("https:",.) 

    ima <- knitr::include_graphics(read_ima[[1]])
