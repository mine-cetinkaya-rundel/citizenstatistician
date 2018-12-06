---
author: andy
comments: true
date: 2015-10-30 22:51:34+00:00
layout: post
link: http://citizen-statistician.org/2015/10/30/fruit-plot-plotting-using-multiple-pngs/
slug: fruit-plot-plotting-using-multiple-pngs
title: 'Fruit Plot: Plotting Using Multiple PNGs'
wordpress_id: 989
categories:
- R Project
---

In one of our previous posts ([Halloween: An Excuse for Plotting with Icons](http://citizen-statistician.org/2015/10/27/halloween-an-excuse-for-plotting-with-icons/)), we gave a quick tutorial on how to plot using icons using ggplot. A reader, Dr. D. K. Samuel asked in a comment how to use multiple icons. His comment read,


<blockquote>...can you make a blog post on using multiple icons for such data
year, crop,yield
1995,Tomato,250
1995,Apple,300
1995,Orange,500
2000, Tomato,600
2000,Apple, 800
2000,Orange,900
it will be nice to use icons for each data point. It will also be nice if the (icon) data could be colored by year.</blockquote>


This blog post will address this request. First, the result...

[![fruit-plot](http://citizen-statistician.org/wp-content/uploads/2015/10/fruit-plot1.png)](http://citizen-statistician.org/wp-content/uploads/2015/10/fruit-plot1.png)

The process I used to create this plot is as follows:



	
  1. **Find the icons that you want to use in place of the points on your scatterplot (or dot plot).**


I used an apple icon (created by [Creative Stall](https://thenounproject.com/creativestall)), an orange icon (created by [Gui Zamarioli](https://thenounproject.com/guiez)), and a tomato icon (created by [Andrey Vasiliev](https://thenounproject.com/andvasiliev)); all obtained from [The Noun Project](https://thenounproject.com/).



	
  2. **Color the icons.**


After downloading the icons, I used [Gimp](http://www.gimp.org/), a free image manipulation program, to color each of the icons. I created a green version, and a blue version of each icon. (The request asked for the two different years to have different colors.) I also cropped the icons.

Given that there were only three icons, doing this manually was not much of a time burden (10 minutes after I selected the color palette—using [colorbrewer.org](http://colorbrewer2.org/)). Could this be done programatically? I am not sure. A person, who is not me, might be able to write some commands to do this with [ImageMagick](http://www.imagemagick.org/script/index.php) or some other program. You might also be able to do this in R, but I sure don't know how...I imagine it involves re-writing the values for the pixels you want to change the color of, but how you determine which of those you want is beyond me.

If you are interested in only changing the color of the icon outline, an alternative would be to download the SVGs rather than the PNGs. Opening the SVG file in a text editor gives the underlying syntax for the SVG. For example, the apple icon looks like this:

[code language="html"]
<svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" version="1.1" x="0px" y="0px" viewBox="0 0 48 60" enable-background="new 0 0 48 48" xml:space="preserve">
  <g>
    <path d="M19.749,48c-1.662... />
    <path d="M24.001,14.866c-0.048, ... />
    <path d="M29.512, ... />
  </g>
<text x="0" y="63" fill="#000000" font-size="5px" font-weight="bold" font-family="'Helvetica Neue', Helvetica, Arial-Unicode, Arial, Sans-serif">Created by Creative Stall</text><text x="0" y="68" fill="#000000" font-size="5px" font-weight="bold" font-family="'Helvetica Neue', Helvetica, Arial-Unicode, Arial, Sans-serif">from the Noun Project</text>
</svg>
[/code]

The three path commands draw the actual apple. The first draws the apple, the second path command draws the leaf on top of the apple, and the third draws the stem. Adding the text, fill="blue" to the end of each path command will change the color of the path from black to blue (see below).

[code language="html"]
<svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" version="1.1" x="0px" y="0px" viewBox="0 0 48 60" enable-background="new 0 0 48 48" xml:space="preserve">
  <g>
    <path d="M19.749,48c-1.662 ... fill="blue" />
    <path d="M24.001,14.866c-0.048, ... fill="blue" />
    <path d="M29.512, ... fill="blue" />
  </g>
<text x="0" y="63" fill="#000000" font-size="5px" font-weight="bold" font-family="'Helvetica Neue', Helvetica, Arial-Unicode, Arial, Sans-serif">Created by Creative Stall</text><text x="0" y="68" fill="#000000" font-size="5px" font-weight="bold" font-family="'Helvetica Neue', Helvetica, Arial-Unicode, Arial, Sans-serif">from the Noun Project</text>
</svg>
[/code]

This could easily be programmatically changed. Then the SVG images could also programmatically be exported to PNGs.



	
  3. **Read in the icons (which are PNG files).**


Here we use the `readPNG()` function from the **png** library to bring the icon into R.

[code language="r"]
library(png)
blue_apple = readPNG("~/Desktop/fruit-plot/blue_apple.png", TRUE)
green_apple = readPNG("~/Desktop/fruit-plot/green_apple.png", TRUE)
blue_orange = readPNG("~/Desktop/fruit-plot/blue_orange.png", TRUE)
green_orange = readPNG("~/Desktop/fruit-plot/green_orange.png", TRUE)
blue_tomato = readPNG("~/Desktop/fruit-plot/blue_tomato.png", TRUE)
green_tomato = readPNG("~/Desktop/fruit-plot/green_tomato.png", TRUE)
[/code]




	
  4. **Create the data.**


Use the `data.frame()` function to create the data.

[code language="r"]
plotData = data.frame(
&nbsp; year = c(1995, 1995, 1995, 2000, 2000, 2000),
&nbsp; crop = c("tomato", "apple", "orange", "tomato", "apple", "orange"),
&nbsp; yield = c(250, 300, 500, 600, 800, 900)
)

plotData
  year   crop yield
1 1995 tomato   250
2 1995  apple   300
3 1995 orange   500
4 2000 tomato   600
5 2000  apple   800
6 2000 orange   900
[/code]

Next we will add a column to our data frame that maps the year to color. This uses the `ifelse()` function. In this example, if the logical statement `plotData$year == 1995` evaluates as TRUE, then the value will be "blue". If it evaluates as FALSE, then the value will be "green".

[code language="r"]
plotData$color = ifelse(plotData$year == 1995, "blue", "green")

plotData
  year   crop yield color
1 1995 tomato   250  blue
2 1995  apple   300  blue
3 1995 orange   500  blue
4 2000 tomato   600 green
5 2000  apple   800 green
6 2000 orange   900 green
[/code]

Now we will use this new "color" column in conjunction with the "crop" column to identify the icon that will be plotted for each row. the `paste0()` function concatenates each argument together with no spaces between them. Here we are concatenating the color value, an underscore, and the crop value.

[code language="r"]
plotData$icon = paste0(plotData$color, "_", plotData$crop)

plotData
  year   crop yield color         icon
1 1995 tomato   250  blue  blue_tomato
2 1995  apple   300  blue   blue_apple
3 1995 orange   500  blue  blue_orange
4 2000 tomato   600 green green_tomato
5 2000  apple   800 green  green_apple
6 2000 orange   900 green green_orange
[/code]




	
  5. **Use ggplot to create a scatterplot of the data, making the size of the points 0.**



[code language="r"]
library(ggplot2)

p = ggplot(data = plotData, aes(x = year, y = yield)) +
  geom_point(size = 0) +
  theme_bw() +
  xlab("Year") +
  ylab("Yield")
[/code]


	
  6. **Use a for() loop to add annotation_custom() layers (one for each point) that contain the image.
**


Similar to the [previous post](http://citizen-statistician.org/2015/10/27/halloween-an-excuse-for-plotting-with-icons/), we add new layers (in our case each layer will be an additional point) by recursively adding the layer and then writing this into `p.` The key is that the image name is now in the "icon" column of the data frame. The values in the "icon" column are character data. To make R treat these as objects we first parse the character data using the `parse()` function, and then we use `eval()` to have R evaluate the parsed expression. A description of this appears in [this Stack Overflow question](http://stackoverflow.com/questions/1743698/r-eval-expression).

[code language="r"]
library(grid)

for(i in 1:nrow(plotData)){
  p = p + annotation_custom(
    rasterGrob(eval(parse(text = plotData$icon[i]))),
    xmin = plotData$year[i] - 20, xmax = plotData$year[i] + 20, 
    ymin = plotData$yield[i] - 20, ymax = plotData$yield[i] + 20
  )
} 

# Show plot
print(p)
[/code]




	
  7. **Some issues to consider and my alternative plot.
**


I think that plot is what was requested, but since I cannot help myself, I would propose a few changes that I think would make this plot better. First, I would add lines to connect each fruit (apple in 1995 to apple in 2000). This would help the reader to better track the change in yield over time.

Secondly, I would actually leave the fruit color constant across years and vary the color between fruits (probably coloring them according to their real-world colors). This again helps the reader in that they can more easily identify the fruits and also helps them track the change in yield. (It also avoids a Stroop-like effect of coloring an orange some other color than orange!)

Here is the code:

[code language="r"]
# Read in PNG files
apple = readPNG("~/Desktop/fruit-plot/red_apple.png", TRUE)
orange = readPNG("~/Desktop/fruit-plot/orange_orange.png", TRUE)
tomato = readPNG("~/Desktop/fruit-plot/red_tomato.png", TRUE)

# Plot
p2 = ggplot(data = plotData, aes(x = year, y = yield)) +
  geom_point(size = 0) +
  geom_line(aes(group = crop), lty = "dashed") +
  theme_bw()  +
  xlab("Year") +
  ylab("Yield") +
  annotate("text", x = 1997, y = 350, label = "Tomato created by Andrey Vasiliev from the Noun Project", size = 2, hjust = 0) +
  annotate("text", x = 1997, y = 330, label = "Apple created by Creative Stall from the Noun Project", size = 2, hjust = 0) +
  annotate("text", x = 1997, y = 310, label = "Orange created by Gui Zamarioli from the Noun Project", size = 2, hjust = 0)

for(i in 1:nrow(plotData)){
  p2 = p2 + annotation_custom(
    rasterGrob(eval(parse(text = as.character(plotData$crop[i])))),
    xmin = plotData$year[i] - 20, xmax = plotData$year[i] + 20, 
    ymin = plotData$yield[i] -20, ymax = plotData$yield[i]+20
  )
}

# Show plot
print(p2)
[/code]

And the result...

[![fruit-plot2](http://citizen-statistician.org/wp-content/uploads/2015/10/fruit-plot2.png)](http://citizen-statistician.org/wp-content/uploads/2015/10/fruit-plot2.png)
