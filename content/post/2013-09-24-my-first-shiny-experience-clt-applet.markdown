---
author: mine
comments: true
date: 2013-09-24 18:32:11+00:00
layout: post
link: http://citizen-statistician.org/2013/09/24/my-first-shiny-experience-clt-applet/
slug: my-first-shiny-experience-clt-applet
title: My first Shiny experience - CLT applet
wordpress_id: 688
---

When introducing the Central Limit Theorem for the first time in class, I used to use applets like the [SOCR Sampling Distribution Applet](http://www.socr.ucla.edu/applets.dir/samplingdistributionapplet.html) or the [OnlineStatBook Sampling Distribution Applet](http://onlinestatbook.com/stat_sim/sampling_dist/). If you are reading this post on Google Chrome, chances are those previous links did not work for you. If on another browser, they may have, but you may have also seen warnings like this one:

[![java_warning](http://citizen-statistician.org/wp-content/uploads/2013/09/java_warning-300x162.png)](http://citizen-statistician.org/wp-content/uploads/2013/09/java_warning.png)

Last year when I tried using one of these applets in class and had students pull it up on their own computers as well, it was a chaos. Between warnings like this and no simple way for everyone in their various computers and operating systems to update Java, most students got frustrated. As a class we had to give up playing with the applet, and the students just watched me go through the demonstrations on the screen.

In an effort to make things a little easier this year, I searched to see if I could find something similar created using Shiny. [This one](http://spark.rstudio.com/synchrony/climit/), created by [Tarik Gouhier](https://github.com/tgouhier), looked pretty promising. However it wasn't exactly what I was looking for. For example, it's pretty safe to assume that my students have never heard of the Cauchy distribution, and I didn't want to present something that might confuse them further.

Thanks to the [code being available on GitHub](https://github.com/tgouhier/climit), I was able to re-write the applet to match the functionality of the previous CLT applets: [http://rundel.dyndns.org:3838/CLT](http://rundel.dyndns.org:3838/CLT/).

[![clt_applet](http://citizen-statistician.org/wp-content/uploads/2013/09/clt_applet3-1024x669.png)](http://citizen-statistician.org/wp-content/uploads/2013/09/clt_applet3.png)

I'm sure I'll make some edits to the applet after I class-test it today. Among planned improvements are:



	
  * an intermediary step between the top (population distribution) and the bottom (sampling distribution) plots: the sample distribution.

	
  * sliders for input parameters (like mean and standard deviation) for the population distribution.


None of this is revolutionary, but it's great to be able to build on someone else's work so quickly. Plus, since all of the code is in R, which the students are learning anyway, those who are particularly motivated can dive deeper and can see the connection between the demonstration and what they're doing in lab.

If you use such demonstrations in your class and have suggestions for improvements, leave a comment below. If you'd like to customize the applet for your use, the code is linked on the applet page, and I'll be transitioning it to GitHub as I work on creating a few more of such applets.


##### (I should also thank [Colin Rundel](http://stat.duke.edu/~cr173/) who helped with the implementation and is temporarily hosting the applet on his server until I get my Shiny Server set up -- I filled out the registration form last night but I'm not yet sure what the next step is supposed to be.)
