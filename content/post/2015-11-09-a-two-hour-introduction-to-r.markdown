---
author: mine
comments: true
date: 2015-11-09 12:16:43+00:00
layout: post
link: http://citizen-statistician.org/2015/11/09/a-two-hour-introduction-to-r/
slug: a-two-hour-introduction-to-r
title: A two-hour introduction to data analysis in R
wordpress_id: 999
categories:
- Computing
- Data
- rstats
- teaching
---

A few weeks ago I gave a two-hour Introduction to R workshop for the [Master of Engineering Management](http://memp.pratt.duke.edu/) students at Duke. The session was organized by the student-led [Career Development and Alumni Relations](http://www.dukemempdc.org/cdar) committee within this program. The slides for the workshop can be found [here](http://rpubs.com/minebocek/117428) and the source code is available [on GitHub](https://github.com/mine-cetinkaya-rundel/rworkshop-mem).

Why might this be of interest to you?



	
  * The materials can give you a sense of what's feasible to teach in two hours to an audience that is not scared of programming but is new to R.

	
  * The workshop introduces the `ggplot2` and `dplyr` packages without the `diamonds` or `nycflights13` datasets. I have nothing against the these datasets, in fact, I think they're great for introducing these packages, but frankly I'm a bit tired of them. So I was looking for something different when preparing this workshop and decided to use the [North Carolina Bicycle Crash Data](https://opendurham.nc.gov/explore/dataset/north_carolina_bicycle_crash_data_heatmap_/?tab=metas) from [Durham OpenData](https://opendurham.nc.gov/page/home/). This choice had some pros and some cons:

	
    * Pro - open data: Most people new to data analysis are unaware of open data resources. I think it's useful to showcase such data sources whenever possible.

	
    * Pro - medium data: The dataset has 5716 observations and 54 variables. It's not large enough to slow things down (which can especially be an issue for visualizing much larger data) but it's large enough that manual wrangling of the data would be too much trouble.

	
    * Con: The visualizations do not really reveal very useful insights into the data. While this is not absolutely necessary for teaching syntax, it would have been a welcome cherry on top...




	
  * The raw dataset has a feature I love -- it's been damaged due (most likely) to being opened in Excel! One of the variables in the dataset is age group of the biker (`BikeAge_gr`). Here is the age distribution of bikers as they appear in the original data:

```
##    BikeAge_Gr crash_count
##    (chr)      (int)
## 1  0-5        60
## 2  10-Jun     421
## 3  15-Nov     747
## 4  16-19      605
## 5  20-24      680
## 6  25-29      430
## 7  30-39      658
## 8  40-49      920
## 9  50-59      739
## 10 60-69      274
## 11 70         12
## 12 70+        58
```

Obviously the age groups `10-Jun` and `15-Nov` don't make sense. This is a great opportunity to highlight the importance of exploring the data before modeling or doing something more advanced with it. It is also an opportunity to demonstrate how merely opening a file in Excel can result in unexpected issues. These age groups should instead be 6-10 (not June 10th) and 11-15 (not November 15th). Making these corrections also provides an opportunity to talk about text processing in R.

I should admit that I don't have evidence of Excel causing this issue. However this is my best guess since "helping" the user by formatting date fields is standard Excel behaviour. There may be other software out there that also do this that I'm unaware of...

If you're looking for a non-`diamonds` or non-`nycflights13` introduction to R / `ggplot2` / `dplyr` feel free to use materials from this workshop.
