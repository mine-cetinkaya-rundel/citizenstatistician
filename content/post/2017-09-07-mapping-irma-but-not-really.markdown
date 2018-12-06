---
author: mine
comments: true
date: 2017-09-07 19:00:10+00:00
layout: post
link: http://citizen-statistician.org/2017/09/07/mapping-irma-but-not-really/
slug: mapping-irma-but-not-really
title: Mapping Irma,  but not really...
wordpress_id: 1217
categories:
- Data
- Teaching
- teaching
- Visualization
---

We're discussing data visualization nowadays in [my course](http://www2.stat.duke.edu/courses/Fall17/sta112.01/), and today's topic was supposed to be mapping. However late last night I realized I was going to run out of time and decided to table hands on mapping exercises till a bit later in the course (after we do some data manipulation as well, which I think will work better).

That being said, talking about maps seemed timely, especially with Hurricane Irma developing. Here is how we went about it:[![](http://citizen-statistician.org/wp-content/uploads/2017/09/irma-slide-1024x817.png)](https://www.nytimes.com/interactive/2017/09/05/us/hurricane-irma-map.html?smid=pl-share)

In addition to what's on the slide I told the students that they can assume the map is given, and they should only think about how the forecast lines would be drawn.

Everyone came up with "we need latitude and longitude and time". However some teams suggested each column would represent one of the trajectories (wide data), while others came up with the idea of having an indicator column for the trajectory (long data). We sketched out on the board what these two data frames would look like, and evaluated which would be easier to directly plot using tools we've learned so far (plotting in R with ggplot2).

While this was a somewhat superficial activity compared to a hands on mapping exercise, I thought it worked well for a variety of reasons:



 	
  1. It was a timely example that grabbed students' attention.

 	
  2. It generated lively discussion around various ways of organizing data into data frames (which hopefully will serve as a good primer for the data manipulation unit where we'll discuss how data don't always come in the format you need and you might need to get it in shape first before you can visualize/analyze it).

 	
  3. Working backwards from a visualization to source data (as opposed to from data to visualization) provided a different challenge/perspective, and a welcome break from "how do I get R to plot this?".

 	
  4. We got to talk about the fact that predictions based on the same source data can vary depending on the forecasting model (foreshadowing of concepts we will discuss in the modeling unit coming up later in the course).

 	
  5. It was quick to prepare! And quick to work through in class (~5 mins of team discussion + ~10 mins of class discussion).


I also suggested to students that they read the [underlying NYTimes article](https://nyti.ms/2x7nKLD) as well as [this Upshot article](https://nyti.ms/2xPWa2z) if they're interested in finding out more about modeling the path of a hurricane (or modeling anything, really) and uncertainty.
