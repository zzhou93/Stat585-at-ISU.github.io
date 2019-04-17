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
      # check input, whether code is avilable
      checkmate::assertCharacter(code)
       ## check code is charachter and 4 charachters
      if(!is.character(code)){
        stop('the code is not character')
      }
      
      if(nchar(code) != 4){
        stop("The code must have 4 characters!")
      }
      weatherData <- read_xml(paste0("https://w1.weather.gov/xml/current_obs/",code,".xml")) %>%
        xml_children() %>%
        xml_text() %>%
        .[c(7,8,9,11,14,18,20)] %>%
        t() %>%
        data.frame() %>%
        setNames(c("stationID","lat","long","lastUpdate","temp(F)","windDirection","windSpeed(MPH)"))
      
      #check output is dataframe
      checkmate::assertDataFrame(weatherData,types = c("numeric", "factor"), min.rows = 1, col.names = "named")
      weatherData
    }
    current_weather("KAMW")

    ##   stationID      lat      long                      lastUpdate temp(F)
    ## 1      KAMW 41.99056 -93.61889 Tue, 02 Apr 2019 10:53:00 -0500    39.0
    ##   windDirection windSpeed(MPH)
    ## 1     Northwest           10.4

1.  Which HTML tags did you investigate? Describe how to format at least
    3 separate pieces of a document using HTML tags.

-   css Style: use to format the document, here set blue color to
    background color and blue color to header text and red to paragraph
    text
=======
---
title: "A Series of Tubes..."
author: "Zahra Khoshmanesh"
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
  # check input, whether code is avilable
  checkmate::assertCharacter(code)
   ## check code is charachter and 4 charachters
  if(!is.character(code)){
    stop('the code is not character')
  }
  
  if(nchar(code) != 4){
    stop("The code must have 4 characters!")
  }
  weatherData <- read_xml(paste0("https://w1.weather.gov/xml/current_obs/",code,".xml")) %>%
    xml_children() %>%
    xml_text() %>%
    .[c(7,8,9,11,14,18,20)] %>%
    t() %>%
    data.frame() %>%
    setNames(c("stationID","lat","long","lastUpdate","temp(F)","windDirection","windSpeed(MPH)"))
  
  #check output is dataframe
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


2. Which HTML tags did you investigate? Describe how to format at least 3 separate pieces of a document using HTML tags.

* css Style: use to format the document, here set blue color to background color and blue color to header text and red to paragraph text
>>>>>>> blog 9 posts up

<style>
body {background-color: powderblue;}
h1   {color: blue;}
p    {color: red;}
</style>
<<<<<<< HEAD
-   header and paragraph: <h> tag is for setting a header. h1 is larger
    size and h5 is smaller size.

<h1>
This is a heading
</h1>
<p>
This is a paragraph.
</p>
-   CSS Border p { border: 1px solid powderblue; }

-   Hyperlinks <a href="url">link text</a>
    <a href="https://github.com/">GitHub</a>

-   image
    <img src="https://bloximages.newyork1.vip.townnews.com/stltoday.com/content/tncms/assets/v3/editorial/5/ca/5ca00daf-81a6-5e26-bff3-25ea003d8f4e/4f9054fbddfae.image.jpg" alt="Cute Chimpanzee">

-   table
    <table style="width:100%">
    <tr>
    <th>
    Firstname
    </th>
    <th>
    Lastname
    </th>
    <th>
    Age
    </th>
    </tr>
    <tr>
    <td>
    tom
    </td>
    <td>
    Smith
    </td>
    <td>
    20
    </td>
    </tr>
    <tr>
    <td>
    sara
    </td>
    <td>
    Jackson
    </td>
    <td>
    48
    </td>
    </tr>
    </table>

