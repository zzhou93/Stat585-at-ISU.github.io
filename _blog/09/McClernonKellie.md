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

    getweather <- function(aircode){
      assertthat::assert_that(assertthat::is.string(aircode))
      assertthat::assert_that(str_length(aircode) == 4)
      newcode <- str_to_upper(aircode)
      url <- paste0("https://w1.weather.gov/xml/current_obs/",newcode,".xml")
      dta <- read_xml(url) %>% xml_children
      out <- data.frame(field = xml_name(dta), info = xml_text(dta)) %>% 
        tidyr::spread(field, info) %>% 
        select(station_id, latitude, longitude, observation_time, 
               temp_f, weather, wind_mph, wind_dir) %>%
        mutate_all(.funs = as.character) %>%
        mutate_at("observation_time", .funs = function(x){str_remove(x, "Last Updated on ")}) %>%
        mutate_at(vars(latitude, longitude, temp_f, wind_mph), .funs = as.numeric)
        
      return(out)
    }

    getweather("KCXW")

    ##   station_id latitude longitude         observation_time temp_f weather
    ## 1       KCXW  35.0199  -92.5551 Apr 2 2019, 10:55 am CDT     57    Fair
    ##   wind_mph wind_dir
    ## 1      8.1     West

1.  Which HTML tags did you investigate? Describe how to format at least
    3 separate pieces of a document using HTML tags.

I looked at the HTML tags for headings, lists, and URLs. For headings
the tags are “h” followed by a number 1-6 for how large you want your
heading. Then lists are first specificed if the list body is order or
unordered and then each item is called with the tag “li”. URL links have
the tag “a” with the URL pecified by the attribute “href”.

<h1>
This heading is the biggest
</h1>
<h2>
This is the penultimate largest heading!
</h2>
<h6>
This is the smallest heading. There were 5 levels of heading before this
one.
</h6>
<ol>
Lists are nice because they are…
<li>
Concise
</li>
<li>
Organized
</li>
<li>
Easy to skim
</li>
</ol>
<a href="https://xkcd.com/87/">Something to always keep in mind…</a>

1.  Compile this Rmarkdown document to HTML, then open the HTML file in
    a web browser. Open the inspector console for your browser
    (Ctrl-Shift-I in Chrome, Ctrl-Shift-C in Firefox) and look at the
    HTML code corresponding to various parts of the document. <br>
    Answer the following questions:

    -   What types of tags did you find?

    I found tags for heading, lists, urls, and preformatted texts
    &lt;pre&gt; (for the R-code).

    -   How are code chunks formatted in HTML?

    Code chunks are preformatted with class=“r”. Within the body of
    &lt;pre&gt; there are code tags that define the formatting for key
    words in R code and the separation of functions.

    -   What differences are there in the HTML markup for R code chunks
        and R output blocks?

    R code chunks are &lt;pre class=“r”&gt; but R output is only
    &lt;pre&gt; without the class of “r”. Both use &lt;code
    class=“hljs”&gt; for formatting the text.

2.  In R, the `rvest` package, which is part of the tidyverse, makes it
    (relatively) easy to pull specific pieces from structured documents.
    The `html_nodes` function selects nodes using either xpath or css,
    and additional functions such as `html_attrs`, `html_text`, and
    `html_table` pull information out of the markup text.<br> Choose a
    Wikipedia page that has at least one image to test the `rvest`
    package out

Remember, just because you have the HTML file doesn’t mean you should
commit it to your git repository!!! Delete the HTML file now if you’re
going to be tempted to accidentally commit and push it.

    library(rvest)

    polar <- read_html("https://en.wikipedia.org/wiki/Polar_bear")
    picurls <- polar %>% html_nodes("img") %>% html_attr("src")
    bearpics <- str_subset(picurls, "bear")

    knitr::include_graphics(bearpics[3])

![](//upload.wikimedia.org/wikipedia/commons/thumb/f/f5/Polar_bears_near_north_pole.jpg/220px-Polar_bears_near_north_pole.jpg)

    knitr::include_graphics(bearpics[7])

![](//upload.wikimedia.org/wikipedia/commons/thumb/a/af/Female_polar_bear_%28Ursus_maritimus%29_with_cub%2C_Svalbard.jpg/220px-Female_polar_bear_%28Ursus_maritimus%29_with_cub%2C_Svalbard.jpg)

    knitr::include_graphics(bearpics[12])

![](//upload.wikimedia.org/wikipedia/commons/thumb/d/d8/Polar_bear_arctic.JPG/220px-Polar_bear_arctic.JPG)

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
