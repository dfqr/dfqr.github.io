# DAByLite docs <a href="https://DAByLite.github.io"><img src="assets/images/DAByLite_hex.jpeg?raw=true" align="right" height="138" /></a>

[![jsDelivr](https://data.jsdelivr.com/v1/package/gh/dabylite/dabylite/badge)](https://www.jsdelivr.com/package/gh/dabylite/dabylite)
![visitors](https://visitor-badge.laobi.icu/badge?page_id=DAByLite.DAByLite.github.io)
[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)


<!--
![CI](https://github.com/JV-conseil/jekyll-theme-read-the-docs/workflows/CI/badge.svg?branch=develop)
[![License BSD 3-Clause](https://img.shields.io/badge/License-BSD%203--Clause-blue.svg)](LICENSE)
-->

| Find the R package                                             | Find the documentation                         |
|----------------------------------------------------------------|------------------------------------------------|
| [DAByLite Github repo](https://github.com/DAByLite/DAByLite)   | [DAByLite docs](https://dabylite.github.io/)   |

> Big data management in R with **da**ta **by**te **lite**

## What it does

Easily manage big data sets that can't fit into memory with minimum overhead.

## Quick start

1. **DAByLite is an R package, so first install R and probably an IDE/editor.**

The best installation istructions for R and RStudio can be found at [Posit](https://posit.co/download/rstudio-desktop/).

2. **Install the package from Github using the remotes package**

```{r}
install.packages("remotes")
remotes::install_github("DAByLite/DAByLite")
```

## Usage

```{r}
library(DAByLite)
```

1. **DAByLite uses CSV files, so first convert your file type to CSV.**

The burden is on the user to write the source data to CSV. Many tools have this capability and conversion tools are available.

2. **DAByLite checks your CSV formatting.**

Assuming your CSV file is called "mydata.csv".

```{r}
check_csv("mydata.csv")
```
DAByLite tells you if the format doesn't match the package's CSV standard. If no issues were detected, skip step 4.

3. **DAByLite will adapt your CSV to the DAByLite CSV standard.**

Assume you would like to write the source data "mydata.csv" to a new file called "mydata_formatted.csv".

```{r}
rewrite_csv("mydata.csv", "mydata_formatted.csv")
```

4. **DAByLite reads CSV data into an efficient format for reading.**

You can control the number of rows and columns to read efficiently. For example, say you want to read 1 million rows at a time of each column separately. Set rows to 1000000 and cols to 1.

```{r}
mydata = read_csv("mydata_formatted.csv", rows = 1000000, cols = 1)
```

5. **DAByLite reads CSV data into an efficient format for reading.**

Now, read the first 1 million rows of the first variable. Set x to 1 (first million rows) and y to 1 (first variable).

```{r}
read_partial(mydata, x = 1, y = 1)
```
