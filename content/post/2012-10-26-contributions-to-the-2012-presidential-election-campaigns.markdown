---
author: mine
comments: true
date: 2012-10-26 21:20:01+00:00
layout: post
link: http://citizen-statistician.org/2012/10/26/contributions-to-the-2012-presidential-election-campaigns/
slug: contributions-to-the-2012-presidential-election-campaigns
title: Contributions to the 2012 Presidential Election Campaigns
wordpress_id: 183
categories:
- Data
- pret-a-porter
- Teaching
- teaching
---

With fewer than two weeks left till the US presidential elections, motivating class discussion with data related to the candidates, elections, or politics in general is quite easy. So for yesterday's lab we used data released by The Federal Election Commission on contributions made to 2012 presidential campaigns. I came across the data last week, via a [post](http://www.guardian.co.uk/news/datablog/interactive/2012/oct/19/us-presidential-election-fundraising) on The Guardian Datablog. The post has a nice [interactive feature](http://public.tableausoftware.com/views/USAElectionContributions_1/StateLevelContributions?&:exclude=State%20Level&:sync_session=vizql029/83febbf2-0:0) for analyzing data from all contributions. The students started the lab by exploring the data using this applet, and then moved on to analyzing the data in R.

The original dataset can be found [here](http://www.fec.gov/disclosurep/PDownload.do). You can download data for all contributions (~620 MB csv file), or contributions by state (~16 MB for North Carolina, for example). The complete dataset has information on over 3.3 million contributions. The students worked with a random sample of 10,000 observations from this dataset. I chose to not use the entire population data because (1) it's too large to efficiently work with in an introductory stats course, and (2) we're currently covering inference so a setting where you start with random sample data to infer something about the population felt more natural.

While the data come in csv format, loading the data into R is slightly problematic. For some reason, all rows except the header row end with a comma, and hence naively loading the data into R using the read.csv function results in an error as R sees the extra comma as indicating an additional column and complains the header row does not have the same length as the rest of the dataset. Below are a couple ways to resolve this problem:

  * One solution is to simply open the csv file in Excel, and resave. This eliminates the spurious commas at the end of each line, making it possible to load the data using the read.csv function. However this solution is not ideal for the large dataset of all contributions.

  * Another solution for loading the population data (somewhat quickly) and taking a random sample is presented below:

```
x = readLines("P00000001-ALL.csv")
n = 10000 # desired sample size
s = sample(2:length(x), n)
header = strsplit(x[1],",")[[1]]
d = read.csv(textConnection(x[s]), header = FALSE)
d = d[,-ncol(d)]
colnames(d) = header
```

Our lab focused on comparing average contribution amounts among elections and candidates. But these data could also be used to compare contributions from different geographies (city, state, zip code), or to explore characteristics of contributions from individuals of various occupations, individuals vs. PACs etc.

If you're interested, there should still be enough time for you to squeeze an analysis/discussion of these data in your class before the elections. But even if not, the data should still be interesting after November 6.
