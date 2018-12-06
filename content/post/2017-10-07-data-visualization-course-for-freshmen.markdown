---
author: andy
comments: true
date: 2017-10-07 15:26:51+00:00
layout: post
link: http://citizen-statistician.org/2017/10/07/data-visualization-course-for-freshmen/
slug: data-visualization-course-for-freshmen
title: Data Visualization Course for First-Year Students
wordpress_id: 1225
categories:
- Computation
- R Project
- Teaching
- Visualization
---

A little over a year ago, we decided to propose a data visualization course at the first-year level. We had been thinking about this for awhile, but never had the time to teach it given the scheduling constraints we had. When one of the other departments on campus was shut down and the faculty merged in with other departments, we felt that the time was ripe to make this proposal.

[caption id="attachment_1227" align="aligncenter" width="1518"][![](http://citizen-statistician.org/wp-content/uploads/2017/10/Screen-Shot-2017-10-07-at-10.24.51-AM.png)](http://citizen-statistician.org/2017/10/07/data-visualization-course-for-freshmen/screen-shot-2017-10-07-at-10-24-51-am/) Course description of the EPsy 1261 data visualization course[/caption]

In putting together the proposal, we knew that:



 	
  * The course would be primarily composed of social science students. My department, Educational Psychology, attracts students from the _College of Education and Human Development_ (e.g., Child Psychology, Social Work, Family Social Science).

 	
  * To attract students, it would be helpful if the course would fulfill the University's Liberal Education (LE) requirement for _Mathematical Thinking_.


This led to several challenges and long discussions about the curriculum for this course. For example:

 	
  * Should the class focus on **producing** data visualizations (very exciting for the students) or on **understanding/interpreting** existing visualizations (useful for most social science students)?

 	
  * If we were going to produce data visualizations, which software tool would we use? Could this level of student handle R?

 	
  * In order to meet the LE requirement, the curriculum for the course would need to show a rigorous treatment of students actually "doing" mathematics. How could we do this?

 	
  * Which types of visualizations would we include in the course?

 	
  * Would we use a textbook? How might this inform the content of the course?




# Software and Content


After several conversations among the teaching team, with stakeholder departments, and with colleagues teaching data visualization courses at other universities, we eventually proposed that the course:



 	
  * Focus both on students' being able to read and understand existing visualizations and produce a subset of these visualizations, and

 	
  * Use R (primary tool) and [RAWGraphs](http://app.rawgraphs.io/) for the production of these plots.




## Software: Use ggplot2 in R


The choice to use R was not an immediate one. We initially looked at using Tableau, but the default choices made by the software (e.g., to immediately plot summaries rather than raw data) and the cost for students after matriculating from the course eventually sealed its fate (we don't use it). We contemplated using Excel for a minute (gasp!), but we vetoed that even quicker than Tableau. The [RAWGraphs website](http://app.rawgraphs.io/), we felt, held a lot of promise as a software tool for the course. It had an intuitive drag-and-drop interface, and could be used to create many of the plots we wanted students to produce. Unfortunately, we were not able to get the bar graph widget to produce side-by-side bar plots easily (actually at all). The other drawback was that the drag-and-drop interactions made it a harder sell to the LE committee as a method of building students' computational and mathematical thinking if we used it as the primary tool.

Once we settled on using R, we had to decide between using the suite of **base plots**, or **ggplot2** (**lattice** was not in the running). We decided that **ggplot** made the most sense in terms of thinking about extensibility. Its syntax was based on a theoretical foundation for creating and thinking about plots, which also made it a natural choice for a data visualization course. The idea of mapping variables to aesthetics was also consistent with the language used in RAWGraphs, so it helped reenforce core ideas across the tools. Lastly, we felt that using the ggplot syntax would also help students transition to other tools (such as ggviz or plotly) more easily.

One thing that the teaching team completely agreed on (and was mentioned by almost everyone who we talked to who taught data visualization) was that we wanted students to be producing graphs very early in the course; giving them a sense of power and the reenforcement that they could be successful. We felt this might be difficult for students with the ggplot syntax. To ameliorate this, we wrote a course-specific R package ([epsy1261; available on github](https://github.com/zief0002/epsy1261)) that allows students to create a few simple plots interactively by employing functionality from the manipulate package. (We could have also done this via Shiny, but I am not as well-versed in Shiny and only had a few hours to devote to this over the summer given other responsibilities.)

[caption id="attachment_1226" align="aligncenter" width="2124"][![](http://citizen-statistician.org/wp-content/uploads/2017/10/Screen-Shot-2017-10-07-at-10.16.24-AM.png)](http://citizen-statistician.org/2017/10/07/data-visualization-course-for-freshmen/screen-shot-2017-10-07-at-10-16-24-am/) Interactive creation of the bar chart using the **epsy1261** package. This allows students to input  minimal syntax, barchart(data), and then use interaction to create plots.[/caption]


## Course Content


We decided on a three-pronged approach to the course content. The first prong would be based on the production of common statistical plots: bar charts, scatterplots, and maps, and some variations of these (e.g., donut plots, treemaps, bubble charts). The second prong was focused on reading more complex plots (e.g., networks, alluvial plots), but not producing them, except maybe by hand. The third prong was a group project. This would give students a chance to use what they had learned, and also, perhaps, access other plots we had not covered. In addition, we wanted students to consider narrative in the presentation of these plots—to tell a data-driven story.

Along with this, we had hoped to introduce students to computational skills such as data summarization, tidying, and joining data sets. We also wanted to introduce concepts such as smoothing (especially for helping describe trend in scatterplots), color choice, and projection and coordinate systems (in maps). Other things we thought about were using R Markdown and data scraping.


# Reality


The reality, as we are finding now that we are over a third of the way through the course, is that this amount of content was over-ambitious. We grossly under-estimated the amount of practice time these students would need, especially working with R. Two things play a role in this:



 	
  1. The course attracted way more students than we expected for the first offering (our class size is 44) and there is a lot of heterogeneity of students' experiences and academic background. For example, we have graduate students from the School of Design, some first years, and mostly sophomores and juniors. We also have a variety of majors including, design, the social sciences, and computer science.

 	
  2. We hypothesize that students are not practicing much outside of class. This means they are essentially only using R twice a week for 75 minutes when they are in class. This amount of practice is too infrequent for students to really learn the syntax.


Most of the students' computational experiences are minimal prior to taking this course. They are very competent at using point-and-click software (e.g., Google Docs), but have an abundance of trouble when forced to use syntax. The precision of case-sensitivity, commas, and parentheses is outside their wheelhouse.

I would go so far as to say that several of these students are intimidated by the computation, and completely panic on facing an error message. This has led to us having to really think through and spend time discussing computational workflows and dealing with how to "de-bug" syntax to find errors. All of this has added more time than we anticipated on the actual computing. (While this may add time, it is still educationally useful for these students.)

The teaching team meets weekly for 90 minutes to discuss and reflect on what happened in the course. We also plan what will happen in the upcoming week based on what we observed and what we see in students' homework. As of now, we clearly see that students need more practice, and we have begun giving students the end result of a plot and asking them to re-create these.

I am still hoping to get to scatterplots and maps in the course. However, some of the other computational ideas (scraping, joining) may have to be relegated to conceptual ideas in a reading. We are also considering scrapping the project, at least for this semester. At the very least, we will change it to a more structured set of plots they need to produce rather than letting them choose the data sets, etc. Live and learn. Next time we offer the course it will be better.

***Technology note:** RAWGraphs can be adapted by designing additional chart types, so in theory, if one had time, we could write our own version to be more compatible with the course. We are also considering using the **[ggplotgui](https://github.com/gertstulp/ggplotgui/)** package, which is a Shiny dashboard for creating ggplot plots.




