---
author: citizenstat
comments: true
date: 2017-07-26 22:15:47+00:00
layout: post
link: http://citizen-statistician.org/2017/07/26/structuring-data-in-middle-school/
slug: structuring-data-in-middle-school
title: Structuring Data in Middle School
wordpress_id: 1140
categories:
- Data
- Teaching
- teaching
---

Of the many provocative and exciting discussions at this year’s Statistics Research Teaching and Learning conference in Rotarua, NZ, one that has stuck in my mind is from Lucia Zapata-Cardona, from the Universidad de Antioquia in Columbia. Lucia discussed data from her classroom observations of a teacher at a middle school (ages 12-13) in a “Northwest Columbian city”. The class was exciting for many reasons, but the reason that I want to write about it here is because of the fact that the teacher had the students structure and store their own data.

The classroom was remarkable – to my American eyes – for the large number of students (45) and for the noise (walls were thin, the playground was immediately outside, and windows were kept open because of the heat.) Despite this, the teacher led an inquiry-based discussion, skillfully prompting the students with questions from the back of the classroom. The discussion lasted over several days.

The students had collected data about the nutritional content of the foods they eat. Challenging students with real-world, meaningful problems is an important part of Prof. Zapata-Cardona’s research, since an important goal of education is to tie the world of the classroom to the real world. Lucia was interested in examining how (and whether) the students constructed and employed statistical models to reason with the data. (Modeling was the theme of this SRTL.) What fascinated me wasn't the modeling, but the role that the _structure_ of the data played in the students' reasoning.

Students were asked to collect data on the food contained in their lunchboxes so that they could answer the statistical question "How nutritious is the food we bring to school in our lunchbox?" It’s important to note that in Columbia, as Lucia explained to us, the “lunch box” doesn’t contain actual lunch (which the students eat at home), but instead includes snacks for during the day. What interested me was that the teacher let the class, after discussion, decide how they would enter and organize the data. Now I’m not sure what parameters/options the students were given. I do know that the classroom had one computer, and students took turns entering the data into this computer. And I know that the students discussed which variables they wanted to store, and how they wanted to store them.

The pivotal decision here was that the students decided that each row would represent a _food_, for example, _Chicle._ They decided to record information about serving size, calories, fats, carbs, protein, sodium, sugars, whether it was “processed” (5 g, 18, 0, 5, 0, 0, 0 and _si, _in case you were curious). They decided _not_ to store information about how many students brought this food, or how many servings any individual student brought.

At this point, you may have realized that their statistical question is rather difficult, if not impossible, to answer given the format in which they stored the data. Had each case of the data been an individual lunchbox or an individual person, then the students might have made headway. Instead, they stumbled over issues about how to compare the total calories of the dataset with the total calories eaten by individuals. (After much discussion, most of the class “discovered” that the average amount was a good way of summarizing the data, but some of the more perceptive students pointed out that it wasn’t clear what the average really meant.)

Lucia’s forthcoming paper will go into the details about the good and the bad in the students’ statistical reasoning, and the ways in which they used (or failed to use) statistical models. But what was fascinating to me was the opportunity this provided for helping students understand how the structure of data affects the questions that we can ask, and how the questions we ask should first consider the structure of the data.

Too often, particularly in textbooks, there is no opportunity to reason about the structure of data. When a question is asked, the students are given appropriate data, and rarely allowed even to decide which variables to consider (since the provided data usually includes only the necessary variables), much less whether or not the data should be restructured or re-collected.

Another reason classrooms have avoided letting students structure their own data is that many real-life datasets have complicated structures. The data these students collected is really (or should have been) hierarchical. If the case is the lunchbox, a lunchbox is associated with a student and possibly with more than 1 item. If data are collected on multiple days, then there is nesting within days as well as the potential for missing variables or unequal record lengths.

Data with such a complicated structure are simply not taught in middle schools, even though, as Lucia’s case study demonstrates, they arise easily from familiar contexts.   These data are messy and complicated. Should we even open this pandora’s box for middle school students, or should it wait until they are older? Is it enough to work with the simplified “flat” format such as the one these students came up with, and just modify the statistical question? Should students be taught how to manipulate such data into different formats to answer the questions they are interested in?

You might think hierarchical formats are beyond the middle school level, but work done by Cliff Konold and Bill Finzer, in the context of using the CODAP tool, suggests that it is possible. [I can’t find an online paper to link to for this result, but there are some leads [here](https://concord.org/projects/codap#research), and I'm told it has been approved for publication so should appear soon.]

So the question is: when do we teach students to reason with hierarchical data? When do we teach students to recognize that data can be stored in different formats? When do we teach students to convert data from one format to another?

We are back to the question I asked in my last blog: what’s the learning trajectory that takes statistical beginners and teaches them the computational and statistical tools to allow them to address fundamental questions that rely on data that, on the one hand, are complex but on the other hand are found in our day-to-day lives?
