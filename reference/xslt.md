# XSLT 1.0 Transformations

Transform an XML document by applying an XSL stylesheet. Usually returns
the transformed
[xml_document](http://xml2.r-lib.org/reference/xml_new_document.md),
unless the stylesheet has `<xsl:output method="text">` in which case we
return a text string.

## Usage

``` r
xml_xslt(doc, stylesheet, params)

xslt_version()
```

## Arguments

- doc:

  xml document as returned by
  [xml2::read_xml](http://xml2.r-lib.org/reference/read_xml.md)

- stylesheet:

  another xml document containing the XSL stylesheet

- params:

  named list or vector with additional XSLT parameters

## Details

This implementation supports XSLT 1.0 features plus most of the EXSLT
set of processor-portable extensions functions. Unfortunately XSLT 2.0
or 3.0 features are only available in proprietary libraries and
currently unsupported. However XSLT 2.0 is not widely adopted anyway
because it is unavailable in most browsers.

## Examples

``` r
doc <- read_xml(system.file("examples/cd_catalog.xml", package = "xslt"))
style <- read_xml(system.file("examples/cd_catalog.xsl", package = "xslt"))
html <- xml_xslt(doc, style)
cat(as.character(html))
#> <html><body>
#> <h2>My CD Collection</h2>
#> <table border="1">
#> <tr bgcolor="#9acd32">
#> <th>Title</th>
#> <th>Artist</th>
#> </tr>
#> <tr>
#> <td>Empire Burlesque</td>
#> <td>Bob Dylan</td>
#> </tr>
#> <tr>
#> <td>Still got the blues</td>
#> <td>Gary Moore</td>
#> </tr>
#> <tr>
#> <td>One night only</td>
#> <td>Bee Gees</td>
#> </tr>
#> <tr>
#> <td>Romanza</td>
#> <td>Andrea Bocelli</td>
#> </tr>
#> <tr>
#> <td>Black angel</td>
#> <td>Savage Rose</td>
#> </tr>
#> <tr>
#> <td>1999 Grammy Nominees</td>
#> <td>Many</td>
#> </tr>
#> </table>
#> </body></html>
```
