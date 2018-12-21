---
author: citizenstat
comments: true
date: 2017-07-24 20:48:16+00:00
layout: post
link: http://citizen-statistician.org/2017/07/24/are-computers-needed-to-teach-data-science/
slug: are-computers-needed-to-teach-data-science
title: Are computers needed to teach Data Science?
wordpress_id: 1136
categories:
- computing
- musings
- rstats
- statistical software
- teaching
---

One of the many nice things about summer is the time and space it allows for blogging. And, after a very stimulating SRTL conference (Statistics Reasoning, Teaching and Learning) in Rotorua, New Zealand, there's lots to blog about.

Let's begin with a provocative posting by fellow SRTL-er Tim Erickson at his excellent blog [A Best Case Scenario](https://bestcase.wordpress.com/2017/07/18/more-about-data-moves-and-r/).  I've known Tim for quite awhile, and have enjoyed many interesting and challenging discussions. Tim is a creator of curricula _par excellence_, and has first-hand experience in what inspires and motivates students to think deeply about statistics.

The central question here is: Is computation (on a computer) necessary for learning data science? The learners here are beginners in K-12. Tim answers no, and I answer, tentatively, yes. Tim portrays me in his blog as being a bit more steadfast on this position than I really am. In truth the answer is, some; maybe; a little; I don't know.

My own experience in the topic comes from the [Mobilize](http://www.mobilizingcs.org/) project  , in which we developed the course Introduction to Data Science for students in the Los Angeles Unified School District. (I'm pleased to say that the course is expanding. This summer, five new L.A.-area school districts will begin training teachers to teach this course. )

The course relies heavily on R via Rstudio. Students begin by studying the structure of data, learning to identify cases and variables and to organize unstructured data into a "tidy" format. Next, they learn to "read" tidy datafiles into Rstudio. The course ends with students learning some predictive modeling using Classification and Regression Trees. In between, they study some inference using randomization-based methods.

To be precise, the students don't learn straight-up R. They work within a package developed by the Mobilize team (primarily James Molyneux, Amelia McNamara, Steve Nolen, Jeroen Ooms, and Hongsuda Tangmunarunkit) called mobilizR, which is based pretty heavily on the [mosaic](http://mosaic-web.org) package developed by Randall Pruim, Danny Kaplan and Nick Horton.  The idea with these packages is to provide beginners to R with a unified syntax and a set of verbs that relate more directly to the analysts' goals. The basic structure for (almost) all commands is

_WhatIWantToDo(yvariable~xvariables, dataset)_

For example, to see the average walking distance recorded by a fitbit by day of the week:

    
    
     > mean(Distance~DOW,data=fitbitdec)
     Friday Monday Saturday Sunday Thursday Tuesday Wednesday 1.900000 3.690000 2.020909 2.419091 1.432727 3.378182 3.644545


The idea is to provide students with a simplified syntax that "bridges the gap" between beginners of R and more advanced users. Hopefully, this frees up some of the cognitive load required to remember and employ R commands so that students can think strategically and statistically about problems they are trying to solve.

The "bridge the gap" terminology comes from Amelia McNamara, who used the term in her PhD [dissertation.](http://www.science.smith.edu/~amcnamara/dissertation.html) One of the many really useful ideas Amelia has given us is the notion that the gap needs to be bridged. Much of "traditional" statistics education holds to the idea that statistical concepts are primarily mathematical, and, for most people, it is sufficient to learn enough of the mathematical concepts so that they can react skeptically and critically to others' analyses. What is exciting about data science in education is that students can do their own analyses. And if students are analyzing data and discovering on their own (instead of just trying to understand others' findings), then we need to teach them to use software in such a way that they can transition to more professional practices.

And now, dear readers, we get to the heart of the matter. That gap is really hard to bridge. One reason is that we know little to nothing about the terrain. How do students learn coding when applied to data analysis? How does the technology they use mediate that experience? How can it enhance, rather than inhibit, understanding of statistical concepts and the ability to do data analysis intelligently?

In other words, what's the learning trajectory?

Tim rightly points to [CODAP](https://concord.org/projects/codap), the Common Online Data Analysis Platform,  as one tool that might help bridge the gap by providing students with some powerful data manipulation techniques. And I recently learned about [data.world](https://data.world/), which seems another attempt to help bridge the gap.  But Amelia's point is that it is not enough to give students the ability to do something; you have to give it to them so that they are prepared to learn the next step. And if the end-point of a statistics education involves coding, then those intermediate steps need to be developing students' coding skills, as well as their statistical thinking. It's not sufficient to help studemts learn statistics. They must simultaneously learn computation.

So how do we get there? One important initial step, I believe, is to really examine what the term "computational thinking" means when we apply it to data analysis. And that will be the subject of an upcoming summer blog.
