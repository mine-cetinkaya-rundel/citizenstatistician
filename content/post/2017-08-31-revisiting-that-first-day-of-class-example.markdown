---
author: mine
comments: true
date: 2017-08-31 04:45:55+00:00
layout: post
link: http://citizen-statistician.org/2017/08/31/revisiting-that-first-day-of-class-example/
slug: revisiting-that-first-day-of-class-example
title: Revisiting that first day of class example
wordpress_id: 1199
---

About a year ago I wrote this post: [
![](http://citizen-statistician.org/wp-content/uploads/2017/08/first-day-of-class-1024x502.png)](http://citizen-statistician.org/2016/08/13/a-timely-first-day-of-class-example-for-fall-2016-trump-tweets/)

I wasn't teaching that semester, so couldn't take my own advice then, but thankfully (or the opposite of thankfully) Trump's tweets still make timely discussion.

I had two goals for presenting this example on the first day of my data science course (to an audience of all first-year undergraduates, with little to no background in computing and statistics):



 	
  1. Give a data analysis example with a familiar context

 	
  2. Show that if they take the time to read the code, they can probably understand what it's doing, at least at a high level


First, I provided them some context: _"The author wanted to analyze Trump's tweets: both the text, and some other information on the tweets like when and from what device they were posted."_ And I asked the students _"If you wanted to do this analysis, how would you go about collecting the data?"_. Some suggested manual data collection, which we all agreed is too tedious. A few suggested there should be a way to get the data from Twitter. So then we went back to the blog post, and worked our way through some of the code. (My narrative is roughly outlined in handwriting below.)

![](http://citizen-statistician.org/wp-content/uploads/2017/08/Screen-Shot-2017-08-31-at-00.07.49-1024x636.png)

The moral of the story: You don't need to figure out how to write a program that gets tweets from Twitter. Someone else has already done it, and packaged it up (in a package called **twitteR**), and made it available for you to use. Here, the important message I tried to convey was that _"No, I don't expect you to know that this package exists, or to figure out how to use it. But I hope you agree that once you know the package exists, it's worth the effort to figure out how to use its functionality to get the tweets, instead of collecting the data manually."_

Then, we discussed the following plot in detail:

![](http://citizen-statistician.org/wp-content/uploads/2017/08/Screen-Shot-2017-08-31-at-00.15.20-1001x1024.png)

First, I asked the students to come up with a list of variables we need in our dataset so that we can make this plot: we need to know what time each tweet was posted and what device it came from and we need to know how what percentage of tweets were posted in a given hour.

Here is the breakdown of the code (again, my narrative is in the handwritten comments):

![](http://citizen-statistician.org/wp-content/uploads/2017/08/Screen-Shot-2017-08-31-at-00.30.28-1024x627.png)

Once again, I wanted to show the students that if they take some time, they can probably figure out roughly what each line (ok, maybe not each, but most lines) of code are doing. We didn't get into discussing what's a _geom_, what's the difference between _%>%_ and _+_, what's an _aesthetic_, etc. We'll get into those, but the <del>night</del> semester is young...

My hope is that next time I present how to do something new in R, they'll remember this experience of being able to mostly figure out what's happening by taking some time staring at the code and thinking about _"if I had to do this by hand, how would I go about it?"_.
