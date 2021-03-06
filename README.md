
<!-- README.md is generated from README.Rmd. Please edit that file -->

# cbpaper

[![Binder](http://mybinder.org/badge.svg)](http://beta.mybinder.org/v2/gh/sahirbhatnagar/cbpaper/master?urlpath=rstudio)  
[![Travis-CI Build
Status](https://travis-ci.org/sahirbhatnagar/cbpaper.svg?branch=master)](https://travis-ci.org/sahirbhatnagar/cbpaper)

Source code for casebase paper. Install the following packages from
GitHub

``` r
# install.packages("devtools")

devtools::install_github("rstudio/rticles") # for template
devtools::install_github("benmarwick/rrtools") # for building the research compendium/docker container
```

# To contribute

1.  Modify the `analysis/paper/paper.Rmd` file.
2.  Run `rrtools::add_dependencies_to_description()`. This command will
    ensure all used packages are added to the DESCRIPTION file.
3.  Compile the `paper.Rmd` file
4.  Commit and push your changes to GitHub

# Docker Image

``` bash
# https://github.com/rocker-org/rocker/wiki/Using-the-RStudio-image
# https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-16-04
# https://docs.docker.com/engine/reference/run/ which explains the run tags
docker pull sahirbhatnagar/cbpaper:latest # pulls the image locally
docker images # see list of images
docker ps -a # also see list of images
docker run -d -p 8787:8787 -e PASSWORD=<YOUR_PASS> --name cbpaper sahirbhatnagar/cbpaper
# then go to http://localhost:8787
# username is rstudio, password is what you specified
# in R do: setwd('/cbpaper/') and then you should see the folder with all the materials in the folder RStudio pane
docker stop cbpaper # this can be what you supplied to --name in the above command or the container ID
```

# File structure of repo

    analysis/
    |
    ├── paper/
    │   ├── paper.Rmd       # this is the main document to edit. just testing code for now
    │   └── references.bib  # this contains the reference list information
    ├── figures/            # location of the figures produced by the Rmd
    |
    ├── data/
        ├── raw_data/       # data obtained from elsewhere
        └── derived_data/   # data generated during the analysis

# Outline

1.  Introduction
2.  Theory
3.  Implementation Details (Population time plots, Data analysis)
4.  Case study 1 ERPSC (Single Event)
5.  Case study 2 Bone Marrow Transplant (Competing risk)
6.  Variable Selection (see
    <https://cran.r-project.org/web/packages/TCGA2STAT/vignettes/TCGA2STAT.html>
    for HD survival Data)
7.  Discussion

# To-DO (July 15)

1)  Max: implement multinomial glmnet
2)  Jesse: tests single and competing risk variable selection on TCGA.
    Look at variable selection litterature for competing risks. Find
    data
3)  Sahir: Implementation details (population time plots)
4)  Sahir: Review existing literature. What exists in terms of package.
    Look at Hanley and Miettinen. CRAN task view.

# To-DO (July 22)

1)  Max: theory text
2)  Jesse: tests single event variable selection on TCGA. Look at
    variable selection litterature for single. Plot KM curve with
    casebase+glmnet, and glmnet+cox
3)  Sahir: Implementation details (population time plots), check issue.
4)  Sahir: Review existing literature. What exists in terms of package.
    Look at Hanley and Miettinen. CRAN task
view.

| Package                                                 |       on CRAN        |                                    documentation                                    |                               Published                                | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |                                                                        Function call                                                                         |
| :------------------------------------------------------ | :------------------: | :---------------------------------------------------------------------------------: | :--------------------------------------------------------------------: | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------: |
| [flexsurv](https://cran.r-project.org/package=flexsurv) | :heavy\_check\_mark: | [Vignette](https://cran.r-project.org/web/packages/flexsurv/vignettes/flexsurv.pdf) | [Jackson, C. JSS 2016](https://www.jstatsoft.org/article/view/v070i08) | Fully-parametric. Any parametric time-to-event distribution may be fitted if the user supplies a probability density or hazard function, and ideally also their cumulative versions. Standard survival distributions are built in, including the three and four-parameter generalized gamma and Fdistributions. Any parameter of any distribution can be modelled as a linear or log-linear function of covariates. The package also includes the spline model of Royston and Parmar (2002), in which both baseline survival and covariate effects can be arbitrarily flexible parametric functions of time. See Table 1 for full list of distributions. | `flexsurvreg(Surv(recyrs, censrec) ~ group, data = bc, dist = "gengamma")` `flexsurvspline(Surv(recyrs, censrec) ~ group, data = bc, k = 1, scale = "odds")` |
| git diff                                                |       git diff       |                                      git diff                                       |                                   dd                                   | 44                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |                                                                              dd                                                                              |

# Casebase paper

[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh///master?urlpath=rstudio)

This repository contains the data and code for our paper:

> Authors, (YYYY). *Title of your paper goes here*. Name of journal/book
> <https://doi.org/xxx/xxx>

Our pre-print is online here:

> Authors, (YYYY). *Title of your paper goes here*. Name of
> journal/book, Accessed 04 Feb 2020. Online at
> <https://doi.org/xxx/xxx>

### How to cite

Please cite this compendium as:

> Authors, (2020). *Compendium of R code and data for Title of your
> paper goes here*. Accessed 04 Feb 2020. Online at
> <https://doi.org/xxx/xxx>

### How to download or install

You can download the compendium as a zip from from this URL:
</archive/master.zip>

Or you can install this compendium as an R package, pap, from GitHub
with:

``` r
# install.packages("devtools")
remotes::install_github("/")
```

### Licenses

**Text and figures :**
[CC-BY-4.0](http://creativecommons.org/licenses/by/4.0/)

**Code :** See the [DESCRIPTION](DESCRIPTION) file

**Data :** [CC-0](http://creativecommons.org/publicdomain/zero/1.0/)
attribution requested in reuse

### Contributions

We welcome contributions from everyone. Before you get started, please
see our [contributor guidelines](CONTRIBUTING.md). Please note that this
project is released with a [Contributor Code of Conduct](CONDUCT.md). By
participating in this project you agree to abide by its terms.
