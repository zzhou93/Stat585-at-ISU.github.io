<<<<<<< HEAD
**Write a blog post answering the following questions and detailing the
progress: **

1.  

<!-- -->

    # Write a function, current_weather that accepts a 4-letter airport code and returns a data frame with station ID, latitude, longitude, last update time, and current weather information, temperature, weather condition, wind speed and direction.
     
    # return a data frame with appropriate data types. 
    library(xml2)
    library(tidyverse)

    current_weather <- function(code){
      checkmate::assertCharacter(code)
      
      airport <- read_xml(paste0("https://w1.weather.gov/xml/current_obs/",code,".xml"))
      
      #airport <- read_xml('https://w1.weather.gov/xml/current_obs/KORD.xml')
      #airport %>% xml_children()%>%xml_name()%>%View()
      
      info <-airport %>% xml_children()%>%xml_name()%>%.[c(7,8,9,10,12,14,15,18,20)]
      data <-airport %>% xml_children()%>%xml_text()%>%.[c(7,8,9,10,12,14,15,18,20)]
      
      # 1 obs of 9 vaiables 
      df <- data.frame( as.list(data), stringsAsFactors=FALSE)
      names(df)<-info
      # chane types of latitude,longitude, temp_f, temp_c ,wind_mph to be numeric, others be chr   #str(df)
      df[, c(2,3,6,7,9)] <- sapply(df[, c(2,3,6,7,9)], as.numeric)
      #str(df)
      df
    }

    # call functions:
    current_weather("KAMW")

    ##   station_id latitude longitude                         observation_time
    ## 1       KAMW 41.99056 -93.61889 Last Updated on Apr 2 2019, 10:53 am CDT
    ##         weather temp_f temp_c  wind_dir wind_mph
    ## 1 Mostly Cloudy     39    3.9 Northwest     10.4

    current_weather("KORD")

    ##   station_id latitude longitude                         observation_time
    ## 1       KORD 41.97972 -87.90444 Last Updated on Apr 2 2019, 10:51 am CDT
    ##         weather temp_f temp_c  wind_dir wind_mph
    ## 1 Mostly Cloudy     50     10 Southwest     13.8

1.  Which HTML tags did you investigate? Describe how to format at least
    3 separate pieces of a document using HTML tags.

I checked `<div>`, `<iframe>`, `<img>`, `<table>` ect..

Format 3 separate pieces:

> I use `<iframe>` to embed my site to this page:

<iframe height="300" src="https://zhengying1127.github.io/" width="100%" height="50%">
</iframe>
> I use `<table>` to make a table:

<table>
<tr>
<th>
sepal\_length
</th>
<th>
sepal\_width
</th>
<th>
petal\_length
</th>
<th>
petal\_width
</th>
<th>
species
</th>
</tr>
<tr>
<td>
5.1
</td>
<td>
3.5
</td>
<td>
1.4
</td>
<td>
0.2
</td>
<td>
setosa
</td>
</tr>
<tr>
<td>
4.9
</td>
<td>
3.0
</td>
<td>
1.4
</td>
<td>
0.2
</td>
<td>
setosa
</td>
</tr>
</table>
> I use `<img>` to insert an image to this page:

<img src="https://www.google.com/images/branding/googlelogo/2x/googlelogo_color_272x92dp.png" alt="google" width="30%" height="30%">

1.  Compile this Rmarkdown document to HTML, then open the HTML file in
    a web browser. Open the inspector console for your browser
    (Ctrl-Shift-I in Chrome, Ctrl-Shift-C in Firefox) and look at the
    HTML code corresponding to various parts of the document. <br>
    Answer the following questions:

    -   What types of tags did you find?

        I found `div`, `p`, `ol`, `pre`, `code`, `iframe`, `table`,
        `img` ect..

    -   How are code chunks formatted in HTML?

        `<pre class="r"><code class="hljs"> code </code></pre>`

    -   What differences are there in the HTML markup for R code chunks
        and R output blocks?

        The R output is formated as:

        `<pre><code class="hljs"> output </code></pre>`

        The difference is for R code chunks, the `pre` element has an
        attribute `class` and value is `"r"`.

2.  In R, the `rvest` package, which is part of the tidyverse, makes it
    (relatively) easy to pull specific pieces from structured documents.
    The `html_nodes` function selects nodes using either xpath or css,
    and additional functions such as `html_attrs`, `html_text`, and
    `html_table` pull information out of the markup text. Choose a
    Wikipedia page that has at least one image to test the `rvest`
    package out

