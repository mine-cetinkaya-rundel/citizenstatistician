---
author: andy
comments: true
date: 2012-12-13 16:58:05+00:00
layout: post
link: http://citizen-statistician.org/2012/12/13/turning-tables-into-graphs/
slug: turning-tables-into-graphs
title: Turning Tables into Graphs
wordpress_id: 301
categories:
- Computing
- Teaching
---

We have just finished another semester, and before my mind completely turns to rubble, I want to share what I believe to be a fairly good assignment. What I present below was parts of two separate assignments that I gave this semester, but upon reflection I think it would be better as one.




-----

Read the article _Let’s Practice What We Preach: Turning Tables into Graphs_ (full reference given below). In this article, Gelman, Pascarica, & Dodhia suggest that presentations of results using graphs are more effective than results presented in tables.

Gelman, A., Pasarica, C., & Dodhia, R. (2002). Let’s practice what we preach: Turning tables into graphs. The American Statistician, 56(2), 121–130.

Find an article in a journal that presents results (or data) in a table. Re-create the data in a tabular format using R (or Excel).



	
  1. Use the functions in ggplot2 to produce a plot that conveys the same message as the original table.

	
  2.  Include the original table (this can be a screenshot or web-link) and citation, along with your plot.

	
  3. Write a few sentences describing why the plot you produced provides a better presentation of the results or data (be sure to use recommendations from the article in making your case).


In the second part of this assignment, you will write a tutorial for the process you followed for turning a table into a plot using _R Markdown_ and will publish that tutorial on _RPubs_.

There are several resources for learning R Markdown.



	
  * RStudio's [[documentation](http://www.rstudio.com/ide/docs/authoring/using_markdown)] for writing a document with R Markdown

	
  * Yihue's [[screencast](http://www.screenr.com/qcv8)] introducing R Markdown

	
  * An [[example/tutorial](https://onlinecourses.science.psu.edu/stat497r/sites/onlinecourses.science.psu.edu.stat497r/files/knitr-markdown%20demo.html)] from PSU


Your tutorial should be written so that a student who was just learning ggplot could follow your directions easily. Include instructions for obtaining the data, getting it into a useable tabular format, manipulating the data so it can be used with ggplot, and well-commented instructions for creating your final plot. (Think of the level of detail you would want in a tutorial when you were first learning ggplot!)

It should also include:

	
  * a citation or link to the website/journal that published the original table

	
  * a view of your final data (full or a subset depending on size)

	
  * all commands necessary to create your final plot (with appropriate explanation), and

	
  * the final plot


When you knit the .Rmd document it should compile without errors.

-----

Students commented that they learned a lot about the use of ggplot during the initial assignment (this was the second assignment in the course). The Markdown part of the assignment I gave as an extra credit assignment at the end of the class, but in retrospect, I should have made it required and done it very early on.

Here are a couple of the tutorials that I have received so far:

	
  * These students took a table of characteristics of survey participants published in the _Journal of Ethnic and Cultural Diversity in Social Work_ and turned it into a bar graph.  [http://rpubs.com/TSK_2012/3184](http://rpubs.com/TSK_2012/3184)

	
  * These students took data about trends and topics discussed in _Seventeen Magazine_'s Traumarama articles from 1994-2007 and turned it into a line plot. [http://rpubs.com/opalc123/3155](http://rpubs.com/opalc123/3155)

	
  * These students took a table of data related to approval ratings and turned them into a box-and-whiskers plot. [http://www.rpubs.com/GeorgeBrisse/3217](http://www.rpubs.com/GeorgeBrisse/3217)

	
  * These students' work depict a great example of how data initially presented in a table is much easier to process in a graph. The data, from a table published in the _Journal of Deaf Studies and Deaf Education_, show the academic status and progress of deaf and hard-of-hearing students in general education classrooms.  [http://rpubs.com/mens0055/3211](http://rpubs.com/mens0055/3211)

	
  * These students used a stacked bar chart to show data about the sample sizes for different stages for 12 problem behaviors published in _Health Psychology_. [http://rpubs.com/nikedenise/3256](http://rpubs.com/nikedenise/3256)

	
  * These students created a line graph representing pre- and post-training scores for consonant, vowel, sentence, and gender perception scores in cochlear implant users to examine whether an auditory training program improves performance. [http://rpubs.com/koern030/3255](http://rpubs.com/koern030/3255)



