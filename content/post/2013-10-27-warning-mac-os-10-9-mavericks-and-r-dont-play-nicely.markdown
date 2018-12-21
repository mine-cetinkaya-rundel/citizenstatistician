---
author: andy
comments: true
date: 2013-10-27 20:46:50+00:00
layout: post
link: http://citizen-statistician.org/2013/10/27/warning-mac-os-10-9-mavericks-and-r-dont-play-nicely/
slug: warning-mac-os-10-9-mavericks-and-r-dont-play-nicely
title: 'Warning: Mac OS 10.9 Mavericks and R Don''t Play Nicely'
wordpress_id: 714
categories:
- rstats
- Teaching
---

For some reason I was compelled to update my Mac's OS and R on the same day. (I know...) It didn't go well on several accounts and I mostly blame Apple. Here are the details.



	
  * I updated R to version 3.0.2 "Frisbee Sailing"

	
  * I updated my OS to 10.9 "Mavericks"


When I went to use R things were going fine until I mistyped a command. Rather than giving some sort of syntax error, R responded with,

    
    > *** caught segfault *** 
    > address 0x7c0, cause 'memory not mapped' 
    > 
    > Possible actions: 
    > 1: abort (with core dump, if enabled) 
    > 2: normal R exit 
    > 3: exit R without saving workspace 
    > 4: exit R saving workspace 
    > Selection:


Unlike most of my experiences with computing, this I was able to replicate many times. After a day of panic and no luck on Google, I was finally able to find a [post on one of the Google Groups from Simon Urbanek](https://groups.google.com/forum/#!topic/r-sig-mac/qKwxj2DaRgc) responding to someone with a similar problem. He points out that there are a couple of solutions, one of which is to wait until Apple gets things stabilized. (This is an issue since if you have ever tried to go back to a previous OS on a Mac, you will know that this might take several days of pain and swearing.)

The second solution he suggests is to install the nightly build or rebuild the GUI. To install the nightly build visit the [R  for Mac OS X Developer's page](http://r.research.att.com/#nightly). Or, in Terminal issue the following commands,

    
    svn co https://svn.r-project.org/R-packages/trunk/Mac-GUI 
    cd Mac-GUI 
    xcodebuild -configuration Debug 
    open build/Debug/R.app


I tried both and this worked fine...until I needed to load a package. Then I was given an error that the package couldn't be found. Now I realize that you can download the packages you need from source and compile them yourself, but I was trying to figure out how to deal with students who were in a similar situation. (This is not an option for most social science students.)

The best solution it turned out is to use [RStudio](http://www.rstudio.com), which my students pretty much all use anyway. (My problem is that I am a Sublime Text 2 user.) This allowed the newest version of R to run on the new Mac OS. But, as is pointed out on the [RStudio blog](http://blog.rstudio.org/2013/10/22/rstudio-and-os-x-10-9-mavericks/),


<blockquote>As a result of a problem between Mavericks and the user interface toolkit underlying RStudio (Qt) the RStudio IDE is very slow in painting and user interactions  when running under Mavericks.</blockquote>


I re-downloaded the latest stable release of the R GUI about an hour ago, and so far it seems to be working fine with Mavericks (no abort message yet), so this whole post may be moot.