<!-- -->

    library(rvest)
    url<-"https://en.wikipedia.org/wiki/Normal_distribution"
    normal <- read_html(url)

    html_node(normal,"img")%>% 
      xml_attr("src") %>%
      paste0("https:",.) %>%
      magick::image_read()

<img src="../figure/09/ZhengYing/unnamed-chunk-2-1.png" width="340" />

    html_node(normal,"table")%>% 
       html_table()

    ##                                                                               X1
    ## 1  Probability density functionThe red curve is the standard normal distribution
    ## 2                                               Cumulative distribution function
    ## 3                                                                       Notation
    ## 4                                                                     Parameters
    ## 5                                                                        Support
    ## 6                                                                            PDF
    ## 7                                                                            CDF
    ## 8                                                                       Quantile
    ## 9                                                                           Mean
    ## 10                                                                        Median
    ## 11                                                                          Mode
    ## 12                                                                      Variance
    ## 13                                                                      Skewness
    ## 14                                                                  Ex. kurtosis
    ## 15                                                                       Entropy
    ## 16                                                                           MGF
    ## 17                                                                            CF
    ## 18                                                            Fisher information
    ##                                                                                                                                                                                                                                                                                                X2
    ## 1                                                                                                                                                                                                                   Probability density functionThe red curve is the standard normal distribution
    ## 2                                                                                                                                                                                                                                                                Cumulative distribution function
    ## 3                                                                                                                                                                                                                                     N(μ,σ2){\\displaystyle {\\mathcal {N}}(\\mu ,\\sigma ^{2})}
    ## 4                                                                                                                                                                     μ∈R{\\displaystyle \\mu \\in \\mathbb {R} } = mean (location)σ2>0{\\displaystyle \\sigma ^{2}>0} = variance (squared scale)
    ## 5                                                                                                                                                                                                                                                         x∈R{\\displaystyle x\\in \\mathbb {R} }
    ## 6                                                                                                                                                                          12πσ2e−(x−μ)22σ2{\\displaystyle {\\frac {1}{\\sqrt {2\\pi \\sigma ^{2}}}}e^{-{\\frac {(x-\\mu )^{2}}{2\\sigma ^{2}}}}}
    ## 7                                                                                                                                                   12[1+erf⁡(x−μσ2)]{\\displaystyle {\\frac {1}{2}}\\left[1+\\operatorname {erf} \\left({\\frac {x-\\mu }{\\sigma {\\sqrt {2}}}}\\right)\\right]}
    ## 8                                                                                                                                                                                                      μ+σ2erf−1⁡(2F−1){\\displaystyle \\mu +\\sigma {\\sqrt {2}}\\operatorname {erf} ^{-1}(2F-1)}
    ## 9                                                                                                                                                                                                                                                                         μ{\\displaystyle \\mu }
    ## 10                                                                                                                                                                                                                                                                        μ{\\displaystyle \\mu }
    ## 11                                                                                                                                                                                                                                                                        μ{\\displaystyle \\mu }
    ## 12                                                                                                                                                                                                                                                                σ2{\\displaystyle \\sigma ^{2}}
    ## 13                                                                                                                                                                                                                                                                            0{\\displaystyle 0}
    ## 14                                                                                                                                                                                                                                                                            0{\\displaystyle 0}
    ## 15                                                                                                                                                                                                                         12log⁡(2πeσ2){\\displaystyle {\\frac {1}{2}}\\log(2\\pi e\\sigma ^{2})}
    ## 16                                                                                                                                                                                                                               exp⁡(μt+σ2t2/2){\\displaystyle \\exp(\\mu t+\\sigma ^{2}t^{2}/2)}
    ## 17                                                                                                                                                                                                                             exp⁡(iμt−σ2t2/2){\\displaystyle \\exp(i\\mu t-\\sigma ^{2}t^{2}/2)}
    ## 18 I(μ,σ)=(1/σ2002/σ2){\\displaystyle {\\mathcal {I}}(\\mu ,\\sigma )={\\begin{pmatrix}1/\\sigma ^{2}&0\\\\0&2/\\sigma ^{2}\\end{pmatrix}}} \nI(μ,σ2)=(1/σ2001/(2σ4)){\\displaystyle {\\mathcal {I}}(\\mu ,\\sigma ^{2})={\\begin{pmatrix}1/\\sigma ^{2}&0\\\\0&1/(2\\sigma ^{4})\\end{pmatrix}}}
