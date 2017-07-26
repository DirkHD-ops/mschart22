mschart R package
================

<!-- README.md is generated from README.Rmd. Please edit that file -->
[![Project Status: WIP - Initial development is in progress, but there has not yet been a stable, usable release suitable for the public.](http://www.repostatus.org/badges/latest/wip.svg)](http://www.repostatus.org/#wip) [![Build Status](https://travis-ci.org/ardata-fr/mschart.svg?branch=master)](https://travis-ci.org/ardata-fr/mschart) [![AppVeyor Build Status](https://ci.appveyor.com/api/projects/status/github/ardata-fr/mschart?branch=master&svg=true)](https://ci.appveyor.com/project/ardata-fr/mschart)

The `mschart` package provides a framework for easily create charts within 'Microsoft PowerPoint' documents.

Installation
------------

You can install the package from github with:

``` r
# install.packages("devtools")
devtools::install_github("ardata-fr/mschart")
```

Example
-------

This is a basic example which shows you how to create a line chart.

``` r
library(mschart)
library(officer)

linec <- ms_linechart(data = iris, x = "Sepal.Length",
                      y = "Sepal.Width", group = "Species")
linec <- chart_ax_y(linec, num_fmt = "0.00", rotation = -90)
```

Then use package `officer` to send the object as a chart.

``` r
doc <- read_pptx()
doc <- add_slide(doc, layout = "Title and Content", master = "Office Theme")
doc <- ph_with_chart(doc, value = linec)

print(doc, target = "example.pptx")
```
