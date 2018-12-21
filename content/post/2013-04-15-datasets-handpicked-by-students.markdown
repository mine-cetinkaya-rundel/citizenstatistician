---
author: mine
comments: true
date: 2013-04-15 03:40:41+00:00
layout: post
link: http://citizen-statistician.org/2013/04/15/datasets-handpicked-by-students/
slug: datasets-handpicked-by-students
title: Datasets handpicked by students
wordpress_id: 206
categories:
- rstats
- teaching
---

I'm often on the hunt for datasets that will not only work well with the material we're covering in class, but will (hopefully) pique students' interest. One sure choice is to use data collected from the students, as it is easy to engage them with data about themselves. However I think it is also important to open their eyes to the vast amount of data collected and made available to the public. It's always a guessing game whether a particular dataset will actually be interesting to students, so learning from the datasets _they_ choose to work with seems like a good idea.

Below are a few datasets that I haven't seen in previous project assignments. I've included the research question the students chose to pursue, but most of these datasets have multiple variables, so you might come up with different questions.

1. _Religious service attendance and moral beliefs about contraceptive use:_ The data are from a February 2012 Pew Research poll. To download the dataset, go to [http://www.people-press.org/category/datasets/?download=20039620](http://www.people-press.org/category/datasets/?download=20039620). You will be prompted to fill out some information and will receive a zipped folder including the questionnaire, methodology, the "topline" (distributions of some of the responses), as well as the raw data in SPSS format (.sav file). Below I've provided some code to load this dataset in R, and then to clean it up a bit. Most of the code should apply to any dataset released by Pew Research.

```
# read data
library(foreign)
d_raw = as.data.frame(read.spss("Feb12 political public.sav"))

# clean up
library(stringr)
d = lapply(d_raw, function(x) str_replace(x, " \\[OR\\]", ""))
d = lapply(d, function(x) str_replace(x, "\\[VOL. DO NOT READ\\] ", ""))
d = lapply(d, function(x) str_replace(x, "\222", "'"))
d = lapply(d, function(x) str_replace(x, " \\(VOL.\\)", ""))
d$partysum = factor(d$partysum)
levels(d$partysum) = c("Refused","Democrat","Independent","Republican","No preference","Other party")
```

The student who found this dataset was interested examining the relationship between religious service attendance and views on contraceptive use. The code provided below can be used to organize the levels of these variables in a meaningful way, and to take a quick peek at a contingency table.

```
# variables of interest
d$attend = factor(d$attend, levels = c("More than once a week","Once a week", "Once or twice a month", "A few times a year", "Seldom", "Never", "Don't know/Refused"))
d$q40a = factor(d$q40a, levels = c("Morally acceptable","Morally wrong", "Not a moral issue", "Depends on situation", "Don't know/Refused"))
table(d$attend, d$q40a)
```

2. _Social network use and reading:_ Another student was interested in the relationship between number of books read in the last year and social network use. This dataset is provided by the Pew Internet and American Life Project. You can download a .csv version of the data file at [http://www.pewinternet.org/Shared-Content/Data-Sets/2012/February-2012--Search-Social-Networking-Sites-and-Politics.aspx](http://www.pewinternet.org/Shared-Content/Data-Sets/2012/February-2012--Search-Social-Networking-Sites-and-Politics.aspx). The questionnaire can also be found at this website. One of the variables of interest, number of books read in the past 12 months (q2), is  recorded using the following scheme:
	
  * 0: none
  * 1-96: exact number
  * 97: 97 or more
  * 98: don't know
  * 99: refused

This could be used to motivate a discussion about the importance doing exploratory data analysis prior to jumping into running inferential tests (like asking "Why are there no people who read more than 99 books?") and also pointing out the importance of checking the codebook.

3. _Parental involvement and disciplinary actions at schools:_ The 2007-2008 School Survey on Crime and Safety, conducted by the National Center for Education Statistics, contains school level data on crime and safety. The dataset can be downloaded at [http://nces.ed.gov/surveys/ssocs/data_products.asp](http://nces.ed.gov/surveys/ssocs/data_products.asp).  The SPSS formatted version of the data file (.sav) can be loaded in R using the read.spss() function in the foreign library (used above in the first data example). The variables of interest for the particular research question the student proposed are parent involvement in school programs (C0204) and number of disciplinary actions (DISTOT08), but the dataset can be used to explore other interesting characteristics of schools, like type of security guards, whether guards are armed with firearms, etc.

4. _Dieting in school-aged children:_ The Health Behavior in School-Aged Children is an international survey on health-risk behaviors of children in grades 6 through 10. The 2005-2006 US dataset can be found at [http://www.icpsr.umich.edu/icpsrweb/ICPSR/studies/28241](http://www.icpsr.umich.edu/icpsrweb/ICPSR/studies/28241). You will need to log in to download the dataset, but you can do so using a Google or a Facebook account. There are multiple versions of the dataset posted, and the Delimited version (.tsv) can be easily loaded in R using the read.delim() function. The student who found this dataset was interested in exploring the relationship between race of the student (Q6_COMP) and whether or not the student is on a diet to lose weight (Q30). The survey also asks questions on body image, substance use, bullying, etc. that may be interesting to explore.

One common feature of the above datasets is that they are all observational/survey based as it's more challenging to find experimental (raw) datasets online. Any suggestions?
