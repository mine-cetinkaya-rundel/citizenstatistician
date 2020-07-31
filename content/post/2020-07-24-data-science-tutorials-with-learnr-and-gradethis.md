---
title: Data Science Tutorials with Learnr and Gradethis
author: Lee Suddaby, Zeno Kujawa
date: '2020-07-24'
slug: data-science-tutorials-with-learnr-and-gradethis
categories: []
tags: []
keywords:
  - tech
---

*This post was contributed by [Lee Suddaby](https://github.com/lee-suddaby) and [Zeno Kujawa](https://github.com/ZenoMK).*

Over the university summer break (which was slightly longer than usual - thanks COVID!), we (Zeno and Lee) were busy making preparations for moving more of our Introduction to Data Science course from being human-graded to computer-graded. 

<!--more-->

Even without the existence of a certain pandemic virus (not naming names of course), moving course delivery online and to more automated marking has definite advantages. For one, feedback can be instant and significantly more informative than R's sometimes cryptic errors: for example, what on earth does `"object of type 'closure' is not subsettable"` mean? For two, this method is much more scalable. Courses are growing, which *should* be a good thing, but manual marking is not scalable unless your human resources are growing at the same rate as class sizes.

The solution then? Interactive tutorials, with help from the `shiny`, `learnr` and `gradethis`. In our case, we were converting written homeworks (the very ones we'd both completed on our time on the course last year!) into the auto-graded tutorials.


### Work(flow)ing 9 to 5

Behind every successful project is a successful workflow, so that is where we start. Our base is, of course, Github. Then, whisk in a handful of Pull Requests, two cups of peer reviews, and a few Issues if necessary, and mix to form a smooth batter. Bake in an RStudio environment for 20-25 minutes and add Merge Conflicts to taste.

Our first task was to familiarise oursevles with the particular packages - `learnr` and `gradethis` (more on these two below). Having done this, our workflow involved writing the tutorials two at a time - one person writing each - then reviewing the other person's work. After as many cycles of implementing and reviewing changes, a final review was carried out by the course organiser Dr. Çetinkaya-Rundel, who is also the creator of Citizen Statistician.


### learnr

`learnr` is an R package designed to make it easy to build interactive tutorials in R markdown documents. These tutorials can contain all manner of objects, including text, graphics and figures, sections and subsections, code exercises that students can execute, multiple choice questions, even YouTube videos!


One of our tutorials was slightly adapted for use the Teach R Online workshop series. You can see it [here](https://gallery.shinyapps.io/lego-sales/)

### Challenges

We quickly learned that converting the homework assignments wouldn't be as straightforward as just replicating the questions in a `shiny` document. Since some tasks like interpreting visualisations can't easily be graded automatically, we had to make certain trade-offs. Usually, this either meant replacing an open-ended question with a series of multiple-choice questions while trying to preserve a questions essential lesson. 

Another question we had to ask ourselves frequently was whether the students code itself or the output it produced should be evaluated. Here's an example of this conundrum: 

<img src="https://imgur.com/sVa8ehy.jpg" width="499" height="95" />

There are many ways to answer this question in R, and since we wanted students to be awarded points whichever correct way they chose, we implemented result grading on this question, so that every answer that produced the correct output would be marked as correct. 
With visualisations and code that doesn't produce any output, however, this becomes a bit trickier. 
In those situations, we decided to grade the code itself, which has the disadvantage that the code has to be exactly the same as in the solution, even though it would have the same effect if two lines were interchanged. We tried to circumvent the problem by giving the students more hints and providing a structure where fewer mistakes would be possible. The following image is an example of how we dealt with visualisation exercises:

<img src="https://imgur.com/qYIvTx1.jpg" width="500" height="211" />

### Conclusion

We hope that our converted assignments will help scale the course and deliver something very close to the experience we had last fall. 
Both of us learned a lot through this project and we are very eager to hear what next years students have to say about the course! We would like to thank Dr. Çetinkaya-Rundel for the giving us the opportunity to be part of IDS and her neverending patience for us! 