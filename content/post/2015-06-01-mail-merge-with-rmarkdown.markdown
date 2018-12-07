---
author: mine
comments: true
date: 2015-06-01 08:14:23+00:00
layout: post
link: http://citizen-statistician.org/2015/06/01/mail-merge-with-rmarkdown/
slug: mail-merge-with-rmarkdown
title: '"Mail merge" with RMarkdown'
wordpress_id: 904
categories:
- Musings
- R Project
---

The term "mail merge" might not be familiar to those who have not worked in an office setting, but here is the Wikipedia definition:


<blockquote>**Mail merge** is a software operation describing the production of multiple (and potentially large numbers of) documents from a single template form and a structured data source. The letter may be sent out to many "recipients" with small changes, such as a change of address or a change in the greeting line.

Source: http://en.wikipedia.org/wiki/Mail_merge</blockquote>


The other day I was working on creating personalized handouts for a workshop. That is, each handout contained some standard text (including some R code) and some fields that were personalized for each participant (login information for our RStudio server). I wanted to do this in RMarkdown so that the R code on the handout could be formatted nicely. Googling "rmarkdown mail merge" didn't yield much (that's why I'm posting this), but I finally came across [this tutorial](http://reed.edu/data-at-reed/software/R/markdown_multiple_reports.html) which called the process "iterative reporting".

Turns our this is a pretty straightforward task. Below is a _very simple_ minimum working example. You can obviously make your markdown document a lot more complicated. I'm thinking holiday cards made in R...

All relevant files for this example can also be found [here](https://github.com/mine-cetinkaya-rundel/mail_merge).


# Input data: meeting_times.csv


This is a 20 x 2 csv file, an excerpt is shown below. I got the names from [here](http://listofrandomnames.com/).
<table cellpadding="0" width="130" style="border-collapse: collapse; width: 388px; height: 285px;" cellspacing="0" border="0" > 
<tbody >
<tr style="height: 15.0pt;" >

<td width="65" style="height: 15.0pt; width: 65pt;" height="15" >**name**
</td>

<td width="65" style="width: 65pt;" >**meeting_time**
</td>
</tr>
<tr style="height: 15.0pt;" >

<td style="height: 15.0pt;" height="15" >Peggy Kallas
</td>

<td align="right" class="xl63" >9:00 AM
</td>
</tr>
<tr style="height: 15.0pt;" >

<td style="height: 15.0pt;" height="15" >Ezra Zanders
</td>

<td align="right" class="xl63" >9:15 AM
</td>
</tr>
<tr style="height: 15.0pt;" >

<td style="height: 15.0pt;" height="15" >Hope Mogan
</td>

<td align="right" class="xl63" >9:30 AM
</td>
</tr>
<tr style="height: 15.0pt;" >

<td style="height: 15.0pt;" height="15" >Nathanael Scully
</td>

<td align="right" class="xl63" >9:45 AM
</td>
</tr>
<tr style="height: 15.0pt;" >

<td style="height: 15.0pt;" height="15" >Mayra Cowley
</td>

<td align="right" class="xl63" >10:00 AM
</td>
</tr>
<tr style="height: 15.0pt;" >

<td style="height: 15.0pt;" height="15" >Ethelene Oglesbee
</td>

<td align="right" class="xl63" >10:15 AM
</td>
</tr>
<tr style="height: 15.0pt;" >

<td style="height: 15.0pt;" height="15" >...
</td>

<td align="right" class="xl63" >...
</td>
</tr>
</tbody>
</table>


# 




# R script: mail_merge_script.R

```
## Packages
library(knitr)
library(rmarkdown)

## Data
personalized_info <- read.csv(file = "meeting_times.csv")

## Loop
for (i in 1:nrow(personalized_info)){
 rmarkdown::render(input = "mail_merge_handout.Rmd",
 output_format = "pdf_document",
 output_file = paste("handout_", i, ".pdf", sep=''),
 output_dir = "handouts/")
}
```

# RMarkdown: mail_merge_handout.Rmd

```
---
output: pdf_document
---

```{r echo=FALSE}
personalized_info <- read.csv("meeting_times.csv", stringsAsFactors = FALSE)
name <- personalized_info$name[i]
time <- personalized_info$meeting_time[i]
```

Dear `r name`,

Your meeting time is `r time`.

See you then!
```

Save the Rmd file and the R script in the same folder (or specify the path to the Rmd file accordingly in the R script), and then run the R script. This will call the Rmd file within the loop and output 20 PDF files to the handouts directory. Each of these files look something like this

[![mail_merge_sample](http://citizen-statistician.org/wp-content/uploads/2015/06/mail_merge_sample1-1024x223.png)](http://citizen-statistician.org/wp-content/uploads/2015/06/mail_merge_sample1.png)

with the name and date field being different in each one.

If you prefer HTML or Word output, you can specify this in the _output_format_ argument in the R script.
