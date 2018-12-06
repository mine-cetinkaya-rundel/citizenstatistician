---
author: andy
comments: true
date: 2013-11-25 14:10:21+00:00
layout: post
link: http://citizen-statistician.org/2013/11/25/ranked-choice-voting/
slug: ranked-choice-voting
title: Ranked Choice Voting
wordpress_id: 736
categories:
- pret-a-porter
- R Project
---

The city of Minneapolis recently elected a new mayor. This is not newsworthy in and of itself, however the method they used was—ranked choice voting. Ranked choice voting is a method of voting allowing voters to rank multiple candidates in order of preference. In the Minneapolis mayoral election, voters ranked up to three candidates.

The interesting part of this whole thing was that it took over two days for the election officials to declare a winner. It turns out that the official procedure for calculating the winner of the ranked-choice vote involved cutting and pasting spreadsheets in Excel.

The technology coordinator at [E-Democracy](http://forums.e-democracy.org), Bill Bushey, posted the challenge of writing a program to calculate the winner of a ranked-choice election to the Twin Cities Javascript and Python meetup groups. Winston Chang also posted it to the Twin Cities R Meetup group. While not a super difficult problem, it is complicated enough that it can make for a nice project—especially for new R programmers. (In fact, our student R group is doing this.)

The algorithm, described by Bill Bushey, is



	
  1. Create a data structure that represents a ballot with voters' 1st, 2nd, and 3rd choices

	
  2. Count up the number of 1st choice votes for each candidate. If a candidate has 50% + 1 votes, declare that candidate the winner.

	
  3. Else, select the candidate with the lowest number of 1st choice votes, remove that candidate completely from the data structure, make the 2nd choice of any voter who voted for the removed candidate the new 1st choice (and the old 3rd choice the new 2nd choice).

	
  4. Goto 2


As an example consider the following sample data:

    
    Voter  Choice1  Choice2  Choice3
        1    James     Fred    Frank
        2    Frank     Fred    James
        3    James    James    James
        4    Laura 
        5    David 
        6    James              Fred
        7    Laura
        8    James
        9    David    Arnie
       10    David


In this data, James has the most 1st choice votes (4) but it is not enough to win the election (a candidate needs 6 votes = 50% of 10 votes cast + 1 to win). So at this point we determine the least voted for candidate…Frank, and delete him from the entire structure:

    
    Voter  Choice1  Choice2  Choice3
        1    James     Fred    <del>Frank</del>
        2    <del>Frank</del>     Fred    James
        3    James    James    James
        4    Laura 
        5    David 
        6    James              Fred
        7    Laura
        8    James
        9    David    Arnie
       10    David


Then, the 2nd choice of any voter who voted for Frank now become the new "1st" choice. This is only Voter #2 in the sample data. Thus Fred would become Voter #2's 1st choice and James would become Voter #2's 2nd choice:

    
    Voter  Choice1  Choice2  Choice3
        1    James     Fred
        2     Fred    James
        3    James    James    James
        4    Laura 
        5    David 
        6    James              Fred
        7    Laura
        8    James
        9    David    Laura
       10    David


James still has the most 1st choice votes, but not enough to win (he still needs 6 votes!). Fred has the fewest 1st choice votes, so he is eliminated, and his voter's 2nd and 3rd choices are moved up:

    
    Voter  Choice1  Choice2  Choice3
        1    James
        2    James
        3    James    James    James
        4    Laura 
        5    David 
        6    James              
        7    Laura
        8    James
        9    David    Laura
       10    David


James now has five 1st choice votes, but still not enough to win. Laura has the fewest 1st choice votes, so she is eliminated, and her voter's 2nd and 3rd choices are moved up:

    
    Voter  Choice1  Choice2  Choice3
        1    James
        2    James
        3    James    James    James
        4     
        5    David 
        6    James              
        7    
        8    James
        9    David    Laura
       10    David


James retains his lead with five first place votes…but now he is declared the winner. Since Voter #4 and #7 do not have a 2nd or 3rd choice vote, they no longer count in the number of voters. Thus to win, a candidate only needs 5 votes = 50% of the 8 1st choice votes + 1.

The actual data from Minneapolis includes over 80,000 votes for 36 different candidates. There are also ballot issues such as undervoting and overvoting. This occurs when voters give multiple candidates the same ranking (overvoting) or do not select a candidate (undervoting).

The animated GIF below shows the results after each round of elimination for the Minneapolis mayoral election.

[![2013 Mayoral Race](http://citizen-statistician.org/wp-content/uploads/2013/11/animation.gif)](http://citizen-statistician.org/wp-content/uploads/2013/11/animation.gif)

The [Minneapolis mayoral data is available on GitHub](https://github.com/tcrug/ranked-choice-vote-data) as a CSV file (along with some other smaller sample files to hone your programming algorithm). There is also a [frequently asked questions webpage available from the City of Minneapolis](http://vote.minneapolismn.gov/rcv/what-is-rcv) regarding ranked choice voting.

In addition you can also [listen to the Minnesota Public Radio broadcast](http://minnesota.publicradio.org/display/web/2013/11/22/politics/ranked-choice-vote-count-programmers) in which they discussed the problems with the vote counting. The folks at the  R Users Group Meeting were featured and Winston brought the house down when commuting on the R program that computed the winner within a few seconds said, "it took me about an hour and a half to get something usable, but I was watching TV at the time".

See the [R syntax I used here](http://citizen-statistician.org/2013/11/30/r-syntax-for-ranked-choice-voting/).


