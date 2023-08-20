---
{"title":"R Package","alias":null,"type":"note","created":"2022-09-11T20:20:44","modified":"2022-09-19T00:00:10","dg-publish":true,"sup":[["R","r"]],"state":"done","permalink":"/r-package/","dgPassFrontmatter":true,"updated":"2022-09-19T00:00:10"}
---


# R Package

```r
# Install a package
install.packages("tidyverse")
# Load a package
library("tidyverse")
```

If we need to be explicit about where a function (or dataset) comes from, we’ll use the special form `package::function()`. For example, `ggplot2::ggplot()` tells you explicitly that we’re using the `ggplot()` function from the `ggplot2` package

To install from GitHub:

```R
library(devtools)
devtools::install_github("metalyrics/rmetacritic")
```
