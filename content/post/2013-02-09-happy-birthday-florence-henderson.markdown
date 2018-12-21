---
author: andy
comments: true
date: 2013-02-09 22:53:16+00:00
layout: post
link: http://citizen-statistician.org/2013/02/09/happy-birthday-florence-henderson/
slug: happy-birthday-florence-henderson
title: Happy Birthday Florence Henderson
wordpress_id: 404
categories:
- rstats
---

As a celebration of Florence Henderson's 79th birthday (on February 14), I have created this scatterplot to use in my regression course.


[![ValDay](http://citizen-statistician.org/wp-content/uploads/2013/02/ValDay-300x225.jpg)](http://citizen-statistician.org/wp-content/uploads/2013/02/ValDay.jpg)


The plot depicts the relationship between time spent on mathematics homework outside of school (expressed as z-scores) and mathematics achievement scores (expressed as T-scores, _M_=50, _SD_=10) for 200 8th-graders taken from the 1988 [National Education Longitudinal Study](http://nces.ed.gov/surveys/nels88/). The color–in a display of very poor data science–is just randomly applied to the observations rather than meaning anything substantial. (Bloggers Note: I think it fits with the spirit of Valentine's Day...a gratuitous, yet meaningless, gesture intended to make the receiver feel all gooshy.)

I created the plot using the **Valentine** package (available [here](https://github.com/zief0002/Valentine)) which applies a Valentine's Day theme to ggplot. I also applied a picture of Cupid into the background of the plot and used hearts instead of points to plot the observations. Lastly, I changed the default color and fill on the regression smoother to more aptly fit the color scheme.

Below I will explain the how-to of creating this plot.


# Reading in the NELS Data


First, I read the NELS data into R. These data and its codebook are available via my [regression course website](http://www.tc.umn.edu/~zief0002/8262.php).

```
nels <- read.csv("http://www.tc.umn.edu/~zief0002/Data/NELS.csv")
```

# Using Hearts Instead of Points


I first needed to find an image of a heart that I liked. For icons of all sorts, I generally use [The Noun Project](http://thenounproject.com). (This particular heart can be found [here](http://thenounproject.com/noun/heart/#icon-No187).) All of the images at The Noun Project are [SVG](http://en.wikipedia.org/wiki/Scalable_Vector_Graphics) files. This makes them very useful for display in browsers. To use them in ggplot, I converted the SVG image to a [PNG](http://en.wikipedia.org/wiki/Portable_Network_Graphics) file using the free image manipulation program [GIMP](http://www.gimp.org) (Perhaps you can use the SVG format directly without converting it, but I have never done that, so I don't know.)

Using GIMP, I also replaced the black color to the hexadecimal color "ad97c6" by selecting **Color > Map > Color Exchange**. (Double-clicking the color swatch under "To Color" allows for color entry in hexadecimal.) After this I saved the heart as "heart1.png", and repeated the process four more times, but using the colors "e58cbc" (_heart2.png_), "f2935b" (_heart3.png_), "9fc8b6" (_heart4.png_), and "eddc74" (_heart5.png_). (Note: These colors are the same colors I chose for the Valentine's Day theme color and fill palettes and are based on the colors of the candy hearts you get in elementary school.)

I then used the **png** package to read the five PNG files into R. (Note: For anyone who doesn't want to go through the hassle of coloring the hearts and reformatting both them and Cupid, I have made those files available for download [here](https://github.com/zief0002/Public-Stuff/tree/master/Hearts%20and%20Cupid).)

```
library(png)
h1 <- readPNG("/Users/andrewz/Desktop/heart1.png", TRUE)
h2 <- readPNG("/Users/andrewz/Desktop/heart2.png", TRUE)
h3 <- readPNG("/Users/andrewz/Desktop/heart3.png", TRUE)
h4 <- readPNG("/Users/andrewz/Desktop/heart4.png", TRUE)
h5 <- readPNG("/Users/andrewz/Desktop/heart5.png", TRUE)
```

To randomly assign each observation to one of the five hearts (h1–h5), I used the `sample()` function inside the `paste()` function to concatenate the letter "h" and a random value from 1–5. I then used the `do()` function from the **mosaic** package to "do" this 200 times. Lastly, I appended this vector to the `nels` data frame, in the process, coercing it to characters (to be sure it isn't appended as a factor–which will be needed later for use in the `get()` function).

```
library(mosaic)
heart <- do(200) * paste("h", sample(1:5, size = 1), sep="")
nels$Heart <- as.character(heart[, 1])
head(nels)
#  ID   Homework   Math Heart
#1  1 -0.3329931 42.432    h4
#2  2 -0.2136822 53.698    h2
#3  3 -1.0077991 49.205    h2
#4  4  0.2059000 53.698    h1
#5  5 -0.1177185 55.980    h5
#6  6  0.1413540 65.331    h3
```

This is all that is needed until we get to actually creating the plot.


# Adding a Cupid into the Plot's Background


I obtained the image of Cupid by doing a Google search on "Cupid, Public Domain". (The actual image I used is available [here](http://graphicsfairy.blogspot.com/2012/01/vintage-clip-art-poems-of-love.html).) Since the image was a JPEG, I again converted the image to a PNG (this time using Preview) and changed the image size to have a width of 800 pixels. I also used the _Instant Alpha_ tool in Preview's toolbar to make the white background transparent. As a sidebar, this could all be done in GIMP as well.

I again used the readPNG() function to read the image file into R, but this time setting the native= argument to FALSE. This will represent the image as an array rather than rasterizing it. I chose to do this so that I could make the image more transparent before rasterizing it.

```
cupid <- readPNG("/Users/andrewz/Desktop/cupid.png", FALSE)
w <- matrix(rgb(cupid[ , , 1], cupid[ , , 2], cupid[ , , 3], cupid[ , , 4] * 0.2), nrow = dim(cupid)[1])
```

# Creating the Plot

Finally, we are ready to create the plot. In the initial calls to ggplot, I use the rasterGrob() function from the grid package to rasterize Cupid which is placed in the plot using the annotation_custom() layer. The color= and fill= arguments to the geom_smooth() layer set the beautiful magenta/pink color for the regression smoother. The theme_valentine() layer sets ggplot's theme to use some specialized fonts (see the [Valentine package on GitHub](https://github.com/zief0002/Valentine)). The size of the points in the geom_point() layer is set to 0, to leave a blank canvas for us to add our hearts. This is assigned into the object p.

```
library(ggplot2)
library(grid)
library(Valentine)
p <- ggplot(data = nels, aes(x = Homework, y = Math)) +
	geom_point(size = 0) +
	annotation_custom(rasterGrob(w)) +
	theme_valentine() +
	geom_smooth(method = "lm", color = "#ec008c", fill = "#ec008c", lwd = 1.5) +
	ggtitle("HAPPY BIRTHDAY FLORENCE HENDERSON")
```

The hearts (points) are now added to the plot by cycling through a for loop. Each time we are going to rasterize the heart and add it to the plot. The optional arguments in the annotation_custom() layer set the horizontal and vertical position of the hearts in the plot.

```
for(i in 1:nrow(nels)){
    p <- p + annotation_custom(
      rasterGrob(get(nels$Heart[i])), 
      xmin = nels$Homework[i] - 0.5, xmax = nels$Homework[i] + 0.5, ymin = nels$Math[i] - 0.5, ymax = nels$Math[i] + 0.5
      ) 
    }
```