=======
---
title: "A Series of Tubes..."
author: "Ying Zheng"
topic: "09"
layout: post
root: ../../../
output: 
  html_document: 
    css: extra.css
---


**Write a blog post answering the following questions and detailing the progress: **

1. 



```r
# Write a function, current_weather that accepts a 4-letter airport code and returns a data frame with station ID, latitude, longitude, last update time, and current weather information, temperature, weather condition, wind speed and direction.
 
# return a data frame with appropriate data types. 
library(xml2)
library(tidyverse)

current_weather <- function(code){
  checkmate::assertCharacter(code)
  
  airport <- read_xml(paste0("https://w1.weather.gov/xml/current_obs/",code,".xml"))
  
  #airport <- read_xml('https://w1.weather.gov/xml/current_obs/KORD.xml')
  #airport %>% xml_children()%>%xml_name()%>%View()
  
  info <-airport %>% xml_children()%>%xml_name()%>%.[c(7,8,9,10,12,14,15,18,20)]
  data <-airport %>% xml_children()%>%xml_text()%>%.[c(7,8,9,10,12,14,15,18,20)]
  
  # 1 obs of 9 vaiables 
  df <- data.frame( as.list(data), stringsAsFactors=FALSE)
  names(df)<-info
  # chane types of latitude,longitude, temp_f, temp_c ,wind_mph to be numeric, others be chr   #str(df)
  df[, c(2,3,6,7,9)] <- sapply(df[, c(2,3,6,7,9)], as.numeric)
  #str(df)
  df
}

# call functions:
current_weather("KAMW")
```

```
##   station_id latitude longitude                         observation_time
## 1       KAMW 41.99056 -93.61889 Last Updated on Apr 3 2019, 12:53 pm CDT
##    weather temp_f temp_c wind_dir wind_mph
## 1 Overcast     54   12.2    South      9.2
```

```r
current_weather("KORD")
```

```
##   station_id latitude longitude                         observation_time
## 1       KORD 41.97972 -87.90444 Last Updated on Apr 3 2019, 12:51 pm CDT
##         weather temp_f temp_c  wind_dir wind_mph
## 1 Mostly Cloudy     54   12.2 Southwest     10.4
```


2. Which HTML tags did you investigate? Describe how to format at least 3 separate pieces of a document using HTML tags.

I checked  `<div>`, `<iframe>`, `<img>`, `<table>` ect..

Format 3 separate pieces:

> I use `<iframe>` to embed my site to this page: 


<iframe height="300" src="https://zhengying1127.github.io/" width="100%" height="50%"></iframe> 


> I use `<table>` to make a table:


<table>
  <tr>
    <th>sepal_length</th>
    <th>sepal_width</th>
    <th>petal_length</th>
    <th>petal_width</th>
    <th>species</th>
  </tr>
  <tr>
    <td>5.1</td>
    <td>3.5</td>
    <td>1.4</td>
    <td>0.2</td>
    <td>setosa</td>
  </tr>
  <tr>
    <td>4.9</td>
    <td>3.0</td>
    <td>1.4</td>
    <td>0.2</td>
    <td>setosa</td>
  </tr>
</table>




> I use `<img>` to insert an image to this page:


<img src="https://www.google.com/images/branding/googlelogo/2x/googlelogo_color_272x92dp.png" alt="google" width="30%" height="30%">

 

3. Compile this Rmarkdown document to HTML, then open the HTML file in a web browser. Open the inspector console for your browser (Ctrl-Shift-I in Chrome, Ctrl-Shift-C in Firefox) and look at the HTML code corresponding to various parts of the document. <br>
Answer the following questions:

    - What types of tags did you find?
      
      I found `div`, `p`, `ol`, `pre`, `code`, `iframe`, `table`, `img` ect..

    - How are code chunks formatted in HTML?

      `<pre class="r"><code class="hljs"> code </code></pre>`

    - What differences are there in the HTML markup for R code chunks and R output blocks?
      
      The  R output is formated as:
      
      `<pre><code class="hljs"> output </code></pre>`
      
      The difference is for R code chunks, the `pre` element has an attribute `class` and        value is `"r"`.
      
    
    
    
4. In R, the `rvest` package, which is part of the tidyverse, makes it (relatively) easy to pull specific pieces from structured documents. The `html_nodes` function selects nodes using either xpath or css, and additional functions such as `html_attrs`, `html_text`, and `html_table` pull information out of the markup text. 
Choose a Wikipedia page that has at least one image to test the `rvest` package out



