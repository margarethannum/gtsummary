
<!-- README.md is generated from README.Rmd. Please edit that file -->

<!-- badges: start -->

[![Travis build
status](https://travis-ci.org/ddsjoberg/gtsummary.svg?branch=master)](https://travis-ci.org/ddsjoberg/gtsummary)
[![AppVeyor build
status](https://ci.appveyor.com/api/projects/status/github/ddsjoberg/gtsummary?branch=master&svg=true)](https://ci.appveyor.com/project/ddsjoberg/gtsummary)
[![Coverage
status](https://codecov.io/gh/ddsjoberg/gtsummary/branch/master/graph/badge.svg)](https://codecov.io/github/ddsjoberg/gtsummary?branch=master)
[![CRAN
status](https://www.r-pkg.org/badges/version/gtsummary)](https://cran.r-project.org/package=gtsummary)
[![](https://cranlogs.r-pkg.org/badges/gtsummary)](https://cran.r-project.org/package=gtsummary)
[![Lifecycle:
maturing](https://img.shields.io/badge/lifecycle-maturing-blue.svg)](https://www.tidyverse.org/lifecycle/#maturing)
<!-- badges: end -->

## gtsummary <a href='https://github.com/ddsjoberg/gtsummary'><img src='man/figures/logo.png' align="right" height="120" /></a>

The {gtsummary} package provides an elegant, flexible, concise way to
create publication-ready and reproducible analytical tables using the
**R** programming language. The {gtsummary} package summarizes data
sets, regression models, and more, using sensible defaults with highly
customizable capabilities to present results.

  - [Summarize **data frames or
    tibbles**](http://www.danieldsjoberg.com/gtsummary/articles/tbl_summary.html)
    easily. Perfect for creating a **Table 1** in **R**, comparing group
    demographics, and more. Detects continuous, categorical, and binary
    variables and also includes amount of missingness in each variable.

  - [Summarize **regression
    models**](http://www.danieldsjoberg.com/gtsummary/articles/tbl_regression.html)
    and include reference rows for categorical variables. Common
    regression models, such as logistic regression and Cox proportional
    hazards regression, are automatically identified and the tables are
    pre-filled with appropriate column headers (i.e. Odds Ratio, and
    Hazard Ratio).

  - [**Customize gtsummary
    tables**](http://www.danieldsjoberg.com/gtsummary/reference/index.html#section-general-formatting-styling-functions)
    using a growing list of formatting/styling functions.
    **[Bold](http://www.danieldsjoberg.com/gtsummary/reference/bold_italicize_labels_levels.html)**
    labels,
    **[italicize](http://www.danieldsjoberg.com/gtsummary/reference/bold_italicize_labels_levels.html)**
    levels, **[add
    p-value](http://www.danieldsjoberg.com/gtsummary/reference/add_p.html)**
    to summary tables,
    **[style](http://www.danieldsjoberg.com/gtsummary/reference/style_percent.html)**
    the statistics however you choose,
    **[merge](http://www.danieldsjoberg.com/gtsummary/reference/tbl_merge.html)**
    or
    **[stack](http://www.danieldsjoberg.com/gtsummary/reference/tbl_stack.html)**
    tables to present results side by side… there are so many
    possibilities to reproducibly create the table of your dreams\!

  - **Report statistics inline** from summary tables and regression
    summary tables in **Rmarkdown** with **[Inline
    Reporting](http://www.danieldsjoberg.com/gtsummary/articles/tbl_summary.html#inline_text)**
    reporting functions. Make your reports completely reproducible\!

By leveraging [{broom}](https://broom.tidyverse.org/),
[{gt}](https://gt.rstudio.com/), and
[{labelled}](http://larmarange.github.io/labelled/) packages,
{gtsummary} creates beautifully formatted, ready-to-share tables in a
single line of R code\!

Check out the examples below, review the
[vignettes](http://www.danieldsjoberg.com/gtsummary/articles/) for a
detailed exploration of the output options, and view the
[gallery](http://www.danieldsjoberg.com/gtsummary/articles/gallery.html)
for various customization examples.

## Installation

The {gtsummary} package was written as a companion to the {gt} package
from RStudio, and it is recommended to install both {gt} and
{gtsummary}. The {gt} package is not automatically installed. If {gt} is
not installed, `knitr::kable()` will be used to produce the summary
tables. You can install {gtsummary} and {gt} with the following code.

1.  Install {gtsummary}
    
    ``` r
    install.packages("gtsummary")
    ```

2.  Install {gt} from GitHub (recommended)
    
    ``` r
    install.packages("remotes")
    remotes::install_github("rstudio/gt")
    ```

Install the development version of {gtsummary} with:

``` r
remotes::install_github("ddsjoberg/gtsummary")
```

## Examples

### Summary Table

``` r
library(gtsummary)
t1 <-
  tbl_summary(
    data = trial[c("trt", "age", "grade", "response")],
    by = trt
  ) %>%
  add_p() 
```

<img src="man/figures/README-tbl_summary_print-1.png" width="66%">

### Regression Models

``` r
mod1 <- glm(response ~ trt + age + grade, trial, family = binomial)

t2 <- tbl_regression(mod1, exponentiate = TRUE)
```

<img src="man/figures/README-tbl_regression_print-1.png" width="50%">

### Side-by-side Regression Models

Side-by-side regression model results from `tbl_merge()`

<img src="man/figures/tbl_merge_ex1.png" width="66%">

The {gtsummary}
[vignettes/tutorials](http://www.danieldsjoberg.com/gtsummary/articles/)
contain detailed examples.

Review even more output options in the [table
gallery](http://www.danieldsjoberg.com/gtsummary/articles/gallery.html).

## Print Engine

{gtsummary} uses the {gt} package to print all summary tables. In
addition to supporting {gt}, the {gtsummary} package works well with
`knitr::kable()`. This is particularly useful when outputting documents
to Microsoft Word. If the {gt} package is not installed, {gtsummary}
will fall back to `knitr::kable()`. To explicitly set the printing
engine, set the option in the script or in the user- or project R
profile, `.Rprofile`.

    options(gtsummary.print_engine = "kable") 

or

    options(gtsummary.print_engine = "gt")

Output from {kable} is less full featured compared to summary tables
produced with {gt}. For example, {kable} summary tables do not include
indentation, footnotes, and spanning header rows.

## Contributing

Please note that the {gtsummary} project is released with a [Contributor
Code of
Conduct](http://www.danieldsjoberg.com/gtsummary/CODE_OF_CONDUCT.html).
By contributing to this project, you agree to abide by its terms. A big
thank you to all contributors\!  
[@margarethannum](https://github.com/margarethannum)
