---
author: mine
comments: true
date: 2016-06-25 17:00:51+00:00
layout: post
link: http://citizen-statistician.org/2016/06/25/project-tier/
slug: project-tier
title: Project TIER
wordpress_id: 1034
categories:
- Computation
- Events
- R Project
- statistical software
- Teaching
---

Last year I was awarded a Project TIER (Teaching Integrity in Empirical Research) fellowship, and last week my work on the fellowship wrapped up with a meeting with the project leads, [other fellows from last year](https://www.haverford.edu/project-tier/people/tier-faculty-fellows), as well as [new fellows for the next year](https://www.haverford.edu/sites/default/files/Office/TIER/2016-17-Fellows-List-2016-06-15.pdf). In a nutshell Project TIER focuses on reproducibility. Here is a brief summary of the project's focus from [their website](https://www.haverford.edu/project-tier/about):


<blockquote>For a number of years, we have been developing a protocol for comprehensively documenting all the steps of data management and analysis that go into an empirical research paper. We teach this protocol every semester to undergraduates writing research papers in our introductory statistics classes, and students writing empirical senior theses use our protocol to document their work with statistical data. The protocol specifies a set of electronic files—including data files, computer command files, and metadata—that students assemble as they conduct their research, and then submit along with their papers or theses.</blockquote>


As part of the fellowship, beyond continuing working on integrating reproducible data analysis practices into my courses with the use of literate programming via R Markdown and version control via git/GitHub, I have also created templates two GitHub repositories that follow the Project TIER guidelines: one for use with R and the other with Stata. They both live under the [Project TIER organization on GitHub](https://github.com/ProjectTIER). The idea is that one wishing to follow the folder structure and workflow suggested by Project TIER can make a copy of these repositories and easily organize their work following the TIER guidelines.

There is more work to be done on these of course, first of which is evolving the TIER guidelines themselves to line up better with working with git and R as well as working with tricky data (like large data, or private data, etc.). Some of these are issues the new fellows might tackle in the next year.

As part of the fellowship I also taught a workshop titled _"Making your research reproducible with Project TIER, R, and GitHub"_ to Economics graduate students at Duke. These are students who primarily use Stata so the workshop was a first introduction to this workflow, using the RStudio interface for git and GitHub. Materials for this workshop can be found [here](https://github.com/mine-cetinkaya-rundel/2016-02-12-project-tier-duke). At the end of the workshop I got the sense that very few of these students were interested in making the switch over to R (can't blame them honestly -- if you've been working on your dissertation for years and you just want to wrap it up, the last thing you want to do is to have to rewrite all your code and redo your analysis in a different platform) but quite a few of them were interested in using GitHub for both version control and for showcasing their work publicly.

Also as part of the fellowship [Ben Baumer](http://www.math.smith.edu/~bbaumer/) (a fellow fellow?) and I have organized a session on reproducibility at [JSM 2016](https://www.amstat.org/meetings/jsm/2016/) that I am very much looking forward to. See [here](https://www.amstat.org/meetings/jsm/2016/onlineprogram/ActivityDetails.cfm?SessionID=212538) for the line up.

In summary, being involved with this project was a great eye opener to the fact that there are researchers and educators out there who truly care about issues surrounding reproducibility of data analysis but who are very unlikely to switch over to R because that is not as customary for their discipline (although at least one fellow did after watching my demo on R Markdown in the 2015 meeting, that was nice to see 😁). Discussions around working with Stata made me once again very thankful for R Markdown and RStudio which make literate programming a breeze in R. And what my mean by "a breeze" is "easy to teach to and be adopted by anyone from a novice to expert R user". It seems to me like it would be in the interest of companies like Stata to implement such a workflow/interface to support reproducibility efforts of researchers and educators using their software. I can't see a single reason why they wouldn't invest time (and yes, money) in developing this.

During these discussions a package called [RStata](https://cran.r-project.org/web/packages/RStata/index.html) also came up. This package is _"[a] simple R -> Stata interface allowing the user to execute Stata commands (both inline and from a .do file) from R."_ Looks promising as it should allow running Stata commands from an R Markdown chunk. But it's really not realistic to think students learning Stata for the first time will learn well (and easily) using this R interface. I can't imagine teaching Stata and saying to students "first download R". Not that I teach Stata, but those who do confirmed that it would be an odd experience for students...

Overall my involvement with the fellowship was a great experience for meeting and brainstorming with faculty from non-stats disciplines (mostly from the social sciences) who regularly teach in platforms like Stata and SPSS who are also dedicated to teaching reproducible data analysis practices. I'm often the person who tries to encourage people to switch over to R, and I don't think I'll be stopping doing that anytime soon, but I do believe that if we want all who do data analysis to do it reproducibly, efforts must be made to (1) come up with workflows that ensure reproducibility in statistical software other than R, and (2) create tools that make reproducible data analysis easier in such software (e.g. tools similar to R Markdown designed specifically for these software).



PS: It's been a while since I last posted here, let's blame it on a hectic academic year. I started and never got around to finishing two posts in the past few months that I hope to finish and publish soon. One is about using R Markdown for generating course/TA evaluation reports and the other is on using Slack for managing TAs for a large course. Stay tuned.

PPS: Super excited for #useR2016 starting on Monday. The lack of axe-throwing will be disappointing (those who attended useR 2015 in Denmark know what I'm talking about) but otherwise the [schedule](http://schedule.user2016.org/) promises a great line up!
