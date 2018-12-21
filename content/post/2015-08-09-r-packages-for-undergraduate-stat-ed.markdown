---
author: mine
comments: true
date: 2015-08-09 13:31:08+00:00
layout: post
link: http://citizen-statistician.org/2015/08/09/r-packages-for-undergraduate-stat-ed/
slug: r-packages-for-undergraduate-stat-ed
title: R packages for undergraduate stat ed
wordpress_id: 925
categories:
- Computing
- rstats
- Teaching
---

The other day on the [isostat](http://www.amstat.org/committees/isostat/isostat.html) mailing list [Doug Andrews](http://www5.wittenberg.edu/academics/math/facultystaff/andrews.html) asked the following question:


<blockquote>Which R packages do you consider the most helpful and essential for undergrad stat ed? I ask in great part because it would help my local IT guru set up the way our network makes software available in our computer classrooms, but also just from curiosity.</blockquote>


Doug asked for a top 10 list, and a few people have already chimed in with great suggestions. I thought those not on the list might also have good ideas, so, with Doug's permission, I'm reposting the question here.

Here is my top 10 (ok, 12) list:
(Links go to vignettes or pages I find to be quickest / most useful references for those packages, but if you know of better resources, let me know and I'll update.)



	
  1. `[knitr](http://yihui.name/knitr/)` / `[rmarkdown](http://rmarkdown.rstudio.com/)` - for reproducible data analysis with literate programming, great set of tools that students can use from day 1 in intro stats all the way through to writing their undergrad theses

	
  2. `[dplyr](https://github.com/hadley/dplyr)` - for most data manipulation tasks, with the added benefit of piping (via magrittr)

	
  3. `[ggplot2](http://docs.ggplot2.org/current/)` - easy faceting allows for graphing multivariate relationships more easily than with base R (lattice is also good for that, but IMO ggplot2 graphics look more modern and lattice has a much steeper learning curve)

	
  4. `[openintro](https://cran.r-project.org/web/packages/openintro/openintro.pdf)` - or packages that come with the textbooks you use, great for pulling up any dataset from the text and building on it in class (a new version coming soon to fully complement 3rd edition of [OpenIntro Statistics](https://www.openintro.org/os))

	
  5. `[mosaic](http://mosaic-web.org/r-packages/)` - for consistent syntax for functions used in intro stat

	
  6. `[googlesheets](https://github.com/jennybc/googlesheets)` - for loading data directly from Google spreadsheets

	
  7. `[lubridate](https://cran.r-project.org/web/packages/lubridate/vignettes/lubridate.html)` - if you ever need to work with any date fields

	
  8. `[stringr](https://cran.r-project.org/web/packages/stringr/vignettes/stringr.html)` - for text parsing and manipulation

	
  9. `[rvest](http://blog.rstudio.org/2014/11/24/rvest-easy-web-scraping-with-r/)` - for scraping data off the web

	
  10. `[readr](https://github.com/hadley/readr)` / `[data.table](https://github.com/Rdatatable/data.table/wiki)` - for loading large datasets & default `stringsAsFactors = FALSE`


And the following suggestions from [Randall Prium](http://www.calvin.edu/~rpruim/) complement this list nicely:



	
  * `[readxl](https://github.com/hadley/readxl)` - for reading Excel data

	
  * `[tidyr](https://github.com/hadley/tidyr)` - for converting between wide and long formats and for the very useful `extract_numeric()`

	
  * `[ggvis](http://ggvis.rstudio.com/)` - `ggplot2` “done right” and tuned for interactive graphics

	
  * `[htmlwidgets](http://www.htmlwidgets.org/)` - this is actually a collection of packages for plots: see `leaflet` for maps and `dygraphs` for time series, for example


Note that most of these packages are for data manipulation and visualization. Methods specific packages that are useful / essential for a particular undergraduate program might depend on the focus of that program. Some packages that so far came up in the discussion are:

	
  * `[lme4](https://cran.r-project.org/web/packages/lme4/lme4.pdf)` - for mixed models

	
  * `[pwr](https://cran.r-project.org/web/packages/pwr/pwr.pdf)` - for showing sample size and power calculations


This blog post is meant to provide a space for continuing this discussion, so I'll ask the question one more time: _Which R packages do you consider the most helpful and essential for undergrad stat ed?_ Please add your responses to the comments.



PS: Thanks to [Michael Lopez](http://statsbylopez.com/) for suggesting that I post this list somewhere.
PPS: I should really be working on my fast-approaching [JSM talk](http://www.amstat.org/meetings/jsm/2015/onlineprogram/AbstractDetails.cfm?abstractid=314670).
