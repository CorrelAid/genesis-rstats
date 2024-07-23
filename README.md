
<!-- README.md is generated from README.Rmd. Please edit that file -->

# restatis

<!-- badges: start -->

[![CRAN
status](https://www.r-pkg.org/badges/version/restatis)](https://CRAN.R-project.org/package=restatis)
[![R-CMD-check](https://github.com/CorrelAid/restatis/actions/workflows/R-CMD-check.yaml/badge.svg)](https://github.com/CorrelAid/restatis/actions/workflows/R-CMD-check.yaml)
[![Codecov test
coverage](https://codecov.io/gh/CorrelAid/restatis/branch/main/graph/badge.svg)](https://app.codecov.io/gh/CorrelAid/restatis?branch=main)
[![Lifecycle:
experimental](https://img.shields.io/badge/lifecycle-experimental-orange.svg)](https://lifecycle.r-lib.org/articles/stages.html#experimental)
<!-- badges: end -->

restatis is a wrapper around the RESTful API that provides access to the
three main databases of German official statistics:

- The [**GENESIS database** of the Federal Statistical Office of Germany
  (Destatis)](https://www-genesis.destatis.de/genesis/online).
- [**regionalstatistik.de** which is the database of the German Länder
  (Regionaldatenbank)](https://www.regionalstatistik.de/genesis/online/).
- The [database of the **German 2022 Census** (Zensus
  2022)](https://ergebnisse.zensus2022.de/datenbank/online/).

All functions work on either one of them, on all of them or just on a
selection.

## Installation

You can install the released version of {restatis} from CRAN:

``` r
install.packages("restatis")
```

Or install the development version of {restatis} from
[GitHub](https://github.com/CorrelAid/restatis) with:

``` r
# install.packages("devtools")
devtools::install_github("CorrelAid/restatis")
```

## Usage

### Authentication

To access each one of the APIs, you need to have an account that you can
create on the homepage (see links to them above) and store your username
and password for use in R with `restatis::gen_auth_save()` (see
`?gen_auth_save` for more details). The Zensus 2022 database does
support authentication with an API token as well.

### Main features

{restatis} provides functions (prefixed with `gen_`) for finding,
exploring, and retrieving data from the three supported APIs. See the
[“Basic restatis workflow”
vignette](https://correlaid.github.io/restatis/articles/restatis.html)
for an overview of the main features of the package.

In a short overview, there are functions divided in two main parts,
searching for (meta)data and retrieving data:

#### Searching for (meta)data

- **gen_catalogue()**: Search the API’s catalogue of data
- **gen_find()**: Find objects related to a search term
- **gen_metadata()**: Find meta data to an objects
- **gen_alternative_terms()**: Find alternative terms to a search term
- **gen_modified_data()**: Find out when an object has last been
  modified
- **gen_objects2stat()**, **gen_objects2var()**, **gen_var2stat()**,
  **gen_val2var()**, **gen_val2var2stat()** and **gen_search_vars()**:
  Find objects, statistics, variables and values related to each other

#### Retrieving data

- **gen_cube()**: Using this function, you can download ‘cube’ objects
- **gen_table()**: Using this function, you can download ‘table’ objects
- **gen_list_jobs()** and **gen_download_job()**: Using this function,
  you can find and download previously created jobs (large tables)

#### Other functions

- **gen_logincheck()**: Perform a logincheck to test your credentials
- **gen_qualitysigns()**: Get a list of quality signs (special
  characters) found in the API’s tables
- **gen_update_evas()**: Manually scrape a newer version of the EVAS
  numbers (official statistic IDs)

### Caching

{restatis} uses [**memoisation**](https://github.com/r-lib/memoise) to
cache query results. This means that if you call a function multiple
times with the same input, the values returned the first time are stored
and reused from the second time.

Cached objects are stored in the memory and do not persist across R
sessions.

## Disclaimer

This package is in no way affiliated with the German Federal Statistical
Office (Destatis) or the ‘Verbund Statistische Ämter des Bundes und der
Länder’. It is a simple wrapper providing R functions to access
Destatis’ API. The package authors are in no way responsible for the
data that can be retrieved using its functions. The license of this
package solely applies to its source code.
