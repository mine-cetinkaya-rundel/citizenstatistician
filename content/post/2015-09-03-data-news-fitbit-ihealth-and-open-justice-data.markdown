---
author: citizenstat
comments: true
date: 2015-09-03 17:48:23+00:00
layout: post
link: http://citizen-statistician.org/2015/09/03/data-news-fitbit-ihealth-and-open-justice-data/
slug: data-news-fitbit-ihealth-and-open-justice-data
title: 'Data News: Fitbit + iHealth, and Open Justice data'
wordpress_id: 947
categories:
- Data
- hunting and gathering
- personal
- pret-a-porter
- Teaching
- teaching
---

The [LA Times reported today](http://www.latimes.com/local/crime/la-me-police-transparency-20150903-story.html), along with several other sources, that the California Department of Justice has initiated a new "open justice" data initiative.  On their portal, the "[Justice Dashboard](http://openjustice.doj.ca.gov/index.html)", you can view Arrest Rates, Deaths in Custody, or Law Enforcement Officers Killed or Assaulted.

I chose, for my first visit, to look at Deaths in Custody.  At first, I was disappointed with the quality of the data provided.  Instead of data, you see some nice graphical displays, mostly univariate but a few with two variables, addressing issues and questions that are probably on many people's minds.  (Alarmingly, the second most common cause of death for people in custody is homicide by a law enforcement officer.)

However, if you scroll to the bottom, you'll see that you can, in fact, download relatively raw data, in the form of a spreadsheet in which each row is a person in custody who died.  Variables include date of birth and death, gender, race, custody status, offense, reporting agency, and many other variables.  Altogether, there are 38 variables and over 15000 observations. The data set comes with a nice codebook, too.

**FitBit vs. the iPhone**

Onto a cheerier topic. This quarter I will be teaching regression, and once again my FitBit provided inspiration.  If you teach regression, you know one of the awful secrets of statistics: there are no linear associations. Well, they are few and far between.  And so I was pleased when a potentially linear association sprang to mind:  how well do FitBit step counts predict the Health app counts?

Health app is an ios8 app. It was automatically installed on your iPhone, whether you wanted it or not.  (I speak from the perspective of an iPhone 6 user, with ios8 installed.) Apparently, whether you know it or not, your steps are being counted.  If you have an Apple Watch, you know about this.  But if you don't, it happens invisibly, until you open the app. Or buy the watch.

How can you access these data?  I did so by downloading the [free app QS](https://itunes.apple.com/us/app/qs-access/id920297614?mt=8) (for "Quantified Self"). The Quantified Self people have a [quantified self website](http://quantifiedself.com/guide/tools) directing you to hundreds of apps you can use to learn more about yourself than you probably should.  Once installed, you simply open the app, choose which variables you wish to download, click 'submit', and a csv filed is emailed to you (or whomever you wish).

The FitBit data can only be downloaded if you have a premium account.  The FitBit premium website has a 'custom option' that allows you to download data for any time period you choose, but currently, due to an acknowledged bug, no matter which dates you select, only one month of data will be downloaded. Thus, you must download month by month.  I downloaded only two months, July and August, and at some point in August my FitBit went through the wash cycle, and then I misplaced it.  It's around here, somewhere, I know. I just don't know where.  For these reasons, the data are somewhat sparse.

I won't bore you with details, but by applying functions from the lubridate package in R and using the gsub function to remove commas (because FitBit inexplicably inserts commas into its numbers and, I almost forgot, adds a superfluous title to the document which requires that you use the "skip =1" option in read.table), it was easy to merge a couple of months of FitBit with Health data.  And so here's how they compare:

[![fitbitsteps](http://citizen-statistician.org/wp-content/uploads/2015/09/fitbitsteps-300x273.png)](http://citizen-statistician.org/wp-content/uploads/2015/09/fitbitsteps.png)

The regression line is Predicted.iOS.Steps = 1192 + 0.9553 (FitBit.Steps), r-squared is .9223.  (A residual plot shows that the relationship is not quite as linear as it looks. Damn.)

Questions I'm thinking of posing on the first day of my regression class this quarter:



	
  1. Which do you think is a more reliable counter of steps?

	
  2. How closely in agreement are these two step-counting tools? How would you measure this?

	
  3. What do the slope and intercept tell us?

	
  4. Why is there more variability for low fit-bit step counts than for high?

	
  5. I often lose my FitBit. Currently, for instance, I have no idea where it is.  On those days, FitBit reports "0 steps". (I removed the 0's from this analysis.)  Can I use this regression line to predict the values on days I lose my FitBit?  With how much precision?


I think it will be helpful to talk about these questions informally, on the first day, before they have learned more formal methods for tackling these.  And maybe I'll add a few more months of data.
