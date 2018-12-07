---
author: andy
comments: true
date: 2012-10-15 15:06:16+00:00
layout: post
link: http://citizen-statistician.org/2012/10/15/red-bull-stratos-mission-data/
slug: red-bull-stratos-mission-data
title: Red Bull Stratos Mission Data
wordpress_id: 138
categories:
- pret-a-porter
---

Yesterday (October 14, 2012), Felix Baumgartner made history by becoming the first person to break the speed of sound during a free fall. He also set some other records (e.g., longest free fall, etc.) during the [Red Bull Stratos Mission](www.redbullstratos.com)–which was broadcast live on the internet. Kind of cool, but imagine the conversation that took place daydreaming this one...


**Red Bull Creative Person: **What if we got some idiot to float up into the stratosphere in a space capsule and then had him step out of it and free fall four minutes breaking the sound barrier?




**Another Red Bull Creative Person: **Great idea! Lets' also broadcast it live on the internet.


Well anyway, after the craziness ensued, It was suggested on Facebook that, "I think this data should be on someone's blog!". Rising to the bait, I immediately looked at the mission page,  but the data was no longer there. Thank goodness for Wikipedia [[Red Bull Stratos Mission Data](http://en.wikipedia.org/wiki/Red_Bull_Stratos/Mission_data)]. The data can be copied and pasted into an Excel sheet, or read in to R using the readHTMLTable() function from the **XML** package.

```
mission <- readHTMLTable(
  doc = "http://en.wikipedia.org/wiki/Red_Bull_Stratos/Mission_data",
  header = TRUE
  )
```

We can then write it to an external file, I called it _Mission.csv_ and put it on my desktop, using the `read.csv()` function.

```
write.csv(mission,
  file = "/Users/andrewz/Desktop/Mission.csv",
  row.names = FALSE,
  quote = FALSE
  )
```

Opening the new file in a text editor, we see some issues to deal with (these are also apparent from looking at the data on the Wikipedia page).



	
  * The first line is the first table header, _Elevation Data_, which spanned three columns in the Wikipedia page. Delete it.

	
  * The last row are the re-printed variable names. Delete it.

	
  * Change the variable names in the current first row to be statistical software compliant (e.g., remove the commas and spaces from each variable). My first row looks like the following:




Time,Elevation,DeltaTime,Speed








	
  * Remove the commas from the values in the last column. With a comma separated value (CSV) file, they are trouble.

	
  * There are nine rows which have parentheses around their value in the last column. I don't know what this means. For now, I will remove those values.


The file can be downloaded [here](http://citizen-statistician.org/?attachment_id=152).

Then you can plot (or analyze) away to your heart's content.

```
# read in data to R
mission <- read.csv(file = "/Users/andrewz/Desktop/Mission.csv")

# Load ggplot2 library
library(ggplot2)

# Plot speed vs. time
ggplot(data = mission, aes(x = Time, y = Speed)) +
  geom_line()

# Plot elevation vs. time
ggplot(data = mission, aes(x = Time, y = Elevation)) +
  geom_line()
```

[![](http://citizen-statistician.org/wp-content/uploads/2012/10/p1-1024x1024.jpg)](http://citizen-statistician.org/wp-content/uploads/2012/10/p1.jpg)

[![](http://citizen-statistician.org/wp-content/uploads/2012/10/p2-1024x1024.jpg)](http://citizen-statistician.org/wp-content/uploads/2012/10/p2.jpg)

Since I have no idea what these really represent other than what the variable names tell me, I cannot interpret these very well. Perhaps someone else can.
