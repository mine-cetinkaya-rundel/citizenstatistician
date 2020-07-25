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

The solution then? Interactive tutorials, with help from the `shiny`, `learnr` and `gradethis`.


### Work(flow)ing 9 to 5