1.  Compile this Rmarkdown document to HTML, then open the HTML file in
    a web browser. Open the inspector console for your browser
    (Ctrl-Shift-I in Chrome, Ctrl-Shift-C in Firefox) and look at the
    HTML code corresponding to various parts of the document. <br>
    Answer the following questions:
    -   What types of tags did you find?

        -   head, body, style, script, div,color ,font

        -   line, height and width , margin , padding

    -   How are code chunks formatted in HTML?
        -   R code chunks are with pre class=“r” tags. The actual text
            is stored within a span class=“hljs” tag.
    -   What differences are there in the HTML markup for R code chunks
        and R output blocks?
        -   Code output blocks are stored in a pre tag and the text in
            another code class=“hljs” tag.

2.  In R, the `rvest` package, which is part of the tidyverse, makes it
    (relatively) easy to pull specific pieces from structured documents.
    The `html_nodes` function selects nodes using either xpath or css,
    and additional functions such as `html_attrs`, `html_text`, and
    `html_table` pull information out of the markup text.<br> Choose a
    Wikipedia page that has at least one image to test the `rvest`
    package out

<!-- -->

    library(rvest)
    spring <- read_html("https://en.wikipedia.org/wiki/Spring_(season)")
    html_node(spring,"img") %>% 
      xml_attr(attr="src") %>%
      paste0("https:",.) %>%
      magick::image_read()

<img src="../figure/09/KhoshmaneshZahra/unnamed-chunk-2-1.png" width="260" />

    html_nodes(spring,"table")[1] %>%
      html_attr("class")

    ## [1] "vertical-navbox nowraplinks hlist"

    html_nodes(spring,"table")[1] %>%
    html_table()

    ## [[1]]
    ##                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      X1
    ## 1                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             Part of the nature series
    ## 2                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               Weather
    ## 3                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      Calendar seasons\nWinter\nSpring\nSummer\nAutumn
    ## 4                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   Tropical seasons\nDry season\nHarmattan\nWet season
    ## 5 Storms\nCloud\nCumulonimbus cloud\nArcus cloud\nDownburst\nMicroburst\nHeat burst\nDerecho\nLightning\nThunderstorm\nAir-mass thunderstorm\nThundersnow\nMesocyclone\nSupercell\nTornado\nAnticyclonic tornado\nLandspout\nWaterspout\nDust devil\nFire whirl\nAnticyclone\nCyclone\nPolar low\nExtratropical cyclone\nEuropean windstorm\nNor'easter\nSubtropical cyclone\nTropical cyclone\nAtlantic hurricane\nTyphoon\nStorm surge\nDust storm\nSimoom\nHaboob\nMonsoon\nGale\nSirocco\nFirestorm\nWinter storm\nIce storm\nBlizzard\nGround blizzard\nSnowsquall
    ## 6                                                                                                                                                                                                                                                                                                                                                                     Precipitation\nDrizzle (Freezing drizzle)\nGraupel\nHail\nMegacryometeor\nIce pellets\nDiamond dust\nRain (Freezing rain)\nCloudburst\nSnow\nRain and snow mixed\nSnow grains\nSnow roller\nSlush
    ## 7                                                                                                                                                                                                                                                                                                                               Topics\nAir pollution\nAtmosphereChemistry\nConvection\nPhysics\nRiver\nClimate\nCloud\nPhysics\nFog\nFog season\nCold wave\nHeat wave\nJet stream\nMeteorology\nSevere weather\nList\nExtremeWeather forecasting\nWeather modification
    ## 8                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        Glossaries\nMeteorology\nClimate change\nTornado terms\nTropical cyclone terms
    ## 9                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        Weather portal
=======

* header and paragraph: <h> tag is for setting a header. h1 is larger size and h5 is smaller size.

<h1>This is a heading</h1>
<p>This is a paragraph.</p>

* CSS Border
p {
  border: 1px solid powderblue;
}

* Hyperlinks
<a href="url">link text</a>
<a href="https://github.com/">GitHub</a>

* image
<img src="https://bloximages.newyork1.vip.townnews.com/stltoday.com/content/tncms/assets/v3/editorial/5/ca/5ca00daf-81a6-5e26-bff3-25ea003d8f4e/4f9054fbddfae.image.jpg" alt="Cute Chimpanzee">

