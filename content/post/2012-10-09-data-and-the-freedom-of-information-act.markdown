---
author: andy
comments: true
date: 2012-10-09 02:16:05+00:00
layout: post
link: http://citizen-statistician.org/2012/10/09/data-and-the-freedom-of-information-act/
slug: data-and-the-freedom-of-information-act
title: Data and the Freedom of Information Act
wordpress_id: 120
categories:
- Data
- Musings
---

In reading one of the many blogs that I read, there was a suggestion to use the [Baltimore's parking citation data](https://data.baltimorecity.gov/Financial/Parking-Citations/n4ma-fj3m) to see if some makes/models of cars get citations more than others. Now parking citations are very near and dear to me since I get at least one (n ≥ 1) parking citation a year parking near the University of Minnesota–which most often also leads to my car being towed since you only have so many hours to move your car after they ticket it.

After seeing the data from Baltimore I thought wonderful...I can do some analyses on the Minneapolis parking citation data and empirically examine some hypotheses. For example, are cars parked near the university campus ticketed and/or towed with greater disparity than in other neighborhoods in Minneapolis? [Are the number of parking citations in Minneapolis really down from previous years (especially in locations where the have installed "smart" meters)?](http://kstp.com/news/stories/S2724188.shtml?cat=1) Or even whether particular types of cars are cited more often than others.

One problem. Minneapolis does not make their data as openly accessible as Baltimore. My initial thought was "no worries". The Freedom of Information Act and the Minnesota Government Data Practices Act (Minnesota Statutes, Chapter 13) make it clear that all government data is public unless a state or federal laws says the data is not public. Furthermore, according to the [Hennepin County Requests for Data by Members of the Public](http://hennepin.us/portal/site/HennepinUS/menuitem.b1ab75471750e40fa01dfb47ccf06498/?vgnextoid=9b22712db6733310VgnVCM10000099fe4689RCRD) webpage, these laws "stipulate that Hennepin County must keep all government data in a way that makes it easy for you, as a member of the public, to access."

My quest to obtain the parking citation data for Hennepin County (the county Minneapolis resides in) began at roughly 7:00 a.m. when I went to the [Minneapolis Police Department](http://www.minneapolismn.gov/police/records/police_records_traffic_violations) webpage to find out how to obtain this data. After following the link to "traffic violations" I was redirected to the [Hennepin County Traffic Violations Bureau](http://www.mncourts.gov/district/4/?page=424), which is actually the Fourth District of the Minnesota Judicial Branch's website. (This will matter later in the story). After making sure that I hadn't been accidentally transported to the internet of 1997 (the page had echoes of the old Yahoo), I emailed the contact person under data requests.

At this point it was 7:30 a.m. and I thought great, I will be answering all my questions with ggplot2 by noon! After some back and forth with the contact person (I had to more specifically state what I wanted and make sure that they understood I wanted the raw data not summary reports, them making sure that Excel was an ok format for me) I received the following email:


<blockquote>The fee for running the data request is $60.  If you approve, the next step is to prepay by check.  District Court is unable to process cash or credit card payments for data requests.

</blockquote>


Sixty dollars!!?? Are you kidding me? After my initial shock, I sent a bevy of emails back and forth with the contact person quoting both the Minnesota and Federal laws that they had printed on their website. The response was:


<blockquote>District Court is subject to the Rules of Public Access to the Records of the Judicial Branch [http://www.mncourts.gov/?page=511#publicAccess](http://www.mncourts.gov/?page=511#publicAccess). The Rules do not require raw data to be accessible through the internet. The data you are interested in must be extracted from the database to put is a readable Excel file, thus the prorated fee of $60 (rate is $80/hour).</blockquote>


To which I asked why it would cost me $60 for someone to query a database and output the results into an Excel spreadsheet (I am in the wrong profession!). When I formally withdrew my request at 2:03 p.m., I also politely mentioned that I would be blogging about this adventure. I was asked to call a phone number and talk with them before I blogged about it.

I called and we actually had a pretty good talk. Here is where things are a bit fuzzy and the difference between Hennepin County and the Fourth District Court come into play. I was told that these two entities have completely separate rules regarding the accessibility of data. (_Note to the reader: This is true, but as far as I can tell by the document linked in the second email, these rules would not apply to parking citation data._) Also, because they are not on the same budget different requests for data cost the public money. (_Another note to the reader: This is where I was told that since there were multiple queries to run–at least 21 different rules and regulations governing parking in Minneapolis–it would cost a lot of money because they had to go through quite a menu-structure for each query._)

I have the name of a contact who may or may not be able to help me obtain this data, and I will keep you posted. But all of this is to point out that "publicly accessible" data not only varies in its accessibility, but also in its being "public". In Hennepin County, you still need to be somewhat affluent to obtain these data.

I applaud the cities that have begun and carried through with [open data initiatives](http://www.whitehouse.gov/innovationfellows/opendata). Unfortunately, the [United Kingdom](http://data.gov.uk) is way ahead of the United States when it comes to open data. Here are some examples of cities that have embraced open data.



	
  * Montreal has made[ GPS data of it transportation data](http://w5.montreal.com/mtlweblog/?p=18500) freely accessible.

	
  * [Baltimore](https://data.baltimorecity.gov)

	
  * [New York City](https://nycopendata.socrata.com) had a grassroots movement that opened up much of its data . They have some of the most [progressive legislation](http://www.nyc.gov/portal/site/nycgov/menuitem.c0935b9a57bb4ef3daf2f1c701c789a0/index.jsp?pageID=mayor_press_release&catID=1194&doc_name=http%3A%2F%2Fwww.nyc.gov%2Fhtml%2Fom%2Fhtml%2F2012a%2Fpr081-12.html&cc=unused1978&rc=1194&ndi=1) on open data and are working on [open data technical standards](http://nycopendata.pediacities.com/wiki/index.php/NYC_Open_Data).

	
  * [Chicago](https://data.cityofchicago.org)

	
  * [Los Angeles](http://egis3.lacounty.gov/eGIS/tag/open-data/) (GIS data)


I am sure there are many more cities that have opened up their data in manners that are truly "open". If people have good suggestions about how we as a statistics community can be more instrumental in helping city and county governments embrace these initiatives, post in the comments. I would love to hear from you.


