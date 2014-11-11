---
layout:     post
title:      "Killer KD-Trees"
subtitle:   "Probably one of the roughest MPs I've tackled"
date:       2014-11-10 10:50:00
author:     "Chris Jang"
header-img: "img/posts/post-03/post-03-bg.png"
---

<img src="img/posts/post-03/post-03-monad.png">

<p> It's a beautiful sight, isn't it? Well, it is to me. Those successful test cases for part one of my sixth MP for my Data Structures class is sweet relief to my brain and eyes. I've been working on this for a few days now, and I've been wracked with a plethora of problems, ranging from Segfaults to Out-of-bounds errors, to just straight up incorrect construction of the trees. </p>

<p> If you don't know already, this Machine Problem is centered around k-dimensional trees, or "KD Trees". They're pretty cool variants of the general Binary Search Tree, using a QuickSelect algorithm to partition the nodes, and making sure that the median of a specific dimension stays the root of the subtree it's in.... I'm not sure if that made sense. </p>

<p> It took me longer than I'd care to admit to figure out how the Quickselect algorithm worked... I wrote multiple useless helper functions trying to implement it. I understood the basic idea pretty quickly, but how to implement it? That took me a good while, for some reason. Once I figured it out, however, I was met with tens of new problems I needed to solve. </p>

<p> The final problem I fixed had to do with "mines" in the nodes, or basically any nodes I should not have been traversing during the findNearestNeighbor algorithm. It was a simple vector element swappage problem, and I felt totally stupid after trying to hunt down the source of the bug for hours on end. But I'm finally done with the first part, as per that screenshot at the beginning of the post. I formatted all my code and commented it to make it all pretty, and I'm submitting this blog post as the final step to my completion of the MP (before the Extra Credit due date, yes I'm a tryhard). </p>

<p> Well that's all I have for now. I'm relieved this first part is over, as the second part should be easy, and then I can finally get to working on my website/tree project again. Oh - also the second part of the MP is to implement the K-d Tree to create a photomosaic, so I'll probably create one and post it in that submission when it happens! :) </p>
