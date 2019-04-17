<<<<<<< HEAD
1.  The xml2 R package can be used to work with xml files. Write a
    function, current\_weather that accepts a 4-letter airport code
    (KAMW in the URL here:
    <a href="https://w1.weather.gov/xml/current_obs/KAMW.xml" class="uri">https://w1.weather.gov/xml/current_obs/KAMW.xml</a>)
    and returns a data frame with the airport location (station ID,
    latitude, longitude), last update time, and current weather
    information (temperature, weather condition, wind speed and
    direction) at that airport. The xml2 functions read\_xml,
    xml\_children, xml\_name, and xml\_text will be useful. Remember to
    handle errors and check inputs, and make sure to return a data frame
    with appropriate data types.

<!-- -->

    current_weather <- function(code) {
    #' This function takes in 4-letter airport code and returns information on
    #' airport location, current weather and last update time.
    #'
    #' @author  stat_cat
    #' @param   code 4-letter string
    #' @return  info data frame with information on airport and current weather
    #' @export  current_weather
        # check if code is string
        checkmate::assert_character(code)
        
        # declare path
        path <- paste("https://w1.weather.gov/xml/current_obs/", 
                      code, ".xml", sep = "")
        # extract xml from path
        xml <- read_xml(path)
        
        # from examining xml children, we extract only specific attributes
        # extract character typed variable
        text_ch <- xml_text(xml_children(xml))[c(7,10,12,13,18)]
        # extract double typed variable
        text_dbl <- xml_double(xml_children(xml))[c(8,9,20)]
        # combine into one
        info <- data.frame(attribute = c(text_ch, text_dbl), 
                           row.names = c("station ID",
                                         "last update time",
                                         "weather condition",
                                         "temperature",
                                         "wind direction",
                                         "lattitude",
                                         "longitude",
                                         "wind speed"))
        # check if info is data frame
        checkmate::checkDataFrame(info)
        
        return(info)
    }

Here I used to my function to extract weather information for
international aiport in San Jose, California:

    current_weather("KSJC")

    ##                                                 attribute
    ## station ID                                           KSJC
    ## last update time  Last Updated on Apr 2 2019, 8:53 am PDT
    ## weather condition                                Overcast
    ## temperature                               56.0 F (13.3 C)
    ## wind direction                                  Southeast
    ## lattitude                                        37.35917
    ## longitude                                      -121.92417
    ## wind speed                                            8.1

<br><br> 2. Which HTML tags did you investigate? Describe how to format
at least 3 separate pieces of a document using HTML tags.

I want to share tags by the following examples: (note that since we
defined thhe output of .rmd to be html, this file accepts html tags
directly, i.e we don’t have to include document type declaration, html
and body tags) <br>
<h1>
It’s a HUGE heading!
</h1>
<a href = "https://kgulzina.github.io/">link to my website</a> <br>
<p style="font-family:courier;">
Here is the picture of my favorite cat:
</p>
<img src = "https://static01.nyt.com/images/2016/07/08/arts/08PETS/08PETS-superJumbo-v2.jpg?quality=90&auto=webp">

<br><br> 3. Compile this Rmarkdown document to HTML, then open the HTML
file in a web browser. Open the inspector console for your browser
(Ctrl-Shift-I in Chrome, Ctrl-Shift-C in Firefox) and look at the HTML
code corresponding to various parts of the document. Answer the
following questions:

-   What types of tags did you find?
    <p style="font-family:courier;">
    Tags which I noticed, or at least could differentiate were: head,
    body and html document tags. Also, there are a lot of script and
    style tags.
    </p>
-   How are code chunks formatted in HTML?
    <p style="font-family:courier;">
    Code chunks are formatted by &lt;code&gt; tag with class = “hljs”
    attribute, which are within parent &lt;pre&gt; tag with class = “r”
    as an attribute.
    </p>
-   What differences are there in the HTML markup for R code chunks and
    R output blocks?
    <p style="font-family:courier;">
    While both are contained within parent tag &lt;pre&gt; with class =
    “r”, code chunks are within &lt;code&gt; tag and output blocks are
    simply in &lt;pre&gt; tag without any specific attribute.
    </p>

<br><br> 4. In R, the rvest package, which is part of the tidyverse,
makes it (relatively) easy to pull specific pieces from structured
documents. The html\_nodes function selects nodes using either xpath or
css, and additional functions such as html\_attrs, html\_text, and
html\_table pull information out of the markup text. Choose a Wikipedia
page that has at least one image to test the rvest package out.

    url <- "https://en.wikipedia.org/wiki/Michael_Ballack"
    html <- read_html(url)

    # extract the bigoraphical data
    html %>% html_nodes(".vcard") %>% html_text(trim = TRUE) -> ballack
    ballack[1] %>% strsplit("\n")

    ## [[1]]
    ##  [1] "Michael Ballack"                                                         
    ##  [2] "Ballack in 2014Personal informationFull name"                            
    ##  [3] "Michael Ballack[1]Date of birth"                                         
    ##  [4] " (1976-09-26) 26 September 1976 (age 42)Place of birth"                  
    ##  [5] "Görlitz, East GermanyHeight"                                             
    ##  [6] "1.88 m (6 ft 2 in)[2]Playing position"                                   
    ##  [7] "MidfielderYouth career1983–1995"                                         
    ##  [8] "Chemnitzer FCSenior career*Years"                                        
    ##  [9] "Team"                                                                    
    ## [10] "Apps"                                                                    
    ## [11] "(Gls)1995–1997"                                                          
    ## [12] "Chemnitzer FC II"                                                        
    ## [13] "18"                                                                      
    ## [14] "(5)1995–1997"                                                            
    ## [15] "Chemnitzer FC"                                                           
    ## [16] "49"                                                                      
    ## [17] "(10)1997–1998"                                                           
    ## [18] "1. FC Kaiserslautern II"                                                 
    ## [19] "17"                                                                      
    ## [20] "(8)1997–1999"                                                            
    ## [21] "1. FC Kaiserslautern"                                                    
    ## [22] "46"                                                                      
    ## [23] "(4)1999–2002"                                                            
    ## [24] "Bayer Leverkusen"                                                        
    ## [25] "79"                                                                      
    ## [26] "(27)2002–2006"                                                           
    ## [27] "Bayern Munich"                                                           
    ## [28] "107"                                                                     
    ## [29] "(44)2006–2010"                                                           
    ## [30] "Chelsea"                                                                 
    ## [31] "105"                                                                     
    ## [32] "(17)2010–2012"                                                           
    ## [33] "Bayer Leverkusen"                                                        
    ## [34] "35"                                                                      
    ## [35] "(2)Total"                                                                
    ## [36] ""                                                                        
    ## [37] "456"                                                                     
    ## [38] "(117)National team1996–1998"                                             
    ## [39] "Germany U21"                                                             
    ## [40] "19"                                                                      
    ## [41] "(7)1999–2010"                                                            
    ## [42] "Germany"                                                                 
    ## [43] "98"                                                                      
    ## [44] "(42)"                                                                    
    ## [45] "    Honours"                                                             
    ## [46] "    "                                                                    
    ## [47] ""                                                                        
    ## [48] "FIFA World Cup"                                                          
    ## [49] ""                                                                        
    ## [50] "2002 South Korea–Japan"                                                  
    ## [51] ""                                                                        
    ## [52] ""                                                                        
    ## [53] "2006 Germany"                                                            
    ## [54] ""                                                                        
    ## [55] "UEFA European Championship"                                              
    ## [56] ""                                                                        
    ## [57] "2008 Austria–Switzerland"                                                
    ## [58] ""                                                                        
    ## [59] "FIFA Confederations Cup"                                                 
    ## [60] ""                                                                        
    ## [61] "2005 Germany"                                                            
    ## [62] ""                                                                        
    ## [63] ""                                                                        
    ## [64] "* Senior club appearances and goals counted for the domestic league only"

    ## I could clean up more, but for this moment it's seems to take a lot of time
=======
---
title: "A Serises of Tubes..."
author: "Gulzina Kuttubekova"
topic: '09'
layout: post
root: ../../../
output: 
  html_document: 
    #css: extra.css
---

1. The xml2 R package can be used to work with xml files. Write a function, current_weather that accepts a 4-letter airport code (KAMW in the URL here: https://w1.weather.gov/xml/current_obs/KAMW.xml) and returns a data frame with the airport location (station ID, latitude, longitude), last update time, and current weather information (temperature, weather condition, wind speed and direction) at that airport. The xml2 functions read_xml, xml_children, xml_name, and xml_text will be useful. Remember to handle errors and check inputs, and make sure to return a data frame with appropriate data types.



```r
current_weather <- function(code) {
#' This function takes in 4-letter airport code and returns information on
#' airport location, current weather and last update time.
#'
#' @author  stat_cat
#' @param   code 4-letter string
#' @return  info data frame with information on airport and current weather
#' @export  current_weather
    # check if code is string
    checkmate::assert_character(code)
    
    # declare path
    path <- paste("https://w1.weather.gov/xml/current_obs/", 
                  code, ".xml", sep = "")
    # extract xml from path
    xml <- read_xml(path)
    
    # from examining xml children, we extract only specific attributes
    # extract character typed variable
    text_ch <- xml_text(xml_children(xml))[c(7,10,12,13,18)]
    # extract double typed variable
    text_dbl <- xml_double(xml_children(xml))[c(8,9,20)]
    # combine into one
    info <- data.frame(attribute = c(text_ch, text_dbl), 
                       row.names = c("station ID",
                                     "last update time",
                                     "weather condition",
                                     "temperature",
                                     "wind direction",
                                     "lattitude",
                                     "longitude",
                                     "wind speed"))
    # check if info is data frame
    checkmate::checkDataFrame(info)
    
    return(info)
}
```

Here I used to my function to extract weather information for international aiport in San Jose, California:

```r
current_weather("KSJC")
```

```
##                                                  attribute
## station ID                                            KSJC
## last update time  Last Updated on Apr 3 2019, 10:53 am PDT
## weather condition                                 Overcast
## temperature                                59.0 F (15.0 C)
## wind direction                                    Variable
## lattitude                                         37.35917
## longitude                                       -121.92417
## wind speed                                             3.5
```
<br><br>
2. Which HTML tags did you investigate? Describe how to format at least 3 separate pieces of a document using HTML tags.

 I want to share tags by the following examples: (note that since we defined thhe output of .rmd to be html, this file accepts html tags directly, i.e we don't have to include document type declaration, html and body tags)
<br>
<h1>It's a HUGE heading!</h1>
<a href = "https://kgulzina.github.io/">link to my website</a>
<br>
<p style="font-family:courier;">Here is the picture of my favorite cat:</p>
<img src = "https://static01.nyt.com/images/2016/07/08/arts/08PETS/08PETS-superJumbo-v2.jpg?quality=90&auto=webp">

<br><br>
3. Compile this Rmarkdown document to HTML, then open the HTML file in a web browser. Open the inspector console for your browser (Ctrl-Shift-I in Chrome, Ctrl-Shift-C in Firefox) and look at the HTML code corresponding to various parts of the document. 
Answer the following questions:

- What types of tags did you find?
 <p style="font-family:courier;">Tags which I noticed, or at least could differentiate were: head, body and html document tags. Also, there are a lot of script and style tags.</p>
- How are code chunks formatted in HTML?
 <p style="font-family:courier;">Code chunks are formatted by &lt;code&gt; tag with class = "hljs" attribute, which are within parent &lt;pre&gt; tag with class = "r" as an attribute.</p>
- What differences are there in the HTML markup for R code chunks and R output blocks?
 <p style="font-family:courier;">While both are contained within parent tag &lt;pre&gt; with class = "r", code chunks are within &lt;code&gt; tag and output blocks are simply in &lt;pre&gt; tag without any specific attribute.</p>

<br><br>
4. In R, the rvest package, which is part of the tidyverse, makes it (relatively) easy to pull specific pieces from structured documents. The html_nodes function selects nodes using either xpath or css, and additional functions such as html_attrs, html_text, and html_table pull information out of the markup text.
Choose a Wikipedia page that has at least one image to test the rvest package out.



```r
url <- "https://en.wikipedia.org/wiki/Michael_Ballack"
html <- read_html(url)

# extract the bigoraphical data
html %>% html_nodes(".vcard") %>% html_text(trim = TRUE) -> ballack
ballack[1] %>% strsplit("\n")
```

```
## [[1]]
##  [1] "Michael Ballack"                                                         
##  [2] "Ballack in 2014Personal informationFull name"                            
##  [3] "Michael Ballack[1]Date of birth"                                         
##  [4] " (1976-09-26) 26 September 1976 (age 42)Place of birth"                  
##  [5] "Görlitz, East GermanyHeight"                                             
##  [6] "1.88 m (6 ft 2 in)[2]Playing position"                                   
##  [7] "MidfielderYouth career1983–1995"                                         
##  [8] "Chemnitzer FCSenior career*Years"                                        
##  [9] "Team"                                                                    
## [10] "Apps"                                                                    
## [11] "(Gls)1995–1997"                                                          
## [12] "Chemnitzer FC II"                                                        
## [13] "18"                                                                      
## [14] "(5)1995–1997"                                                            
## [15] "Chemnitzer FC"                                                           
## [16] "49"                                                                      
## [17] "(10)1997–1998"                                                           
## [18] "1. FC Kaiserslautern II"                                                 
## [19] "17"                                                                      
## [20] "(8)1997–1999"                                                            
## [21] "1. FC Kaiserslautern"                                                    
## [22] "46"                                                                      
## [23] "(4)1999–2002"                                                            
## [24] "Bayer Leverkusen"                                                        
## [25] "79"                                                                      
## [26] "(27)2002–2006"                                                           
## [27] "Bayern Munich"                                                           
## [28] "107"                                                                     
## [29] "(44)2006–2010"                                                           
## [30] "Chelsea"                                                                 
## [31] "105"                                                                     
## [32] "(17)2010–2012"                                                           
## [33] "Bayer Leverkusen"                                                        
## [34] "35"                                                                      
## [35] "(2)Total"                                                                
## [36] ""                                                                        
## [37] "456"                                                                     
## [38] "(117)National team1996–1998"                                             
## [39] "Germany U21"                                                             
## [40] "19"                                                                      
## [41] "(7)1999–2010"                                                            
## [42] "Germany"                                                                 
## [43] "98"                                                                      
## [44] "(42)"                                                                    
## [45] "    Honours"                                                             
## [46] "    "                                                                    
## [47] ""                                                                        
## [48] "FIFA World Cup"                                                          
## [49] ""                                                                        
## [50] "2002 South Korea–Japan"                                                  
## [51] ""                                                                        
## [52] ""                                                                        
## [53] "2006 Germany"                                                            
## [54] ""                                                                        
## [55] "UEFA European Championship"                                              
## [56] ""                                                                        
## [57] "2008 Austria–Switzerland"                                                
## [58] ""                                                                        
## [59] "FIFA Confederations Cup"                                                 
## [60] ""                                                                        
## [61] "2005 Germany"                                                            
## [62] ""                                                                        
## [63] ""                                                                        
## [64] "* Senior club appearances and goals counted for the domestic league only"
```

```r
## I could clean up more, but for this moment it's seems to take a lot of time
```









>>>>>>> blog 9 posts up
