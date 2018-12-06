---
author: citizenstat
comments: true
date: 2013-01-24 16:34:53+00:00
layout: post
link: http://citizen-statistician.org/2013/01/24/a-walk-in-venice-beach/
slug: a-walk-in-venice-beach
title: A walk in Venice Beach
wordpress_id: 363
categories:
- Data
- hunting and gathering
- Musings
- personal
- Teaching
---

For various reasons, I decided to walk this weekend from my house to Venice Beach, a distance of about four and a half miles.  The weather was beautiful, and I thought a walk would help clear my mind.  I had recently heard a story on NPR in which it was reported that Thoreau kept data on when certain flowers opened, a record now used to help understand the effects of global warming.  Some of these flowers were as far as 5 miles from Thoreau's home.  Which made me think, that if he could walk 5 miles to collect data, so could I.  Inspired also, perhaps, by the [UCLA Mobilize ](http://www.exploringcs.org/about/related-grants/mobilize)project, I made a decision to take a photo every 5 minutes.  The rule was simple: I would set my phone's timer for 5 minutes. When it rang, no matter where I was, I would snap a picture.

I decided I would take just one picture, so that I would be forced to exercise some editorial decision making. That way, the data would reflect my own state of mind, in some sense.  Later in the walk, I cheated, because it's easier to take many pictures than to decide on one.  I also sometimes cheated by taking pictures of things when it wasn't the right time.  Here's the last picture I decided to take, at the end of my walk (I took a cab home. I am that lazy) on Abbot Kinney.

