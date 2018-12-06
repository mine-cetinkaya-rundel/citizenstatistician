---
author: andy
comments: true
date: 2013-06-12 19:19:36+00:00
layout: post
link: http://citizen-statistician.org/2013/06/12/tise-network/
slug: tise-network
title: TISE Network
wordpress_id: 566
---

Ever since we wrote an article in which we analyzed the articles which were been published in the [Statistics Education Research Journal](http://www.stat.auckland.ac.nz/~iase/publications.php?show=serjarchive) ([Zieffler et al., 2011](http://www.stat.auckland.ac.nz/~iase/serj/SERJ10(2)_Zieffler.pdf)), I have been thinking about the relationships within the network of literature published on statistics education. What are the  pivotal articles? Which are foundational? How inter-connected are the articles?

This spring I started documenting those relationships by putting together a social network of articles published in [Technology Innovations in Statistics Education](http://www.escholarship.org/uc/uclastat_cts_tise) and the articles they referenced. I just finished that work and used [Gephi](https://gephi.org) to produce a couple network plots.

[![Modularity](http://citizen-statistician.org/wp-content/uploads/2013/06/Modularity.png)](http://citizen-statistician.org/wp-content/uploads/2013/06/Modularity.png)The first network graph (shown above) examines the community structure of the network by decomposing the network into sub-networks, or communities. I have made the nodes for the actual TISE articles larger for visual ease of interpretation. The node labels are the first author's last name and year of publication. Currently (and not unsurprisingly), the subnetworks generally consist of the actual article published in TISE and the literature that was referenced therein. There are some commonalities between articles as well. For example, the two articles by McDaniel were identified as a single community. It will be interesting to see how these communities change as I add more literature into the network.

[![InDegree](http://citizen-statistician.org/wp-content/uploads/2013/06/InDegree.png)](http://citizen-statistician.org/wp-content/uploads/2013/06/InDegree.png)

The second network graph has the size of the node and node label sized by in-degree. In this case, in-degree is a measure of how often a particular article was referenced. The most cited literature in TISE is:



	
  * Chance, B., Ben-Zvi, D., Garfield, J., & Medina, E. (2007). [The role of technology in improving student learning of statistics](http://repositories.cdlib.org/uclastat/cts/tise/vol1/iss1/art2). _Technology Innovations in Statistics Education, 1_(1).


	
  * Konold, C., & Miller, C. (2004). _TinkerPlots Dynamic Data Exploration_ (Version 1–2). Emeryville, CA: Key Curriculum Press.

	
  * American Statistical Association. (2010).[_ Guidelines for assessment and instruction in statistics education (GAISE): College report_](http://www.amstat.org/education/gaise/GaiseCollege Full.pdf). Alexandria, VA: Author.

	
  * National Council of Teachers of Mathematics. (2000). _Principles and standards for school mathematics_. Reston, VA: Author.

	
  * R Core Team. (2011). [_R: A language and environment for statistical computing_](http://www.R-project.org). ISBN 3-900051-07-0. Vienna, Austria.


At some point, it would be nice to do this by author as well.
