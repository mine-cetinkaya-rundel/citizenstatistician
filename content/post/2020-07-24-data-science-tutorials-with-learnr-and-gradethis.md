---
title: Data Science Tutorials with learnr and gradethis
author: Lee Suddaby, Zeno Kujawa
date: '2020-07-24'
slug: data-science-tutorials-with-learnr-and-gradethis
categories: 
  - teaching
  - shiny
  - rstats
tags: 
  - learnr
  - gradethis
  - tidyverse
keywords:
  - tech
---

*This post was contributed by [Lee Suddaby](https://github.com/lee-suddaby) and [Zeno Kujawa](https://github.com/ZenoMK).*

Over the university summer break, we (Zeno and Lee) were busy making preparations for moving more of our [Introduction to Data Science](https://introds.org/) course from being human-graded to computer-graded. We both took this course in the Fall of 2019, as part of our first-year studies at the University of Edinburgh, and this is where we first learned R.

<!--more-->

Moving course delivery online and to more automated marking has definite advantages. For one, feedback can be instant and significantly more informative than R's sometimes cryptic errors: for example, what on earth does `"object of type 'closure' is not subsettable"` mean? For two, this method is much more scalable. Courses are growing, which *should* be a good thing, but manual marking is not scalable unless your human resources are growing at the same rate as class sizes.

The solution then? Interactive tutorials, with help from the [**learnr**](https://rstudio.github.io/learnr/) and [**gradethis**](https://github.com/rstudio-education/gradethis) packages. In our case, we were converting written homeworks (the very ones we'd both completed on our time on the course last fall!) into the auto-graded tutorials.


### Work(flow)ing 9 to 5

Behind every successful project is a successful workflow, so that is where we start. Our base is, of course, Github. Then, whisk in a handful of pull requests, two cups of peer reviews, and a few issues if necessary, and mix to form a smooth batter. Bake in an RStudio environment for 20-25 minutes and add merge conflicts to taste.

Our first task was to familiarise ourselves with the particular packages - learnr and gradethis (more on these two below). Having done this, our workflow involved writing the tutorials two at a time - one person writing each - then reviewing the other person's work. After as many cycles of implementing and reviewing changes, a final review was carried out by the course organiser Dr. Çetinkaya-Rundel, who is also the creator of Citizen Statistician.


### learnr

learnr is an R package designed to make it easy to build interactive tutorials in R markdown documents. These tutorials can contain all manner of objects, including text, graphics and figures, sections and subsections, code exercises that students can execute, multiple choice questions, even YouTube videos!

If you're interested in using (or just playing about with) the package yourself, it's available on CRAN, and you can learn about it [here](https://rstudio.github.io/learnr/).


### gradethis

gradethis is a companion to the learnr package, and provides multiple different functions for grading learnr exercises. Code can either be graded against a certain solution, where we check that the student's answer exactly matches the solution, or the result can be checked against a set of conditions.
With the gradethis package, it's also easy to give helpful feedback if a student gets a foreseen wrong answer, so we can nudge them in the right direction.

This package is not yet on CRAN, but you can install it from the Github repository [here](https://github.com/rstudio-education/gradethis).


### Challenges

We quickly learned that converting the homework assignments wouldn't be as straightforward as just replicating the questions in a learnr tutorial. Since some tasks like interpreting visualisations can't easily be graded automatically, we had to make certain trade-offs. Usually, this either meant replacing an open-ended question with a series of multiple-choice questions while trying to preserve a questions essential lesson. 

Another question we had to ask ourselves frequently was whether the student's code itself or the output it produced should be evaluated. Here's an example of this conundrum: 

![Learnr tutorial code block example](/post/2020-07-24-data-science-tutorials-with-learnr-and-gradethis_files/sVa8ehy.png)

There are many ways to answer this question in R, and since we wanted students to be awarded points whichever correct way they chose, we implemented result grading on this question, so that every answer that produced the correct output would be marked as correct. 
With visualisations and code that doesn't produce any output, however, this becomes a bit trickier. 
In those situations, we decided to grade the code itself, which has the disadvantage that the code has to be exactly the same as in the solution, even though it would have the same effect if two lines were interchanged. We tried to circumvent the problem by giving the students more hints and providing a structure where fewer mistakes would be possible. The following image is an example of how we dealt with visualisation exercises:

![Learnr tutorial code block showing visualisation exercise example](/post/2020-07-24-data-science-tutorials-with-learnr-and-gradethis_files/qYIvTx1.png)


### Conclusion

We hope that our converted assignments will help scale the course and deliver something very close to the experience we had last fall. 
Both of us learned a lot through this project and we are very eager to hear what next years students have to say about the course! We would like to thank Dr. Çetinkaya-Rundel for the giving us the opportunity to be part of IDS and her neverending patience for us! 

If you're interested, one of our tutorials was slightly adapted for use the Teach R Online workshop series. You can see it [here](https://gallery.shinyapps.io/lego-sales/).
