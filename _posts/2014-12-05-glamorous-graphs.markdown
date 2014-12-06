---
layout:     post
title:      "Glamorous Graphs"
subtitle:   "Let's delve into some graphs now..."
date:       2014-12-05 11:37:00
author:     "Chris Jang"
header-img: "img/posts/post-06/post-06-bg.png"
---

<p>Alright, back with another post! Today I delve into the latest lab assignment for my Data Structures class, dealing with graphs! I haven't seen graphs since my Discrete Math class last year, so this was exciting for me. For this lab we were tasked with using a Breadth First Search to traverse some graphs of major city networks in the world, including the US, Japan, and Europe. Here are the graphs below: </p>

<p> <img class="img-responsive" src="{{ site.baseurl }}/img/posts/post-06/united-states-mst.png" align="left" style="width:300px"> <img class="img-responsive" src="{{ site.baseurl }}/img/posts/post-06/europe.png" align="middle" style="width:300px"> <img class="img-responsive" src="{{ site.baseurl }}/img/posts/post-06/japan.png" align="right" style="width:300px"> </p>

<p> Those are the graphs when all their vertices and edges are labeled "UNVISITED" or "UNEXPLORED". If you put different labels on them like "DISCOVERY" or "VISITED" they will have different colors. For example, one of the functions I implemented was to find the minimum path from a given vertex 'start' to another given vertex 'end'. I used the BFS algorithm to traverse the tree, but I also kept track of each vertex's distance from the 'start' Vertex, as well as each Vertex's predecessor. After the traversal was finished I just worked my way up through the predecessor vector starting from the 'end' Vertex and going to the 'start' vertex, and labeling those corresponding edges with "MINPATH", which will make them blue, as you can see below. </p>

<img class="img-responsive" src="{{ site.baseurl }}/img/posts/post-06/shortest-path-europe.png" align="middle">

<p>Here's the same function but for the US graph. It finds the shortest path from Washington DC to Kansas City:</p>

<img class="img-responsive" src="{{ site.baseurl }}/img/posts/post-06/shortest-path-us.png" align="middle">

<p> Now you might be wondering, how do I pick with path to represent the minimum path when there are multiple paths that satisfy the minimum requirement length? Well, the way I implemented the algorithm was to add each of a vertex's adjacent vertices to a Queue, and so the first one to be added would be pulled out first, and assessed. I could have made it random, and so I would get a different picture each time, but I decided to just use this, as it was simpler. </p>

<p>Another function I had to implement that I thought was pretty cool was to find the minimum spanning tree for each graph, taking into account each edge's weight. So not just the number of edges, but the weight of each edge, which is represented by the number of miles from a city to the next. To do this, I used something I learned about in class, called Kruskal's Algorithm. This involves gathering all the edges of the graph into a vector (or any other data structure, really), and then sorting them by their respective weights. </p>

<p> After that, we create a disjoint set data structure, (which I made for my most recent MP, blog post coming soon!) and each set in the structure represents a vertex in the graph. We then loop through each edge, and if its two endpoints are in separate sets, we perform a set union on the two sets, merging them into a bigger set. We continue to do this until we have n-1 edges in our spanning tree, where n is the number of vertices we have. So here is the minimum spanning tree for the japan graph: </p>

<img class="img-responsive" src="{{ site.baseurl }}/img/posts/post-06/kruskal-japan.png" align="middle">

<p>Well that's all I have for now, I'll see you guys when I finish up the last part of my current MP. Hope you learned something or just found it even remotely interesting, because I did. I'm beginning to find these graphs super interesting.</p>