```r
library(rvest)
url<-"https://en.wikipedia.org/wiki/Normal_distribution"
normal <- read_html(url)

html_node(normal,"img")%>% 
  xml_attr("src") %>%
  paste0("https:",.) %>%
  magick::image_read()
```

![center](./../figure/09/ZhengYing/unnamed-chunk-2-1.png)

```r
html_node(normal,"table")%>% 
   html_table()
```

```
##                                                                               X1
## 1  Probability density functionThe red curve is the standard normal distribution
## 2                                               Cumulative distribution function
## 3                                                                       Notation
## 4                                                                     Parameters
## 5                                                                        Support
## 6                                                                            PDF
## 7                                                                            CDF
## 8                                                                       Quantile
## 9                                                                           Mean
## 10                                                                        Median
## 11                                                                          Mode
## 12                                                                      Variance
## 13                                                                      Skewness
## 14                                                                  Ex. kurtosis
## 15                                                                       Entropy
## 16                                                                           MGF
## 17                                                                            CF
## 18                                                            Fisher information
##                                                                                                                                                                                                                                                                                                X2
## 1                                                                                                                                                                                                                   Probability density functionThe red curve is the standard normal distribution
## 2                                                                                                                                                                                                                                                                Cumulative distribution function
## 3                                                                                                                                                                                                                                     N(μ,σ2){\\displaystyle {\\mathcal {N}}(\\mu ,\\sigma ^{2})}
## 4                                                                                                                                                                     μ∈R{\\displaystyle \\mu \\in \\mathbb {R} } = mean (location)σ2>0{\\displaystyle \\sigma ^{2}>0} = variance (squared scale)
## 5                                                                                                                                                                                                                                                         x∈R{\\displaystyle x\\in \\mathbb {R} }
## 6                                                                                                                                                                          12πσ2e−(x−μ)22σ2{\\displaystyle {\\frac {1}{\\sqrt {2\\pi \\sigma ^{2}}}}e^{-{\\frac {(x-\\mu )^{2}}{2\\sigma ^{2}}}}}
## 7                                                                                                                                                   12[1+erf⁡(x−μσ2)]{\\displaystyle {\\frac {1}{2}}\\left[1+\\operatorname {erf} \\left({\\frac {x-\\mu }{\\sigma {\\sqrt {2}}}}\\right)\\right]}
## 8                                                                                                                                                                                                      μ+σ2erf−1⁡(2F−1){\\displaystyle \\mu +\\sigma {\\sqrt {2}}\\operatorname {erf} ^{-1}(2F-1)}
## 9                                                                                                                                                                                                                                                                         μ{\\displaystyle \\mu }
## 10                                                                                                                                                                                                                                                                        μ{\\displaystyle \\mu }
## 11                                                                                                                                                                                                                                                                        μ{\\displaystyle \\mu }
## 12                                                                                                                                                                                                                                                                σ2{\\displaystyle \\sigma ^{2}}
## 13                                                                                                                                                                                                                                                                            0{\\displaystyle 0}
## 14                                                                                                                                                                                                                                                                            0{\\displaystyle 0}
## 15                                                                                                                                                                                                                         12log⁡(2πeσ2){\\displaystyle {\\frac {1}{2}}\\log(2\\pi e\\sigma ^{2})}
## 16                                                                                                                                                                                                                               exp⁡(μt+σ2t2/2){\\displaystyle \\exp(\\mu t+\\sigma ^{2}t^{2}/2)}
## 17                                                                                                                                                                                                                             exp⁡(iμt−σ2t2/2){\\displaystyle \\exp(i\\mu t-\\sigma ^{2}t^{2}/2)}
## 18 I(μ,σ)=(1/σ2002/σ2){\\displaystyle {\\mathcal {I}}(\\mu ,\\sigma )={\\begin{pmatrix}1/\\sigma ^{2}&0\\\\0&2/\\sigma ^{2}\\end{pmatrix}}} \nI(μ,σ2)=(1/σ2001/(2σ4)){\\displaystyle {\\mathcal {I}}(\\mu ,\\sigma ^{2})={\\begin{pmatrix}1/\\sigma ^{2}&0\\\\0&1/(2\\sigma ^{4})\\end{pmatrix}}}
```

>>>>>>> blog 9 posts up
