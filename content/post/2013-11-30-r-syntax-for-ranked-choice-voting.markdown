---
author: andy
comments: true
date: 2013-11-30 22:55:21+00:00
layout: post
link: http://citizen-statistician.org/2013/11/30/r-syntax-for-ranked-choice-voting/
slug: r-syntax-for-ranked-choice-voting
title: R Syntax for Ranked Choice Voting
wordpress_id: 744
categories:
- Computation
- R Project
---

I have gotten several requests for the R syntax I used to analyze the ranked-choice voting data and create the animated GIF. Rather than just posting the syntax, I thought I might write a detailed post describing the process.


# Reading in the Data


The data is available on the Twin Cities R User Group's [GitHub page](https://github.com/tcrug). The file we are interested in is [2013-mayor-cvr.csv](https://github.com/tcrug/ranked-choice-vote-data/blob/master/2013-mayor-cvr.csv). Clicking this link gets you the "Display" version of the data. We actually want the "Raw" data, which is viewable by clicking [View Raw](https://raw.github.com/tcrug/ranked-choice-vote-data/master/2013-mayor-cvr.csv). The link is using a secure connection (https://) which R does not handle well without some workaround.

One option is to use the `getURL()` function from the **RCurl** library. The `text=` argument in the `read.csv()` function reads the data in using a text connection, and is necessary to not receive an error.

[code language="r"]
library(RCurl)
url = getURL("https://raw.github.com/tcrug/ranked-choice-vote-data/master/2013-mayor-cvr.csv")
vote = read.csv(text = url)
[/code]

A quick look at the data reveal that the three ranked choices for the 80,101 voters are in columns 2, 3, and 4. The values "undervote" and "overvote" are ballot also need to be converted to "NA" (missing). The syntax below reduces the data frame to the second, third and fourth columns and replaces "undervote" and "over vote' with NAs.

[code language="r"]
vote = vote[ , 2:4]
vote[vote == "undervote"] = NA
vote[vote == "overvote"] = NA
[/code]

The syntax below is the main idea of the vote counting algorithm. (You will need to load the **ggplot** library.) I will try to explain each line in turn.

[code language="r"]
nonMissing = which(vote[ , 1] != "")
candidates = vote[nonMissing, 1]
#print(table(candidates))

vote[ , 1] =  factor(vote[ , 1], levels = rev(names(sort(table(vote[ , 1]), decreasing=TRUE))))
mayor = levels(vote[ , 1])
candidates = vote[nonMissing, 1]

p = ggplot(data = data.frame(candidates), aes(x = factor(candidates, levels = mayor))) +
	geom_bar() +
	theme_bw() +
	ggtitle("Round 1") +
	scale_x_discrete(name = "", drop = FALSE) +
	ylab("Votes") +
	ylim(0, 40000) +
	coord_flip()

ggsave(p, file = "~/Desktop/round1.png", width = 8, height = 6)
[/code]



	
  * Line 1: Examine the first column of the vote data frame to determine which rows are not missing.

	
  * Line 2: Take the candidates from the first column and put them in an object

	
  * Line 3: Count the votes for each candidate

	
  * Line 5: Coerce the first column into a factor (it is currently a character vector) and create the levels of that factor so that they display in reverse order based on the number of votes. This is important in the plot so that the candidates display in the same order every time the plot is created.

	
  * Line 6: Store the levels we just created from Line #5 in an object

	
  * Line 7: Recreate the candidates object (same as Line #2) but this time they are a factor. This is so we can plot them.

	
  * Line 8–16: Create the bar plot

	
  * Line 18: Save the plot onto your computer as a PNG file. In my case, I saved it to the desktop.


Now, we will create an object to hold the round of counting (we just plotted the first round, so the next round is Round 2). We will also coerce the first column back to characters.

[code language="r"]
j = 2
vote[ , 1] = as.character(vote[ , 1])
[/code]

The next part of the syntax is looped so that it repeats the remainder of the algorithm, which essentially is to determine the candidate with the fewest votes, remove him/her from all columns, take the second and third choices of anyone who voted for the removed candidate and make them the 'new' first and second choices, recount and continue.

[code language="r"]
while( any(table(candidates) >= 0.5 * length(candidates) + 1) == FALSE ){
	leastVotes = attr(sort(table(candidates))[1], "names")
	vote[vote == leastVotes] = NA
	rowNum = which(is.na(vote[ , 1]))
	vote[rowNum, 1] = vote[rowNum, 2]
	vote[rowNum, 2] = vote[rowNum, 3]
	vote[rowNum, 3] = NA
	nonMissing = which(vote[ , 1] != "")
	candidates = vote[nonMissing, 1]
	p = ggplot(data = data.frame(candidates), aes(x = factor(candidates, levels = mayor))) +
		geom_bar() +
		theme_bw() +
		ggtitle(paste("Round", j, sep =" ")) +
		scale_x_discrete(name = "", drop = FALSE) +
		ylab("Votes") +
		ylim(0, 40000) +
		coord_flip()
	ggsave(p, file = paste("~/Desktop/round", j, ".png", sep = ""), width = 8, height = 6)
	j = j + 1
	candidates = as.character(candidates)
	print(sort(table(candidates)))
	}
[/code]

The `while{}` loop continues to iterate until the criterion for winning the election is met. Within the loop:



	
  * Line 2: Determines the candidate with the fewest votes

	
  * Line 3: Replaces the candidate with the fewest votes with NA (missing)

	
  * Line 4: Stores the row numbers with any NA in column 1

	
  * Line 5: Takes the second choice for the rows identified in Line #4 and stores them in column 1 (new first choice)

	
  * Line 6: Takes the third choice for the rows identified in Line #4 and stores them in column 2 (new second choice)

	
  * Line 7: Makes the third choice for the rows identified in Line #4 an NA

	
  * Line 8–18: Are equivalent to what we did before (but this time they are in the while loop). The biggest difference is in the `ggsave()` function, the filename is created on the fly using the object we created called _j_.

	
  * Line 19: Augment_ j_ by 1

	
  * Line 20: Print the results




# Creating the Animated GIF


There should now be 35 PNG files on your desktop (or wherever you saved them in the ggsave() function). These should be called _round1.png_, _round2.png_, etc. The first thing I did was rename all of the single digit names so that they were _round01.png_, _round02.png_, …, _round09.png__._

Then I opened _Terminal_ and used _ImageMagick_ to create the animated GIF. Note that in Line #1 I move into the folder where I saved the PNG files. In my case, the desktop.

[code language="powershell"]
cd ~/Desktop
convert -delay 50 round**.png animation.gif
[/code]

The actual animated GIF appears on the [previous Citizen Statistician post](http://citizen-statistician.org/2013/11/25/ranked-choice-voting/).
