---
author: mine
comments: true
date: 2016-08-13 02:47:42+00:00
layout: post
link: http://citizen-statistician.org/2016/08/13/a-timely-first-day-of-class-example-for-fall-2016-trump-tweets/
slug: a-timely-first-day-of-class-example-for-fall-2016-trump-tweets
title: 'A timely first day of class example for Fall 2016: Trump Tweets'
wordpress_id: 1083
categories:
- Data
- Musings
- Teaching
- teaching
---

On the first day of an intro stats or intro data science course I enjoy giving some accessible real data examples, instead of spending the whole time going over the syllabus (which is necessary in my opinion, but somewhat boring nonetheless).

[![silver-feature-most-common-women-names3](http://citizen-statistician.org/wp-content/uploads/2016/08/silver-feature-most-common-women-names3-249x300.png)](http://fivethirtyeight.com/features/how-to-tell-someones-age-when-all-you-know-is-her-name/)One of my favorite examples is [How to Tell Someone’s Age When All You Know Is Her Name](http://fivethirtyeight.com/features/how-to-tell-someones-age-when-all-you-know-is-her-name/) from [FiveThirtyEight](http://fivethirtyeight.com/). As an added bonus, you can use this example to get to know some students' names. I usually go through a few of the visualizations in this article, asking students to raise their hands if their name appears in the visualization. Sometimes I also supplement this with the [Baby Name Voyager](http://www.babynamewizard.com/voyager#prefix=&sw=both&exact=false), it's fun to have students offer up their names so we can take a look at how their popularity has changed over the years.

[![4671594023_b41c2ee662_m](http://citizen-statistician.org/wp-content/uploads/2016/08/4671594023_b41c2ee662_m.jpg)](https://www.flickr.com/photos/walkingsf/4671594023/in/album-72157624209158632/)

Another example I like is the [Locals and Tourists Flickr Photos](https://www.flickr.com/photos/walkingsf/albums/72157624209158632). If I remember correctly I saw this example first in [Mark Hanson](https://journalism.columbia.edu/faculty/mark-hansen)'s class in grad school. These maps use data from geotags on Flickr: blue pictures are taken by locals, red pictures are by tourists, and yellow pictures might be by either. [This one](https://www.flickr.com/photos/walkingsf/4671594023/in/album-72157624209158632/) of Manhattan is one most students will recognize, and since many people know where Times Square and Central Park are, both of which have an abundance of red - tourist - pictures. And if your students watch enough Law & Order they might also know where Rikers Island is they might recognize that, unsurprisingly, no pictures are posted from that location.

![make](http://citizen-statistician.org/wp-content/uploads/2016/08/make-150x150.png)However if I were teaching a class this coming Fall, I would add the following analysis of Donald Trump's tweets to my list of examples. If you have not yet seen this analysis by [David Robinson](http://varianceexplained.org/about/), I recommend you stop what you're doing now and go read it. It's linked below:


[Text analysis of Trump's tweets confirms he writes only the (angrier) Android half](http://varianceexplained.org/r/trump-tweets/)


I'm not going to re-iterate the post here, but the gist of it is that the [@realDonaldTrump](https://twitter.com/realDonaldTrump) account tweets from two different phones, and that


<blockquote>the Android and iPhone tweets are clearly from different people, posting during different times of day and using hashtags, links, and retweets in distinct ways. What’s more, we can see that the Android tweets are angrier and more negative, while the iPhone tweets tend to be benign announcements and pictures.

Source: [http://varianceexplained.org/r/trump-tweets/](http://varianceexplained.org/r/trump-tweets/)</blockquote>


I think this post would be a fantastic and timely first day of class example for a stats / data analysis / data science course. It shows a pretty easy to follow analysis complete with the R code to reproduce it. It uses some sentiment analysis techniques that may not be the focus of an intro course, but since the context will be familiar to students it shouldn't be too confusing for them. It also features techniques one will likely cover in an intro course, like confidence intervals.

As a bonus, many popular media outlets have covered the analysis in the last few days (e.g. see [here](http://www.latimes.com/nation/politics/trailguide/la-na-trailguide-updates-trump-tweets-iphone-android-1470868218-htmlstory.html), [here](http://mashable.com/2016/08/09/donald-trump-tweet-analysis/#ioaC1jIf1aqw), and [here](https://www.theguardian.com/media/2016/aug/10/donald-trump-twitter-republican-candidate-android-iphone)), and some of those articles might be even easier on the students to begin with before delving into the analysis in the blog post. Personally, I would start by playing [this clip](http://www.ctvnews.ca/video?clipId=930154) from the CTV News Channel featuring an interview with David to provide the context first (a video always helps wake students up), and then move on to discussing some of the visualizations from the blog post.
