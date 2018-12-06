---
author: mine
comments: true
date: 2014-01-09 15:22:04+00:00
layout: post
link: http://citizen-statistician.org/2014/01/09/conditional-probabilities-and-kitties/
slug: conditional-probabilities-and-kitties
title: Conditional probabilities and kitties
wordpress_id: 766
categories:
- Musings
- teaching
tags:
- conditional probability
---

I was at the vet yesterday, and just like with any doctor's visit experience, there was a bit of waiting around -- time for re-reading all the posters in the room.

[![vodka](http://citizen-statistician.org/wp-content/uploads/2014/01/vodka-e1389280841663-1024x768.jpg)](http://citizen-statistician.org/wp-content/uploads/2014/01/vodka.jpg)

And this is what caught my eye on the information sheet about feline heartworm (I'll spare you the images):

[![cond](http://citizen-statistician.org/wp-content/uploads/2014/01/cond-1024x409.jpg)](http://citizen-statistician.org/wp-content/uploads/2014/01/cond.jpg)

The question asks: _"My cat is indoor only. Is it still at risk?" _

The way I read it, this question is asking about the risk of an indoor only cat being heartworm positive. To answer this question we would want to know P(heartworm positive | indoor only).

However the answer says: _"A recent study found that 27% of heartworm positive cats were identified as exclusively indoor by their owners"_, which is P(indoor only | heartworm positive) = 0.27.

Sure, this gives us some information, but it doesn't actually answer the original question. The original question is asking about the reverse of this conditional probability.

When we talk about Bayes' theorem in my class and work through examples about sensitivity and specificity of medical tests, I always tell my students that doctors are actually pretty bad at these, looks like I'll need to add vets to my list too!
