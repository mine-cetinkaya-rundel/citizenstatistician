---
author: citizenstat
comments: true
date: 2013-10-07 15:27:47+00:00
layout: post
link: http://citizen-statistician.org/2013/10/07/statistics-the-government-shutdown-and-causality/
slug: statistics-the-government-shutdown-and-causality
title: Statistics, the government shutdown, and causality.
wordpress_id: 702
categories:
- Musings
- Teaching
---

There's a  statistical meme that is making its way into pundits' discussions (as we might politely call them) that is of interest to statistics educators.  There are several variations, but the basic theme is this:  because of the government shutdown, people are unable to benefit from the new drugs they receive by participating in clinical trials.  The L.A Times went so far as to publish an editorial from a gentleman who claimed that he was cured by his participation in a clinical trial.

Now if they had said that _future_ patients are prevented from benefiting from what is learned from a clinical trial, then they'd nail it.  Instead, they seem to be overlooking the fact that some patients will be randomized to the control group, and probably get the same treatment as if there were no trial at all.  And in many trials (a majority?), the result will be that the experimental treatment had little or no effect beyond the traditional treatment.  And in a very small number of cases, the experimental effect will be found to have serious side effects.  And so the pundits should really be telling us that the government shutdown prevents patients from a small probability of a benefitting from experimental treatment.

All snarkiness aside, I think the prevalence of this meme points to the subtleties of interpreting probabilistic experiments, in which outcomes contain much variability, and so conclusions must be stated in terms of group characteristics.  This came out in the SRTL discussion in Minnesota this summer, when Maxinne Pfannkuch, Pip Arnold, and Stephanie Budgett at the University of Auckland  presented their work leading towards a framework for describing students' understanding of causality.  I don't remember very well the example they used, but it was similar to this (and was a real-life study):   patients were randomized to receive either fish oil or vegetable oil in their diet.  The goal of the study was to determine if fish oil lowered cholesterol.  At the end of the study, the fish oil group had a slightly lower _average_ cholesterol levels.  A typical interpretation was, "If I take fish oil, my cholesterol will go down."

One problem with this interpretation is that it ignored the within-group variation.  Some of patients in the fish oil group saw their cholesterol go up; some saw little or no change.  The study's conclusion is about group means, not about individuals.  (There were other problems, too.  This interpretation ignores the existence of the control group: we don't really know if fish oil improves cholesterol compared to your current diet; we know only that it tends to go down in comparison to a vegetable-oil diet.  Also, we know the effects only for those who participated in the study. We assume they were not special people, but possibly the results won't hold for other groups.)

Understanding causality in probabilistic settings (or any setting) is a challenge for young students and even adults.  I'm very excited to see such a distinguished group of researchers begin  to help us understand.  [Judea Pearl](http://bayes.cs.ucla.edu/jp_home.html), at UCLA, has done much to encourage statisticians to think about the importance of teaching causal inference.  Recently, he helped the American Statistical Association establish the [Causality in Statistics Education prize](http://www.amstat.org/education/causalityprize/), won this year by Felix Elwert, a sociologist at the University of Wisconsin-Madison.  We still have a ways to go before we understand how to best teach this topic at the undergraduate level and even further before we understand how to teach it at earlier levels.  But, as the government shut down has shown, understanding probabilistic causality is an important component of statistical literacy.