* table
<table style="width:100%">
  <tr>
    <th>Firstname</th>
    <th>Lastname</th> 
    <th>Age</th>
  </tr>
  <tr>
    <td> tom</td>
    <td>Smith</td> 
    <td>20</td>
  </tr>
  <tr>
    <td>sara</td>
    <td>Jackson</td> 
    <td>48</td>
  </tr>
</table>



3. Compile this Rmarkdown document to HTML, then open the HTML file in a web browser. Open the inspector console for your browser (Ctrl-Shift-I in Chrome, Ctrl-Shift-C in Firefox) and look at the HTML code corresponding to various parts of the document. <br>
Answer the following questions:
    - What types of tags did you find?
    
      * head, body, style, script, div,color ,font
      
      * line, height and width , margin , padding
    
    - How are code chunks formatted in HTML?
       *  R code chunks are with pre class="r" tags. The actual text is stored within a span class="hljs" tag.
    - What differences are there in the HTML markup for R code chunks and R output blocks?
       * Code output blocks are stored in a pre tag and the text in another code class="hljs" tag.
    
4. In R, the `rvest` package, which is part of the tidyverse, makes it (relatively) easy to pull specific pieces from structured documents. The `html_nodes` function selects nodes using either xpath or css, and additional functions such as `html_attrs`, `html_text`, and `html_table` pull information out of the markup text.<br>
Choose a Wikipedia page that has at least one image to test the `rvest` package out


```r
library(rvest)
spring <- read_html("https://en.wikipedia.org/wiki/Spring_(season)")
html_node(spring,"img") %>% 
  xml_attr(attr="src") %>%
  paste0("https:",.) %>%
  magick::image_read()
```

![center](./../figure/09/KhoshmaneshZahra/unnamed-chunk-2-1.png)

```r
html_nodes(spring,"table")[1] %>%
  html_attr("class")
```

```
## [1] "vertical-navbox nowraplinks hlist"
```

```r
html_nodes(spring,"table")[1] %>%
html_table()
```

```
## [[1]]
##                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      X1
## 1                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             Part of the nature series
## 2                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               Weather
## 3                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      Calendar seasons\nWinter\nSpring\nSummer\nAutumn
## 4                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   Tropical seasons\nDry season\nHarmattan\nWet season
## 5 Storms\nCloud\nCumulonimbus cloud\nArcus cloud\nDownburst\nMicroburst\nHeat burst\nDerecho\nLightning\nThunderstorm\nAir-mass thunderstorm\nThundersnow\nMesocyclone\nSupercell\nTornado\nAnticyclonic tornado\nLandspout\nWaterspout\nDust devil\nFire whirl\nAnticyclone\nCyclone\nPolar low\nExtratropical cyclone\nEuropean windstorm\nNor'easter\nSubtropical cyclone\nTropical cyclone\nAtlantic hurricane\nTyphoon\nStorm surge\nDust storm\nSimoom\nHaboob\nMonsoon\nGale\nSirocco\nFirestorm\nWinter storm\nIce storm\nBlizzard\nGround blizzard\nSnowsquall
## 6                                                                                                                                                                                                                                                                                                                                                                     Precipitation\nDrizzle (Freezing drizzle)\nGraupel\nHail\nMegacryometeor\nIce pellets\nDiamond dust\nRain (Freezing rain)\nCloudburst\nSnow\nRain and snow mixed\nSnow grains\nSnow roller\nSlush
## 7                                                                                                                                                                                                                                                                                                                               Topics\nAir pollution\nAtmosphereChemistry\nConvection\nPhysics\nRiver\nClimate\nCloud\nPhysics\nFog\nFog season\nCold wave\nHeat wave\nJet stream\nMeteorology\nSevere weather\nList\nExtremeWeather forecasting\nWeather modification
## 8                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        Glossaries\nMeteorology\nClimate change\nTornado terms\nTropical cyclone terms
## 9                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        Weather portal
```
>>>>>>> blog 9 posts up
