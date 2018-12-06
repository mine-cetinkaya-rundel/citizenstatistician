---
author: mine
comments: true
date: 2012-10-08 04:22:56+00:00
layout: post
link: http://citizen-statistician.org/2012/10/08/planting-seeds-of-reproducibility-with-knitr-and-markdown/
slug: planting-seeds-of-reproducibility-with-knitr-and-markdown
title: Planting seeds of reproducibility with knitr and markdown
wordpress_id: 47
categories:
- Computation
- statistical software
- Teaching
tags:
- knitr
- R
- reproducibility
- RStudio
- teaching
---

I attended useR! 2012 this past summer and one of the highlights of the conference was a [presentation](http://yihui.name/slides/2012-knitr-RStudio.html) by [Yihui Xie](http://yihui.name/en/) and [JJ Allaire](http://rstudio.org/docs/about) on [knitr](http://yihui.name/knitr/). As an often frustrated user of Sweave, I was very impressed with how they streamlined the process of integrating R with LaTeX and other document types, and I was excited to take advantage of the tools. It also occurred to me that these tools, especially the simpler [markdown](http://rstudio.org/docs/authoring/using_markdown) language, could be useful to the students in my introductory statistics course.

For context, I teach a large introductory statistics class with mostly first and second year social science majors. The course has a weekly lab component where students start using R from day one. The emphasis is on concepts and interpretation, as a way of reinforcing lecture material, but students are also expected to be comfortable enough with R to analyze novel data.

So why should students use knitr? Almost all students in this class have no programming experience, and are unfamiliar with command line interfaces. As such, they tend towards  a trial-and-error approach where they repeat the same command over and over again with minor modifications until it yields a reasonable result. This exploratory phase is important, as it helps them become comfortable with R. However it comes with frustraring side effects, such as cluttering the console and workspace, and hence leading to errors that are difficult to debug (e.g., inadvertently overwriting needed variables) and making it difficult for the students to reproduce their own results.

As of this semester, my students are using knitr and markdown to complete their lab reports. In an effort to make the transition from standard word processors as painless as possible, we provide templates containing precise formatting that informs the students on where to embed code vs. written responses. Throughout the semester, the amount of instructions are decreased as the students become more comfortable with the language and the overall formatting of the lab write-ups.

This is still work in progress, but after five labs my impressions are very positive. Students are impressed that their plots show up "magically" in the reports, and enjoy being able to complete their analysis and the write up entirely in RStudio. This eliminates the need to copy and paste plots and outputs into a word processor, and makes revisions far less error prone. Another benefit is that this approach forces them to keep their analysis organized, which helps keep the frustration level down.

And the cherry on top - lab reports created using markdown are much easier for myself and the teaching assistants to grade, since code, output, and write-up are automatically organized in a logical order and all reports follow the same structure.


[![](http://citizen-statistician.org/wp-content/uploads/2012/10/lab_excerpt-300x273.png)](http://citizen-statistician.org/wp-content/uploads/2012/10/lab_excerpt.png)


There were, of course, some initial issues:



	
  * Not immediately realizing that it is essential to embed the code inside chunks identified by ```{r} and ``` in order for it to be processed.

	
  * Running the code in the console first and then copying and pasting into the markdown document results in stray > and + signs, which results in cryptic errors.

	
  * The resulting document can be quite lengthy with all of the code, R output, plots, and written responses, making it less likely for students thoroughly review and catch errors.

	
  * Certain mistakes in R code (such as an extraneous space in a variable name) prevent the document from compiling (other errors will result in a compiled document with the error output). This is perhaps the most frustrating problem since it makes it difficult for the students to identify the source of the error.


With guidance from peers, teaching assistants, and myself, the students quickly develop the skills necessary to troubleshoot these issues, and after 5 weeks, such errors have all but vanished.

It's not all [sunshine and lollipops](http://www.youtube.com/watch?v=XQmBXEZEYtg) though, there are some missing features that would make knitr / RStudio more user friendly in this context:



	
  * Write to PDF: The markdown document creates an HTML file when compiled, which is useful for creating webpages, but a PDF output would be much more useful for students turning in printed reports. (Suggestion: [Pandoc](http://johnmacfarlane.net/pandoc/), ref: [stackoverflow](http://stackoverflow.com/questions/11025123/how-to-convert-r-markdown-to-pdf).)

	
  * Smart page breaks: Since the resulting HTML document is not meant to be printed on letter sized pages, plots and R output can be split between two pages when printed, which is quite messy.

	
  * Word count:  A word count feature that only counts words in the content, and not in the code, would be immensely useful for setting and sticking to length requirements. (Suggestion: [Marked](http://markedapp.com/), ref: [this post](http://christophergandrud.blogspot.com/2012/05/dynamic-content-with-rstudio-markdown.html).)


Tools for resolving some of these issues are out there, but none of them can currently be easily integrated into the RStudio workflow.

All of the above amount to mostly logistic practicalities for using knitr in an introductory course, but there is also a larger pedagogical argument for it: introducing reproducible research in a practical and painless way. Reproducible research is not something that many first or second year undergraduate students are aware of -- after all, very few of them are actually engaged in research activities at that point in their academic careers. At best, students are usually aware that reproducibility is one of the central tenants of the scientific method, but have given very little thought to what that involves either as a researcher producing work that others will want to replicate, or as someone attempting to reproduce another author's work. In the context of completing simple lab assignments and projects with knitr, students experience first hand the benefits and the frustrations of reproducible research, which is hopefully a lesson they'll take away from the class, regardless of how much R or statistics they remember.

PS: If you're interested in the nuts and bolts, you can review the labs as well as knitr templates [here](http://stat.duke.edu/courses/Fall12/sta101.001/schedule.html).
