---
author: andy
comments: true
date: 2015-10-27 13:39:47+00:00
layout: post
link: http://citizen-statistician.org/2015/10/27/halloween-an-excuse-for-plotting-with-icons/
slug: halloween-an-excuse-for-plotting-with-icons
title: 'Halloween: An Excuse for Plotting with Icons'
wordpress_id: 979
categories:
- R Project
- Teaching
---

In my course on the GLM, we are discussing residual plots this week. Given that it is also Halloween this Saturday, it seems like a perfect time to code up a residual plot made of ghosts.

[![Ghost plot](http://citizen-statistician.org/wp-content/uploads/2015/10/Rplot.png)](http://citizen-statistician.org/wp-content/uploads/2015/10/Rplot.png)The process I used to create this plot is as follows:



	
  1. **Find an icon that you want to use in place of the points on your scatterplot (or dot plot).**


I used a ghost icon (created by [Andrea Mazzini](https://thenounproject.com/andreamazz)) obtained from [The Noun Project](https://thenounproject.com/). After downloading the icon, I used Preview to create a new PNG file that had cut out the citation text in the downloaded image. I will add the citation text at a later stage in the plot itself. This new icon was 450x450 pixels.



	
  2. **Use ggplot to create a scatterplot of a set of data, making the size of the points 0.**


Here is the code that will create the data and make the plot that I used.

[code language="r"]
plotData = data.frame(
  .fitted = c(76.5, 81.3, 75.5, 79.5, 80.1, 78.5, 79.5, 77.5, 81.2, 80.4, 78.1, 79.5, 76.6, 79.4, 75.9, 86.6, 84.2, 83.1, 82.4, 78.4, 81.6, 79.6, 80.4, 82.3, 78.6, 82.1, 76.6, 82.1, 87, 82.2, 82.1, 87.2, 80.5, 84.9, 78.5, 79, 78.5, 81.5, 77.4, 76.8, 79.4, 75.5, 80.2, 80.4, 81.5, 81.5, 80.5, 79.2, 82.2, 83, 78.5, 79.2, 80.6, 78.6, 85.9, 76.5, 77.5, 84.1, 77.6, 81.2, 74.8, 83.4, 80.4, 77.6, 78.6, 83.3, 80.4, 80.5, 80.4, 83.8, 85.1, 82.2, 84.1, 80.2, 75.7, 83, 81.5, 83.1, 78.3, 76.9, 82, 82.3, 85.8, 78.5, 75.9, 80.4, 82.3, 75.7, 73.9, 80.4, 83.2, 85.2, 84.9, 80.4, 85.9, 76.8, 83.3, 80.2, 83.1, 77.6),
  .stdresid = c(0.2, -0.3, 0.5, 1.4, 0.3, -0.2, 1.2, -1.1, 0.7, -0.1, -0.3, -1.1, -1.5, -0.1, 0, -1, 1, 0.3, -0.5, 0.5, 1.8, 1.6, -0.1, -1.3, -0.2, -0.9, 1.1, -0.2, 1.5, -0.3, -1.2, -0.6, -0.4, -3, 0.5, 0.3, -0.8, 0.8, 0.5, 1.3, 1.8, 0.5, -1.6, -2, -2.1, -0.8, 0.4, -0.9, 0.4, -0.4, 0.6, 0.4, 1.4, -1.4, 1.3, 0.4, -0.8, -0.2, 0.5, 0.7, 0.5, 0.1, 0.1, -0.8, -2.1, 0, 1.9, -0.5, -0.1, -1.4, 0.6, 0.7, -0.3, 1, -0.7, 0.7, -0.2, 0.8, 1.3, -0.7, -0.4, 1.5, 2.1, 1.6, -1, 0.7, -1, 0.9, -0.3, 0.9, -0.3, -0.7, -0.9, -0.2, 1.2, -0.8, -0.9, -1.7, 0.6, -0.5)
  )

library(ggplot2)

p = ggplot(data = plotData, aes(x = .fitted, y = .stdresid)) +
    theme_bw() + 
    geom_hline(yintercept = 0) +
    geom_point(size = 0) +
    theme_bw() +
    xlab("Fitted values") +
    ylab("Standarized Residuals") +
    annotate("text", x = 76, y = -3, label = "Ghost created by Andrea Mazzini from Noun Project")
[/code]


	
  3. **Read in the icon (which is a PNG file).**


Here we use the `readPNG()` function from the **png** library to bring the icon into R.

[code language="r"]
library(png)
ghost = readPNG("/Users/andrewz/Desktop/ghost.png", TRUE)
[/code]




	
  4. **Use a for() loop to add annotation_custom() layers (one for each point) that contain the image.
**


The idea is that since we have saved our plot in the object `p`, we can add new layers (in our case each layer will be an additional point) by recursively adding the layer and then writing this into `p.` The pseudo-like code for this is:

[code language="r"]
for(i in 1:nrow(plotData)){
    p = p + 
      annotation_custom(
        our_image,
        xmin = minimum_x_value_for_the_image, 
        xmax = maximum_x_value_for_the_image, 
        ymin = minimum_y_value_for_the_image, 
        ymax = maximum_y_value_for_the_image
        ) 
    }
[/code]

In order for the image to be plotted, we first have to make it plot-able by making it a graphical object, or GROB.

The `rasterGrob()` function (found in the **grid,/b> package) renders a bitmap image (raster image) into a graphical object or GROB which can then be displayed at a specified location, orientation, etc. Read more about using [Raster images in R here](https://journal.r-project.org/archive/2011-1/RJournal_2011-1_Murrell.pdf).**

The arguments `xmin`, `xmax`, `ymin`, and `ymax` give the horizontal and vertical locations (in data coordinates) of the raster image. In our residual plot, we want the center of the image to be located at the coordinates (`.fitted`, `.stdresid`). In the syntax below, we add a small bit to the maximum values and subtract a small bit from the minimum values to force the icon into a box that will plot the icons a bit smaller than their actual size. (#protip: play around with this value until you get a plot that looks good.)

[code language="r"]
library(grid)

for(i in 1:nrow(plotData)){
    p = p + annotation_custom(
      rasterGrob(ghost),
      xmin = plotData$.fitted[i]-0.2, xmax = plotData$.fitted[i]+0.2, 
      ymin = plotData$.stdresid[i]-0.2, ymax = plotData$.stdresid[i]+0.2
      ) 
    }
[/code]

Finally we print the plot to our graphics device using

[code language="r"]
print(p)
[/code]

And the result is eerily pleasant!
