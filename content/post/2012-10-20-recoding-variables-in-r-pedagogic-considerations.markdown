---
author: andy
comments: true
date: 2012-10-20 19:37:34+00:00
layout: post
link: http://citizen-statistician.org/2012/10/20/recoding-variables-in-r-pedagogic-considerations/
slug: recoding-variables-in-r-pedagogic-considerations
title: 'Recoding Variables in R: Pedagogic Considerations'
wordpress_id: 160
categories:
- Computation
- R Project
- Teaching
---

I was creating a dataset this last week in which I had to partition the observed responses to show how the ANOVA model partitions the variability. I had the observed _Y _(in this case prices for 113 bottles of wine), and a categorical predictor _X_ (the region of France that each bottle of wine came from). I was going to add three columns to this data, the first showing the marginal mean, the second showing the effect, and the third showing the residual. To create the variable indicating the effect, I essentially wanted to recode a particular region to a particular effect:



	
  * Bordeaux ==> 9.11

	
  * Burgundy ==> 4.20

	
  * Languedoc ==> –9.30

	
  * Rhone ==> –0.75


As I was considering how to do this, it struck me that several options were available to me. Here are two solutions that come up when Googling how to do this.

Use the recode() function from the **car** package.

[sourcecode language="r"]
library(car)
wine$Effect <- recode(wine$Region,
  " 'Bordeaux' = 9.11;
    'Bordeaux' = 4.20;
    'Languedoc' = -9.30;
    'Rhone' = -0.75 " )
[/sourcecode]


This is a commonly suggested solution. The strings inside quotation marks, however, make it likely students (and teachers) will commit a syntax error. This is especially true when recoding a categorical variable into another categorical variable. R-wise (it's a technical term) it also produces a factor, even though it is clear that the intent was to produce numerical values. This is of course, easily fixable using as.numeric(), but it can lead to confusion.










Another solution is to use indexing.


[sourcecode language="r"]
wine$Effect <- 9.11
wine$Effect[wine$Region == "Burgundy"] <- 4.20
wine$Effect[wine$Region == "Languedoc"] <- -9.30
wine$Effect[wine$Region == "Rhone"] <- -0.75
[/sourcecode]





This solution is canonical in that it is clean and the R code is concise. (Note: This is what I ended up using to create this re-coded variable.) In my experience, however, this also means that students without a programming background don't initially understand it. This alone makes it unattractive pedagogically.





A better solution pedagogically seems to be to create a new data frame of key-value pairs (in computer science this is called a hash table) and then use the join() function from the _plyr_ package to `join' the original data frame and the new data frame.

[sourcecode language="r"]
key <- data.frame(
  Region = c("Bordeaux", "Burgundy", "Languedoc", "Rhone"),
  Effect = c(9.11, 4.20, -9.33, -0.75)
  )
join(wine, key, by = Region)
[/sourcecode]

For me this is a useful way to teach how to recode variables. It has a direct link to the Excel VLOOKUP function, and also to ideas of relational databases. It also allows more generalizability in terms of being able to merge data sets using a common variable.

R-wise, it is not difficult syntax, since almost every student has successfully used the data.frame() function to create a data frame. The join() function is also easily explained.
