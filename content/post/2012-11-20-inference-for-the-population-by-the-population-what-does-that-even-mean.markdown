---
author: mine
comments: true
date: 2012-11-20 04:22:54+00:00
layout: post
link: http://citizen-statistician.org/2012/11/20/inference-for-the-population-by-the-population-what-does-that-even-mean/
slug: inference-for-the-population-by-the-population-what-does-that-even-mean
title: Inference for the population by the population -- what does that even mean?
wordpress_id: 204
categories:
- hunting and gathering
- Teaching
- teaching
---

In an effort to integrate more hands on data analysis in my introductory statistics class, I've been assigning students a project early on in the class where they answer a research question of interest to them using a hypothesis test and/or confidence interval. One goal of this project is getting the students to decide which methods to use in which situations, and how to properly apply them. But there's more to it -- students  define their own research question and find an appropriate dataset to answer that question with. The analysis and findings are then presented in a cohesive research paper.

Settling on a research question that can be answered using limited methods (one or two mean or proportion testing, ANOVA, or chi-square) is the first half of the battle. Some of the research questions students come up with require methods much more involved than simple hypothesis testing or parameter estimation. These students end up having to dial back and narrow down the focus of the research topic to meet the assignment guidelines. I think that this is a useful exercise as it helps them evaluate what they have and have not learned.

The next step is finding data, and this can be quite time consuming. Some students choose research questions about the student body and collect data via in-person surveys at the student center or Facebook polls. A few students even go so far as to conduct experiments on their friends. A huge majority look for data online, which initially appears to be the path of least resistance. However finding raw data that is suitable for statistical inference, i.e. data from a random sample, is not a trivial task.

I (purposefully) do not give much guidance on where to look for data. In the past, even casually mentioning one source has resulted in more than half the class using that source, therefore I find it best to give them free reign during this exploration stage (unless someone is really struggling).

Some students use data from national surveys like the [BRFSS](http://www.cdc.gov/brfss/technical_infodata/surveydata.htm) or the [GSS](http://www3.norc.org/GSS+Website/Download/). The data come from a (reasonably) representative sample, and are a perfect candidate for applying statistical inference methods. One problem with such data is that they rarely come in plain text format (SAS, SPSS, etc.), and importing such data into R can be a challenge for novice R users, even with step-by-step instructions.

On the other hand, many students stumble upon the resources like [World Bank Database](http://data.worldbank.org/indicator), [OECD](http://www.oecd.org/statistics/), the [US Census](http://factfinder2.census.gov/faces/nav/jsf/pages/index.xhtml), etc., where data are presented in much more user friendly formats. The drawback is that these are essentially population data, e.g. country indicators like [human development index](http://hdr.undp.org/en/media/HDR_2011_EN_Tables.pdf) for _all_ countries, and there is really no need for hypothesis testing or parameter estimation when the parameter is already known. To complicate matters further, some of the tables presented are not really ``raw data" but instead summary tables, e.g. median household income for all states calculated based on random sample data from each state.

One obvious way to avoid this problem is to make the assignment stricter by requiring that chosen data must come from a (reasonably) random sample. However, this stricter rule would give students much less freedom in the research question they can investigate, and the projects tend to be much more engaging and informative when students write about something they genuinely care about.

Limiting data sources also have the effect of increasing the time spent finding data, and hence decreasing the time students spend actually analyzing the data and writing up results. Providing a list of resources for curated datasets (e.g. [DASL](http://lib.stat.cmu.edu/DASL/)) would certainly diminish time spent looking for data, but I would argue that the learning that happens during the data exploration process is just as valuable (if not more) than being able to conduct a hypothesis test.

Another approach (one that I have been taking) is allowing the use population data but requiring a discussion of why it is actually not necessary to do statistical inference in these circumstances. This approach lets the students pursue their interests, but interpretations of p-values and confidence intervals calculated based on data from the entire population can get quite confusing. In addition, it has the side-effect of sending the message ``it's ok if you don't meet the conditions, just say so, and carry on." I don't think this is the message we want students to walk away with from an introductory statistics course. Instead, we should be insisting that they don't just blindly carry on with the analysis if conditions aren't met. The ``blindly" part is (somewhat) adressed by the required discussion, but the ``carry on with the analysis" part is still there.

So is this assignment a disservice to students because it might leave some with the wrong impression? Or is it still a valuable experience regardless of the caveats?
