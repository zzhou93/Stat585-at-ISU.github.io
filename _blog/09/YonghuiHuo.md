### Background

The internet may not be [a series of
tubes](https://en.wikipedia.org/wiki/Series_of_tubes), but it is made up
of a number of different programming and markup languages. It is useful
to develop a basic vocabulary and understanding of these languages
before attempting to interact with (messy) data stored on the internet.

<a href="https://www.xkcd.com/1144/"><img src="https://imgs.xkcd.com/comics/tags.png" alt="XKCD comic: HTML Tags" /></a>
&lt;A&gt;: Like &lt;/a&gt;this.&nbsp;"

As the reading material for this week, you are asked to read through a
set of websites on XML and HTML and navigating through them:

-   **XML (eXtensible Markup Language):** XML is a generic markup
    framework. Many different common file types are based on or related
    to XML structure (for instance, .docx, .xlsx, .html) <bR> Read the
    following sections of w3schools.com’s Introduction to XML:

    -   [XML Introduction](https://www.w3schools.com/xml/xml_whatis.asp)
    -   [XML How to Use](https://www.w3schools.com/xml/xml_usedfor.asp)
    -   [XML Tree](https://www.w3schools.com/xml/xml_tree.asp)
    -   [XML Syntax](https://www.w3schools.com/xml/xml_syntax.asp)
    -   [XML Elements](https://www.w3schools.com/xml/xml_elements.asp)
    -   [XML
        Attributes](https://www.w3schools.com/xml/xml_attributes.asp)

-   **HTML (HyperText Markup Language):** HTML focuses on the display of
    information in a document format. XML is a much more general
    framework, but most of the concepts (tags, attributes, elements)
    apply directly to HTML. Open up the [w3schools HTML
    page](https://www.w3schools.com/html/default.asp) and read the
    introduction, then look through a few topics in the tutorial that
    interest you.

-   **Navigation: HTML, CSS, XPATH, and more:** In many situations, it
    is helpful to be able to pick out specific parts of an HTML or XML
    file - for example, a table with useful data. CSS (Cascading Style
    Sheets) Selectors and XPATH are two methods commonly used to
    identify specific nodes in HTML or XML documents.

    -   [XPATH Syntax](https://www.w3schools.com/xml/xpath_syntax.asp)
    -   [CSS Selector
        Syntax](https://www.w3schools.com/cssref/css_selectors.asp)

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
    library(testthat)

    current_weather =function(name){
      link = paste0("https://w1.weather.gov/xml/current_obs/", name, ".xml")
      
      assertthat::assert_that(is.character(link), msg = "link should be a string!")
      file = read_xml(link)
      colname = xml_name(xml_children(file))
      len = length(colname)
      text = xml_text(xml_children(file))
      data = as.data.frame(matrix(text, nrow=1, ncol=len, byrow = T), stringsAsFactors = F)
      
      if(!is.data.frame(data)|is.null(dim(data))){warning("please check data again.")}
      
      colnames(data)=colname
      df = data %>% dplyr::select(station_id, latitude, longitude, observation_time, 
                          weather, temperature_string, wind_dir, wind_mph)
      
      expect_s3_class(df, "data.frame")
      return(df)
    }
    current_weather("KAMW")

    ##   station_id latitude longitude                         observation_time
    ## 1       KAMW 41.99056 -93.61889 Last Updated on Apr 2 2019, 10:53 am CDT
    ##         weather temperature_string  wind_dir wind_mph
    ## 1 Mostly Cloudy     39.0 F (3.9 C) Northwest     10.4

1.  Which HTML tags did you investigate? Describe how to format at least
    3 separate pieces of a document using HTML tags.

### I find heading, paragraph, and image.

&lt;!DOCTYPE html&gt;
<html>
<body>
<h1>
Hello
</h1>
<p>
I hope Ames will become warmer in the following days.
</p>
<p style="background-color:Tomato;">
Let’s have a BBQ tomorrow!
</p>
</body>
</html>
1.  Compile this Rmarkdown document to HTML, then open the HTML file in
    a web browser. Open the inspector console for your browser
    (Ctrl-Shift-I in Chrome, Ctrl-Shift-C in Firefox) and look at the
    HTML code corresponding to various parts of the document. <br>
    Answer the following questions:

-   What types of tags did you find? I found head, body and so on.
-   How are code chunks formatted in HTML? code chunks are formatted in
    a container of style “R” with a &lt;pre: class = “r”&gt; tag.
-   What differences are there in the HTML markup for R code chunks and
    R output blocks? code chunks have class = “r” in the “pre” tags(have
    colors), while R output blocks do not have.

1.  In R, the `rvest` package, which is part of the tidyverse, makes it
    (relatively) easy to pull specific pieces from structured documents.
    The `html_nodes` function selects nodes using either xpath or css,
    and additional functions such as `html_attrs`, `html_text`, and
    `html_table` pull information out of the markup text.<br> Choose a
    Wikipedia page that has at least one image to test the `rvest`
    package out

<!-- -->

    library(rvest)
    library(magrittr)
    library(magick)

    link="https://en.wikipedia.org/wiki/Sailor_Moon"
    link2=read_html(link)
    node = html_nodes(link2, "table.infobox")

    text=html_text(node)

    table2=html_table(node, header=F) 
    table2 %>% pander::pander()

-   <table>
    <tbody>
    <tr class="odd">
    <td style="text-align: center;">X1 X2</td>
    </tr>
    </tbody>
    </table>

                Sailor Moon                        Sailor Moon

           First tankōbon volume,             First tankōbon volume,
        released in Japanon July 6,        released in Japanon July 6,
        1992 featuring Usagi Tsukino       1992 featuring Usagi Tsukino
              as Sailor Moon.                    as Sailor Moon.

    美少女戦士セーラームーン(Bishōjo 美少女戦士セーラームーン(Bishōjo
    Senshi Sērāmūn) Senshi Sērāmūn)

                   Genre                           Magical girl

                   Manga                              Manga

                 Written by                       Naoko Takeuchi

                Published by                         Kodansha

             English publisher            AUS Penguin Books AustraliaNA
                                           Kodansha ComicsUK Turnaround
                                                Publisher Services

                Demographic                           Shōjo

                  Magazine                      Nakayoshi, Run Run

              English magazine                  NA Mixxzine, Smile

                Original run               December 28, 1991 – February
                                                     3, 1997

                  Volumes                      18 (List of volumes)

          Anime television series            Anime television series

          Sailor Moon Sailor Moon            Sailor Moon Sailor Moon
                  Crystal                            Crystal

                Other media                        Other media

    Codename: Sailor V (1991-1997) Codename: Sailor V (1991-1997) Pretty
    Guardian Sailor Moon Pretty Guardian Sailor Moon (live-action)
    Films: Sailor (live-action) Films: Sailor Moon R: The Movie (1993)
    Moon R: The Movie (1993) Sailor Moon S: The Movie Sailor Moon S: The
    Movie
    1.  Sailor Moon SuperS: The (1994) Sailor Moon SuperS: The
        Movie (1995) Collectible Card Movie (1995) Collectible Card Game
        Musicals Soundtracks Game Musicals Soundtracks Video games Video
        games

    <!-- -->

           Anime and Manga portal             Anime and Manga portal

    ------------------------------------------------------------------------

<!-- end of list -->
    b=link2 %>% html_node("img") %>% html_attr("src")
    url=paste0("http:",b) 
    d=url%>% image_read() %>% image_trim()
    d

<img src="../figure/09/YonghuiHuo/unnamed-chunk-2-1.png" width="220" />

------------------------------------------------------------------------
