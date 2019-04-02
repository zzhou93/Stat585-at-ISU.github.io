\#1.

    library(xml2)
    library(tidyverse)
    current_weather <- function(code) {
      assertthat::see_if(is.character(code), msg = "Input must be a character")
      url <- paste0("https://w1.weather.gov/xml/current_obs/", code, ".xml")
      xml <- read_xml(url)
      nodeset <- xml %>% xml_children 
      name <- nodeset %>% xml_name
      content <- nodeset %>% xml_text
      dat <- as.data.frame(matrix(content, ncol = length(content), byrow = T), stringsAsFactors = F)
      colnames(dat) <- name
      res <- dat %>% dplyr::select(station_id, latitude, longitude, observation_time, 
                          weather, temperature_string, wind_dir, wind_mph)
      checkmate::checkDataFrame(res)
      return(res)
    }
    current_weather("KAMW")

    ##   station_id latitude longitude                         observation_time
    ## 1       KAMW 41.99056 -93.61889 Last Updated on Apr 2 2019, 10:53 am CDT
    ##         weather temperature_string  wind_dir wind_mph
    ## 1 Mostly Cloudy     39.0 F (3.9 C) Northwest     10.4

\#2.

I looked at HTML colors. Colors can be specified by names, RGB values,
HEX values, HSL values, RGBA values, and HSLA values. And not only the
background, the text can have color, the border can also have color!
Plus, we can make the color somewhat transpant, just like R.

-lists:

<html>
<body>
<h2>
Where will you do during the spring break?
</h2>
<ul style="list-style-type:circle;">
<li>
Stay at home, do nothing.
</li>
<li>
Stay at home, finish your CC!!!
</li>
<li>
Out of tiwn for fun.
</li>
</ul>
</body>
</html>
-color:

<h1 style="border: 2px solid Tomato;">
It’s Spring Break ;) How about watching a movie???
</h1>
-links:

<a href="https://en.wikipedia.org/wiki/Audrey_Hepburn" target="_blank">Audrey’s
website</a>

\#3.

-   What types of tags did you find? Background color and color, font
    size and line height.

-   How are code chunks formatted in HTML?

<pre class="r">
-   What differences are there in the HTML markup for R code chunks and
    R output blocks?

In HTML the output starts like this:

<pre>
<code class="hljs">

Other are quite the same, except that the output of Attaching packages,
in R, it generates different colors, but in HTML, it is just black.

\#4.

    library(rvest)
    library(magrittr)
    url <- "https://en.wikipedia.org/wiki/Audrey_Hepburn"

    table <- url %>% 
      read_html() %>% 
      html_nodes("table.vcard") %>%
      html_table(header=F) 
    table %>% pander::pander()

-   <table style="width:71%;">
    <colgroup>
    <col style="width: 25%" />
    <col style="width: 45%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th style="text-align: center;">X1</th>
    <th style="text-align: center;">X2</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td style="text-align: center;">Audrey Hepburn</td>
    <td style="text-align: center;">Audrey Hepburn</td>
    </tr>
    <tr class="even">
    <td style="text-align: center;">Hepburn in 1956</td>
    <td style="text-align: center;">Hepburn in 1956</td>
    </tr>
    <tr class="odd">
    <td style="text-align: center;">Born</td>
    <td style="text-align: center;">Audrey Kathleen Ruston(1929-05-04)4 May 1929Ixelles, Brussels, Belgium</td>
    </tr>
    <tr class="even">
    <td style="text-align: center;">Died</td>
    <td style="text-align: center;">20 January 1993(1993-01-20) (aged 63)Tolochenaz, Vaud, Switzerland</td>
    </tr>
    <tr class="odd">
    <td style="text-align: center;">Resting place</td>
    <td style="text-align: center;">Tolochenaz Cemetery, Tolochenaz, Vaud</td>
    </tr>
    <tr class="even">
    <td style="text-align: center;">Nationality</td>
    <td style="text-align: center;">British</td>
    </tr>
    <tr class="odd">
    <td style="text-align: center;">Occupation</td>
    <td style="text-align: center;">Actress (1948–1989)Humanitarian (1988–1992)</td>
    </tr>
    <tr class="even">
    <td style="text-align: center;">Spouse(s)</td>
    <td style="text-align: center;">Mel Ferrer(m. 1954; div. 1968)Andrea Dotti(m. 1969; div. 1982)</td>
    </tr>
    <tr class="odd">
    <td style="text-align: center;">Partner(s)</td>
    <td style="text-align: center;">Robert Wolders(1980–1993; her death)</td>
    </tr>
    <tr class="even">
    <td style="text-align: center;">Children</td>
    <td style="text-align: center;">2</td>
    </tr>
    <tr class="odd">
    <td style="text-align: center;">Parent(s)</td>
    <td style="text-align: center;">Baroness Ella van HeemstraJoseph Victor Anthony Ruston</td>
    </tr>
    <tr class="even">
    <td style="text-align: center;">Relatives</td>
    <td style="text-align: center;">Baron Aarnoud van Heemstra(maternal grandfather)Emma Ferrer(granddaughter)</td>
    </tr>
    <tr class="odd">
    <td style="text-align: center;">Signature</td>
    <td style="text-align: center;">Signature</td>
    </tr>
    </tbody>
    </table>

<!-- end of list -->
    url %>% read_html() %>% 
      html_node("img") %>% 
      html_attr("src") %>%
      paste0("https:",.) %>%
      magick::image_read()

<img src="../figure/09/ZhangYudi/unnamed-chunk-2-1.png" width="220" />