[caption id="attachment_364" align="alignnone" width="224"][![mural.](http://citizen-statistician.org/wp-content/uploads/2013/01/IMG_1376-224x300.jpg)](http://citizen-statistician.org/2013/01/24/a-walk-in-venice-beach/img_1376/) Brick mural, on Abbot Kinney[/caption]

This exercise brought up a dilemma I often encounter when touristing--do you take intimate, close-up pictures of interesting features, like the above, or do you take pictures of the environment, to give people an idea of the surroundings?  This latter is almost always a bad idea, particularly if all you've got is an iPhone 4; it really is difficult to improve on Google Street View.  It is, however, extremely tempting, despite the fact that it leads to pictures like this:

[caption id="attachment_373" align="alignnone" width="300"][![Lincoln Blvd (Pacific Coast Hwy) and Venice Blvd, looking North](http://citizen-statistician.org/wp-content/uploads/2013/01/IMG_1355-300x224.jpg)](http://citizen-statistician.org/2013/01/24/a-walk-in-venice-beach/img_1355/) Lincoln Blvd (Pacific Coast Hwy) and Venice Blvd, looking North[/caption]

But my subject-matter choices were also limited in other ways.  For one, it was fairly hot, as this temperature plot ([http://www.friendlyforecast.com/usa/archive](http://www.friendlyforecast.com/usa/archive)) shows.

[![temp plot](http://citizen-statistician.org/wp-content/uploads/2013/01/temp-plot-231x300.jpg)](http://citizen-statistician.org/2013/01/24/a-walk-in-venice-beach/temp-plot-2/)

The heat kept me on the shady side of the street, and the sun meant that I usually had to shoot across the street, although there were some exceptions:

[![IMG_1345](http://citizen-statistician.org/wp-content/uploads/2013/01/IMG_1345-300x224.jpg)](http://citizen-statistician.org/2013/01/24/a-walk-in-venice-beach/img_1345/)(The object on the left is what we once called a "pay phone". The only public phone I encountered that day, in fact, which added to the mystery of this storefront which had a colorful mural, but no name or address marker.)

During the walk I stopped at a farmer's market and at a used book sale at the Mar Vista Library (bought an Everyman's Library book about Beethoven and the score to Bach's Cantata #4.) I watched toddler-aged girls fight and cry and dance outside a ballet studio, drank a too-expensive cup of coffee at Intelligentia coffee (but it was good), and bought my sister, for her birthday,  a terrarium at a make-your-own terrarium shop.

[caption id="attachment_374" align="alignnone" width="150"][![Books.](http://citizen-statistician.org/wp-content/uploads/2013/01/IMG_1342-150x150.jpg)](http://citizen-statistician.org/2013/01/24/a-walk-in-venice-beach/img_1342/) Books.[/caption]

What to do with these data?  One challenge is to see what can be gleaned  from the photos.  The only trend that jumped out at me, while reviewing these, was the fact that I was in line at that coffee shop for a very long time, as this series of photos (taken every 5 minutes, remember), attest:

[![IMG_1369](http://citizen-statistician.org/wp-content/uploads/2013/01/IMG_1369-300x224.jpg)](http://citizen-statistician.org/2013/01/24/a-walk-in-venice-beach/img_1369/)

[caption id="attachment_369" align="alignnone" width="300"][![Closer](http://citizen-statistician.org/wp-content/uploads/2013/01/IMG_1371-300x224.jpg)](http://citizen-statistician.org/2013/01/24/a-walk-in-venice-beach/img_1371/) Closer[/caption]

[caption id="attachment_371" align="alignnone" width="300"][![waiting for the hand-pour-briewed coffee to actually be poured](http://citizen-statistician.org/wp-content/uploads/2013/01/IMG_13731-300x224.jpg)](http://citizen-statistician.org/2013/01/24/a-walk-in-venice-beach/img_1373-2/) waiting for the hand-pour-briewed coffee to actually be poured[/caption]

So at the risk of overthinking this post, I'll just come right to the point (finally):  how do we provide tools to make it easier for people to make sense of these data?

Rather than organize my partial answer in a thoughtful way, and thus spend weeks writing it down, let me just make a list.  I will organize the list, however, by sub-category.

**Gathering the Data**



	
  * The iPhone, of course, stores date and time stamps, as well as location stamps, whenever I snapped a photo.  And lots of other data, called exif data.  I can look at some of these using Preview or iPhoto,  but trying to extract the data for my own use is hard.  Does anyone know a way of getting a datafile that has the time, date, GPS coordinates for my pictures?  (And any other photo meta-data, for that matter.)  I browsed through a discussion on [stackoverflow](http://stackoverflow.com/questions/616346/iphone-access-location-information-from-a-photo), and for me the take-home message was "no." I did find a way to _view_ the data; first, load the iPhone photos into iPhoto. Then export to hard drive, being sure to check the 'include location information' box. Then, open with Preview, open the Inspector (command-i or choose from drop-down menu), and then click on the GPS tab.  From there it is a simple matter of typing everything in, photo by photo, into another file.

	
  * Weather data is easily found to supplement the story, as the above graph shows.

	
  * [OpenPaths](https://openpaths.cc) provides free location data, and even stores if for you.  It allows you to export nice csv files, such as this [file](https://www.dropbox.com/s/kl4ec7fg9o8fz8e/openpathsvenicewalk.csv)


**Displaying the Data**



	
  *  Well, you can always paste photos and graphs into along, rambling narrative.

	
  * iPhoto is apparently one of the few softwares that does have access to your exif data, and the "Places" feature will, with some playing around, let you show where you've been. It's tedious, and you can't easily share the results (maybe not at all).  But it does let you click on a location pin and see the picture taken there, which is fun.

	
  * StatCrunch has a new feature that lets you easily communicate with google maps. You provide latitude, longitude and optional other data, and it makes a map.  some funny formatting requirements:  data must be in this form  lat lon|color|other_variable
Hopefully, [StatCrunch](http://www.statcrunch.com) will add a feature that let's you easily move from the usual flat-file format for data to this format.  In the meantime, I had to export my StatCrunch OpenPaths data to excel, (could have used R, but I'm rusty with the string commands), and then re-import as a new data set.

	
  * [![Venice Walk Open Paths map on StatCrunch-1](http://citizen-statistician.org/wp-content/uploads/2013/01/Venice-Walk-Open-Paths-map-on-StatCrunch-1-150x150.jpg)](http://citizen-statistician.org/2013/01/24/a-walk-in-venice-beach/venice-walk-open-paths-map-on-statcrunch-1/)


**Making Sense of It All**

But the true challenge is how do we make sense of it all?  How do we merge these data in such a way that unexpected patterns that reveal deeper truths can be revealed? At the very least, is there a single, comprehensive data display that would allow you to more fully appreciate my experience?  If (and when) I do this walk again, how can I compare the data from the two different walks?

Some other themes:  our data should be ours to do with as we please. OpenPaths has it right; iPhone has it wrong wrong wrong.  Another theme: maps are now a natural and familiar way of storing and displaying data.  StatCrunch has taken some steps in the right direction in attempting to provide a smooth pathway between data and map, but more is needed.  Perhaps there's a friendly, flexible, open-source mapping tool out there somewhere that would encourage our data-concious citizens to share their lives through maps?

If you're still reading, you can view all of the pictures on [flikr](http://flic.kr/s/aHsjDFcekH).
