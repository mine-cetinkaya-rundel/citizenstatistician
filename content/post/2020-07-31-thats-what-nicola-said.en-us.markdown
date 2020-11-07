---
title: That's what Nicola said
author: Mine Cetinkaya-Rundel
date: '2020-07-31'
slug: thats-what-nicola-said
categories:
  - musings
tags:
  - web scraping
  - sentiment analysis
  - text mining
  - tidyverse
editor_options:
  markdown:
    wrap: sentence
---

For the last four months, just about every week day at 12:30pm I have been watching the Fist Minister, Nicola Sturgeon, deliver her daily COVID-19 update.
If I've chatted with you about COVID during this time span, you have probably heard me say that I am *very* impressed by the way she delivers these updates daily.
I'll be honest, they are almost boring, but in the best possible way.
The last thing I want from a leader at this time is surprises, showmanship, or claims with no scientific basis.

<!-
-more-->

About a few weeks into the daily updates, I realized that the text for these speeches are published [on the Scottish Government website](https://www.gov.scot/collections/first-ministers-speeches/ "Texts of First Minister's COVID-19 speeches").
So, naturally, I downloaded the data and started analyzing it.
You can find the full analysis at [github.com/mine-cetinkaya-rundel/fm-speeches-covid19](https://github.com/mine-cetinkaya-rundel/fm-speeches-covid19 "GitHub repo analysing First Minister's COVID-19 speeches").
In this blog post I'll walk through parts of the analysis and show share some visualisations of the First Minister's speeches and how they compare to the speeches by the UK government.
The text of these speeches can be found [here](https://www.rev.com/blog/transcript-tag/united-kingdom-coronavirus-briefing-transcripts "Texts of UK Government COVID-19 speeches").

## Get First Minister's speeches

First, I checked to make sure we can, indeed, scrape these data with [`robotstxt::paths_allowed()`](https://docs.ropensci.org/robotstxt/reference/paths_allowed.html "robotstxt::paths_allowed()").


```r
robotstxt::paths_allowed("https://www.gov.scot/publications")
```

```
## 
 www.gov.scot
```

```
## [1] TRUE
```

For scraping the data and structuring it as a data frame, I used the [tidyverse](https://tidyverse.org/), [rvest](http://rvest.tidyverse.org/), and [lubridate](https://lubridate.tidyverse.org/) packages and the [here](https://here.r-lib.org/) package for proper file paths when saving the scraped data.


```r
library(tidyverse)
library(rvest)
library(lubridate)
library(here)
```

All speeches are linked from a single webpage.


```r
all_speeches_page_scot <- read_html("https://www.gov.scot/collections/first-ministers-speeches/")
```

Once we read this page, we can extract the URLs of the individual speeches using the [SelectorGadget](http://rvest.tidyverse.org/articles/selectorgadget.html) to locate the nodes and a little bit of string manipulation.


```r
covid_speech_urls_uk_scot <- all_speeches_page_scot %>%
  html_nodes(".collections-list a") %>%
  html_attr("href") %>%
  str_subset("covid-19") %>%
  str_c("https://www.gov.scot", .)

head(covid_speech_urls_uk_scot)
```

```
## [1] "https://www.gov.scot/publications/coronavirus-covid-19-update-first-ministers-speech-28-august-2020/"
## [2] "https://www.gov.scot/publications/coronavirus-covid-19-update-first-ministers-speech-27-august-2020/"
## [3] "https://www.gov.scot/publications/coronavirus-covid-19-update-first-ministers-speech-25-august-2020/"
## [4] "https://www.gov.scot/publications/coronavirus-covid-19-update-first-ministers-speech-24-august-2020/"
## [5] "https://www.gov.scot/publications/coronavirus-covid-19-first-ministers-speech-21-august-2020/"       
## [6] "https://www.gov.scot/publications/coronavirus-covid-19-update-first-ministers-speech-20-august-2020/"
```

Next, we define a function that we can use to scrape each page and save its contents as a tibble with columns for `title`, `date`, `location`, `abstract`, `text`, and `url`.


```r
scrape_speech_scot <- function(url){
  
  speech_page <- read_html(url)
  
  title <- speech_page %>%
    html_node(".article-header__title") %>%
    html_text()
  
  date <- speech_page %>%
    html_node(".content-data__list:nth-child(1) strong") %>%
    html_text() %>%
    dmy()
  
  location <- speech_page %>%
    html_node(".content-data__list+ .content-data__list strong") %>%
    html_text()
  
  abstract <- speech_page %>%
    html_node(".leader--first-para p") %>%
    html_text()
  
  text <- speech_page %>% 
    html_nodes("#preamble p") %>%
    html_text() %>%
    list()
  
  tibble(
    title    = title,
    date     = date,
    location = location,
    abstract = abstract,
    text     = text,
    url      = url
  )
  
}
```

And finally, map the function over the elements of `covid_speech_urls_uk_scot` that we defined earlier.
I'm using `map_dfr()` here since we want the result to be a data frame.


```r
covid_speeches_scot <- map_dfr(
  covid_speech_urls_uk_scot, 
  scrape_speech_scot
  )
```

This can take a little bit of time to run, so each time I've done this analysis, I save the result as an RDS file.
Note the use of `here::here()` to save the data in a folder called data in my project.
If you don't use the here package already, I strongly recommend [this blog post](https://malco.io/2018/11/05/why-should-i-use-the-here-package-when-i-m-already-using-projects/ "Why should I use the here package when I'm already using projects?") by Malcolm Barrett to convince yourself that it's a good idea!


```r
write_rds(
  covid_speeches_scot, 
  path = here::here("data", "covid-speeches-scot.rds")
  )
```

You can find the data as of July 30, 2020 [here](https://github.com/mine-cetinkaya-rundel/fm-speeches-covid19/blob/master/data/covid-speeches-scot.rds "First Minister's speeches data as of July 30, 2020").

This is a recipe I use very regularly for web scraping many pages:

-   write a function to scrape a single page

-   map the function over the list of URLs for the many pages you want to scrape with `map_dfr()`

-   end up with a tibble you can save and analyse

I also think that web scraping is a great motivation for introducing iteration and the purrr package to new learners.[^1]

[^1]: Mine Dogucu and I recently published a paper on webscraping where discuss this approach for teaching web scraping and iteration, with an example for scraping data from [OpenSecrets](https://www.opensecrets.org/ "OpenSecrets.org").
    See [here](https://www.tandfonline.com/doi/full/10.1080/10691898.2020.1787116 "Web Scraping in the Statistics and Data Science Curriculum: Challenges and Opportunities") for the paper (open access) and [here](https://github.com/mdogucu/web-scrape "GitHub repo: Web Scraping in the Statistics and Data Science Curriculum: Challenges and Opportunities") for the repo with the code for that example.

## Analyze First Minister's speeches

Alright, now let's take a look at

## Get UK Government's speeches
