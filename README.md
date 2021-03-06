
![](./man/figures/Loose_lips_might_sink_ships.jpg)

rOpenSci Unconf 18 Project : ropsec
===================================

[![Travis build status](https://travis-ci.org/ropenscilabs/ropsec.svg?branch=master)](https://travis-ci.org/ropenscilabs/ropsec) [![AppVeyor build status](https://ci.appveyor.com/api/projects/status/55vx8b5jckpa216a?svg=true)](https://ci.appveyor.com/project/czeildi/ropsec-w5fnj) [![Coverage status](https://codecov.io/gh/ropenscilabs/ropsec/branch/master/graph/badge.svg)](https://codecov.io/github/ropenscilabs/ropsec?branch=master)

Personal Workstation Safety Checks and Utilities

What's Inside The Tin
---------------------

The following functions are implemented:

-   [`sign_commits_with_key()`](#sign-commits) [![Lifecycle Status](https://img.shields.io/badge/lifecycle-maturing-blue.svg)](https://www.tidyverse.org/lifecycle/)
-   [`store_public_key()`](#sign-commits) [![Lifecycle Status](https://img.shields.io/badge/lifecycle-maturing-blue.svg)](https://www.tidyverse.org/lifecycle/)
-   [`summarize_system_checks()`](#lightweight-system-checks) [![Lifecycle Status](https://img.shields.io/badge/lifecycle-experimental-orange.svg)](https://www.tidyverse.org/lifecycle/)
-   [`full_on_audit()`](#audit) [![Lifecycle Status](https://img.shields.io/badge/lifecycle-experimental-orange.svg)](https://www.tidyverse.org/lifecycle/)

Installation
------------

``` r
devtools::install_github("ropenscilabs/ropsec")
```

To have vignettes available locally:

``` r
devtools::install_github("ropenscilabs/ropsec", build_vignettes = TRUE)
```

Usage
-----

``` r
library(ropsec)
```

### Sign commits with GPG key

For details see [`vignette("sign-commits", "ropsec")`](https://ropenscilabs.github.io/ropsec/articles/sign-commits.html).

``` r
key <- sign_commits_with_key("John Doe", "john.doe@gmail.com")
store_public_key(key)
```

<img src="man/figures/signed_commit.png" align="center"/>

### Lightweight system checks

``` r
ropsec::summarize_system_checks()
```

    ✔ | OK F W S | Context
    ✔ |  1       | SSH Configuration - existence
    ✔ |  2       | SSH Configuration - keys
    ✔ |  1       | SSH Configuration - key size
    ✔ |  1       | GPG Existence
    ✔ |  1       | macOS requires password after sleep or screen saver kicks in [0.1 s]
    ✖ |  0 1     | Firewall is enabled
    # ...

### Audit local machine in detail

E.g. what ports are used.

``` r
full_audit_results <- full_on_audit()
```

Collaborators
-------------

-   Bob Rudis @hrbrmstr
-   Kara Woo @karawoo
-   Karthik Ram @karthik
-   Ildi Czeller @czeildi

Please note that the `ropsec` project is released with a [Contributor Code of Conduct](CODE_OF_CONDUCT.md). By contributing to this project, you agree to abide by its terms.
