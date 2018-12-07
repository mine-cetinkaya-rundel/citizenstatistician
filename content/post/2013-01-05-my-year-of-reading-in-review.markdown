---
author: andy
comments: true
date: 2013-01-05 23:53:36+00:00
layout: post
link: http://citizen-statistician.org/2013/01/05/my-year-of-reading-in-review/
slug: my-year-of-reading-in-review
title: My Year of Reading in Review
wordpress_id: 331
categories:
- Data
- personal
---

Two years ago, I made a New Year's Resolution to read more books. At that point I joined [GoodReads](http://www.goodreads.com) to hold myself accountable. I read 47 books that year (at least that I recorded). In 2012, I didn't re-make that resolution, and my reading productivity dropped to 29 (really 26 since I quit reading 3 books). While the number of books is lower, I did some minor analyses on these books based on data I scraped from GoodReads and Amazon.

One summary I created was to examine the number of books I read per month. I also wanted to account for the fact that some books are a lot shorter than others, so in addition I looked at the average number of pages I read per month as well.

[![Number of books and average pages read per month in 2012.](http://citizen-statistician.org/wp-content/uploads/2013/01/Bookplot-1024x426.jpg)](http://citizen-statistician.org/2013/01/05/my-year-of-reading-in-review/bookplot/) Number of books and average pages read per month in 2012.

It is clear that May and December are prolific reading months for me. My interpretation is that these are the months that semesters end, and very often I retreat into the pages of a book or two to escape for a bit.

How do I rate these books I read? Are Amazon and GoodReads raters giving the books I read the same rating?

[![Average rating of the books I read in 2012 for Amazon and GoodReads raters. Size and color of the points indicate my GoodReads rating.](http://citizen-statistician.org/wp-content/uploads/2013/01/Bookplot5.jpg)](http://citizen-statistician.org/2013/01/05/my-year-of-reading-in-review/bookplot5/) Average rating of the books I read in 2012 for Amazon and GoodReads raters. Size and color of the points indicate my GoodReads rating.

I gave mostly 3/5 and 4/5 stars to the books I read. It is clear from the plot that there is an overall positive relationship: books that are rated highly by GoodReads raters are, on average, the same books being rated highly by Amazon raters–and vice-versa.

What book did I give a rating of 5/5 to? The synopsis of my reading year, including the answer to this question, is available here [[2012-Annual-Reading-Synopsis](http://citizen-statistician.org/2013/01/05/my-year-of-reading-in-review/2012-annual-reading-synopsis/)].

I have also made the spreadsheet data (from both 2011 and 2012) available publicly on GoogleDocs [[data](https://docs.google.com/spreadsheet/pub?key=0AvanLJO1M39wdENZajR0RHJMSmZTWWtLNzhHMi1ySUE&single=true&gid=0&output=csv)].

Here is the R code to access that data.

```
library(RCurl)
myCsv <- getURL("https://docs.google.com/spreadsheet/pub?key=0AvanLJO1M39wdENZajR0RHJMSmZTWWtLNzhHMi1ySUE&single=true&gid=0&output=csv")
books <- read.csv(textConnection(myCsv))
```
