---
author: mine
comments: true
date: 2015-09-17 04:42:53+00:00
layout: post
link: http://citizen-statistician.org/2015/09/17/til-what-happens-if-you-use-instead-of-in-ggplot2/
slug: til-what-happens-if-you-use-instead-of-in-ggplot2
title: TIL what happens if you use %>% instead of + in ggplot2
wordpress_id: 953
categories:
- Computation
- R Project
---

This post is about `ggplot2` and `dplyr` packages, so let's start with loading them:

```
library(ggplot2) 
library(dplyr) 
```

I can't be the first person to make the following mistake:

```
ggplot(mtcars, aes(x = wt, y = mpg)) %>%
    geom_point() 
```

Can you spot the mistake in the code above? Look closely at the end of the first line.

The operator should be the `+` used in `ggplot2` for layering, not the `%>%` operator used in `dplyr` for piping, like this:

```
ggplot(mtcars, aes(x = wt, y = mpg)) +
    geom_point() 
```

So what happens if you accidentally use the pipe operator instead of the `+`? You get the following error:

```    
Error in get(x, envir = this, inherits = inh)(this, ...) : 
 Mapping should be a list of unevaluated mappings created by aes or aes_string
```

My Google search for this error did not yield my careless mistake as a potential cause. Since many people use these two packages together, I'm guessing such mix-up of operators can't be too uncommon (right? I can't be the only one...). So I'm leaving this post here for the next person who makes the same mistake.
