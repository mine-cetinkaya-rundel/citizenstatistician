---
author: andy
comments: true
date: 2013-03-01 14:46:39+00:00
layout: post
link: http://citizen-statistician.org/2013/03/01/dear-gmail/
slug: dear-gmail
title: Dear Gmail...
wordpress_id: 442
categories:
- Musings
---

I recently added a free application/service that analyzes my email called [Gmail Meter](http://www.gmailmeter.com). This service sends me a comprehensive weekly report full of summaries and plots that indicate how I use Gmail.




The first thing I learned is that Wednesdays are for emailing and I seem to respond in a timely manner, on average, to emails sent to me...when I actually respond (I have a 24.58% response rate. Yikes!) Wednesdays I only teach one class (at 4:40pm) this semester, but I have a morning meeting so I am on campus and generally have time to respond to emails that I may not have gotten to.


[![Summary of my Gmail](http://citizen-statistician.org/wp-content/uploads/2013/03/chart-0-300x226.png)](http://citizen-statistician.org/wp-content/uploads/2013/03/chart-0.png)


The plot of my daily email traffic shows that most email is sent to me during the day (typical work hours), while my email times tend to be prior to classes in the morning and after my evening courses. Also, it is clear I am sending far less that I receive. It appears I am doing my part to lower my email footprint!
![chart](http://citizen-statistician.org/wp-content/uploads/2013/03/chart-300x184.png)I seem to be more prompt on my email responses (for the most part) than others who respond to me. What is interesting, is that people who respond to me are in primarily very quick (<4hrs) or take more than a day to get back to me. This fits with the behavior I expect from most academics. ![chart-2](http://citizen-statistician.org/wp-content/uploads/2013/03/chart-2-300x184.png)In the emails I send, I tend to be terse. Generally, I try to avoid long emails to people since when long emails are sent to me I tend to get cranky. (I recognize that sometimes it can't be avoided.) I actually am quite pleased that the mode here is less than 10 words. (Again, yay for my footprint!)




I am not quite as happy to see that the mode for emails sent to me is the category indicating more than 200 words. Some of this is because of the university committees  I sit on. For example, the University of Minnesota Senate sends many emails. These emails often are lengthy because of the inclusion of bylaws and articles to the University Constitution that we will be voting on. That being said, I agree with [this email charter](http://emailcharter.org) which begs us all to keep it short.![chart-3](http://citizen-statistician.org/wp-content/uploads/2013/03/chart-3-300x184.png)What kind of media attachments are taking up space in my Gmail box? It seems that most are Microsoft Word documents. Again, given my collaboration with other academics and feedback to students this makes sense to me. Since I have a Mac and most of my colleagues still work on PC, I send many documents as PDF files. My guess is that if this were sent to me a few years ago, the number of attachments would have been even higher. Our research group has slowly worked toward using sites like Dropbox to share documents. (Next stop...some versioning system.)![chart-4](http://citizen-statistician.org/wp-content/uploads/2013/03/chart-4-300x184.png)Now for the plot that made me stop and write this post. Almost 90% of the email I received this week hit the trash can. Also a small percentage is still in my inbox. I am trying to achieve [Inbox Zero](http://inboxzero.com), but just haven't made it yet. I am currently down to xxx emails in my inbox. I signed up for the [Mailbox app](http://www.mailboxapp.com) which should help with this goal when I check email on my phone, but like the [Tempo app](http://tempo.ai) that Rob signed up for, there is a reservation system in place. Unlike Rob, my spot in the Mailbox line is nowhere near the bottom (last I looked 632,889 people in front of me) despite having reserved my place in line several weeks ago.[![chart-1](http://citizen-statistician.org/wp-content/uploads/2013/03/chart-1-300x184.png)](http://citizen-statistician.org/wp-content/uploads/2013/03/chart-1.png)I also receive information on the week's top emailers to me (Joan) and the top recipients of my mail (one of my students); top conversation threads, a scatterplot of the number of words per email in a thread versus the rank of the email in the thread (was it the 1st email sent, 2nd, etc.). As one might expect there is a strong, negative relationship here. It also produces a word cloud based on the subjects and bodies of all messages sent or received directly. Lastly, it conditions emails received with attachments on whether they came from inside or outside the organization (University of Minnesota).




It is not clear that you can obtain the raw data, although it is not clear that you can't either. There are of course ways to obtain the meta-data that Gmail Meter is using by scraping it using a program such as Python ([see here](http://books.gigatux.nl/mirror/googlehacks/0596008570/googlehks2-CHP-6-SECT-13.html)). My guess is that you could also do this with R 9perhaps using the curl and XML packages). They have several feature requests for making Google Meter more customizable which would make it even cooler.
