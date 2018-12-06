---
author: citizenstat
comments: true
date: 2012-12-13 04:57:18+00:00
layout: post
link: http://citizen-statistician.org/2012/12/13/data-privacy-for-kids/
slug: data-privacy-for-kids
title: Data Privacy for Kids
wordpress_id: 288
categories:
- Data
- personal
- privacy
---

The L.A. Times ran an [interesting article](http://soc.li/oIQvrlE) about the new [Federal Trade Commission](http://www.ftc.gov/os/2012/12/121210mobilekidsappreport.pdf)(downloads) report, "Mobile Apps for Kids: Disclosures Still Not Making the Grade",  followed up on a February 2012 report, and concluded that "Yes, many apps included interactive features or shared kids’ information with third parties without disclosing these practices to parents."

I think this is issue is intriguing on many levels, but of central concern is the fact that as we go about our daily business (or play, as the case may be), we leave a data trail, sometimes unwittingly.   Quite often unknowingly. Perhaps we've reached the point where there's no going back, and we must accept the fact that when we engage with the mobile community, we engage in a data-exchange.  But it seems  an easy thing that standards should be set so that, maybe, developers are required to produce logs of the data transaction.  And third-party developers could write apps that let parents examine this exchange. (Without, of course, sharing this information with a third party.)  It would be interesting and fun, I would think, to create a visualization of the data flow in and out of your device across a period of time.

The report indicated that the most commonly shared datum was the device ID number.  Sounds innocent, but, as we all know, its the crosstabs that kill.  The device ID is a unique number, and is associated with other variables, such as the device operating system, primary language, the carrier, and other information.  It can also be used to access personal data, such as the name, address, email address, of the user.  While some apps share only the device ID, and thus may seem safe, other apps send more data to the same companies.  And so companies that receive data from multiple apps can build up a more detailed picture of the user.  And these companies share data with each other, and so can create even richer pictures.

There are some simple ways of introducing the topic into a stats course.  The report essentially conducted a random sample (well, lets say it had some random sampling components) of apps.  And reports estimated percentages. But never, of course, confidence intervals.  And so you can ask your students a question such as "The FTC randomly sampled 400 apps that were marketed to "kids" from the Google and iTunes app store.  60% of the apps in the sample transmitted the Device ID to a third-party.  Find a 95% confidence interval for the proportion of all apps...."  Or, "only 20% of the apps that transmitted private information to a third-party disclosed this fact to the user.  Find a 95% CI...."

The report contains some nice comparisons with the 2011 data concerning the types of "kids" apps available, as well as a discussion of the type of advertising that appears.  (An amusing example that shouldn't be amusing, is an app targeted at kids that displays advertising for a dating web site: "1000+ singles!".  Reminds me of something my sister told me when her kids were young:  she could always tell when they found something troubling on the computer because suddenly they would grow very quiet.
