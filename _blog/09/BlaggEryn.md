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

    current_weather<-function(code){
      checkmate::assertCharacter(code)
      
      weatherData <- read_xml(paste0("https://w1.weather.gov/xml/current_obs/",code,".xml")) %>%
        xml_children() %>%
        xml_text() %>%
        .[c(7,8,9,11,14,18,20)] %>%
        t() %>%
        data.frame() %>%
        setNames(c("stationID","lat","long","lastUpdate","temp(F)","windDirection","windSpeed(MPH)"))
      
      checkmate::assertDataFrame(weatherData,types = c("numeric", "factor"), min.rows = 1, col.names = "named")
      weatherData
    }

1.  Which HTML tags did you investigate? Describe how to format at least
    3 separate pieces of a document using HTML tags.

    -Color:

<!--html_preserve-->
<h1 style="background-color:rgb(60, 179, 113);color:Yellow;border:10px dashed #F10909">
Testing.
</h1>
<!--/html_preserve-->
    -Links:

<!--html_preserve-->
<style>
a:link, a:visited {
  background-color: rgb(60, 179, 113);
  color: white;
  padding: 15px 25px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
}

a:hover, a:active {
  background-color: #F10909;
}
</style>
<a href="https://findtheinvisiblecow.com/" target="_blank">some fun
things about some fun things website</a> <!--/html_preserve-->

Tables:

<!--html_preserve-->
<table style="width:50%">
<tr>
<th>
Games
</th>
<th>
Fact
</th>
</tr>
<tr>
<td>
Tick tack toe
</td>
<td>
no one ever wins.
</td>
</tr>
<tr>
<td>
Tag
</td>
<td>
the key is to hide.
</td>
</tr>
<tr>
<td>
hide and go seek
</td>
<td>
wish you were small.
</td>
</tr>
</table>
<!--/html_preserve-->
1.  Compile this Rmarkdown document to HTML, then open the HTML file in
    a web browser. Open the inspector console for your browser
    (Ctrl-Shift-I in Chrome, Ctrl-Shift-C in Firefox) and look at the
    HTML code corresponding to various parts of the document. <br>
    Answer the following questions:

    -   What types of tags did you find? Width, height of frame broader
        and font sizes.

    -   How are code chunks formatted in HTML? R code chunks are
        formatted with pre class=“r” tags. Style parameters including
        “background color”, and “border”. The actual text is stored
        within a span class=“hljs” tag, which has a number of style
        parameters to indicate the color and emphasis of the text.

    -   What differences are there in the HTML markup for R code chunks
        and R output blocks?

The output blocks do not fall under the &lt;pre class=“r”&gt; tag and
follow the default class.

1.  In R, the `rvest` package, which is part of the tidyverse, makes it
    (relatively) easy to pull specific pieces from structured documents.
    The `html_nodes` function selects nodes using either xpath or css,
    and additional functions such as `html_attrs`, `html_text`, and
    `html_table` pull information out of the markup text.<br> Choose a
    Wikipedia page that has at least one image to test the `rvest`
    package out

<!-- -->

    library(rvest)
    aussie <- read_html("https://en.wikipedia.org/wiki/Australian_Shepherd")

    html_node(aussie,"img") %>% 
      xml_attr(attr="src") %>%
      paste0("https:",.) %>%
      magick::image_read()

<img src="../figure/09/BlaggEryn/unnamed-chunk-2-1.png" width="219" />

    html_nodes(aussie,"table")[3] %>%
      html_attr("class")

    ## [1] "infobox collapsible"

Remember, just because you have the HTML file doesn’t mean you should
commit it to your git repository!!! Delete the HTML file now if you’re
going to be tempted to accidentally commit and push it.

------------------------------------------------------------------------

### Going further (Optional Reading): Dynamic Web Pages - Javascript, AJAX, PHP, ASP, and more!

Not all web pages are the same. Static web pages have content that is
pre-specified, and when the page is loaded all of the content is just…
there. These pages are the easiest to scrape, because the HTML file
already contains all of the information needed to render the page.
Dynamic web pages have a basic HTML layout, and then scripting languages
are used to inject content into the pages at some point after the
initial page loads. Using `xml2::read_html()` on these pages will get
you a different HTML file than the one you see when loading the page in
your browser.

If you are interested in learning more about how to scrape dynamic web
pages, take a look at the `Rselenium` or `splashR` packages. These
packages emulate a browser (or launch one for you to control using R),
allowing the scripting languages to inject page content before providing
you with the updated HTML file containing the information you actually
wanted in the first place.

Note: Not all websites which use javascript (or other scripting
languages) are difficult to scrape (at this point, practically every web
page uses javascript somewhere), but when javascript is used to inject
data from a database after the page initially loads, it’s likely that
you’ll have to do a bit more work to get at the data.

Instructions:
-------------

Update your forked version of the ‘blog-2019’ repository (or re-fork it
after deleting your previous repo).

Save a **copy** of this file, replacing “Lastname” and “Firstname” with
your own and *leave the original unedited*. (Note: Lastname = your
family name, Firstname = your given name)

In **your copy**, replace the `title:` and `author:` fields in the YAML
above, while leaving the remaining fields intact. Remove the background
and the instructions sections and write your blog post!

Once you are done, **create a pull request** to upload your changes to
the original repository. Do not commit the compiled HTML file to the
repository.
