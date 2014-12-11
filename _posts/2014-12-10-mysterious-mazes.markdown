---
layout:     post
title:      "Mysterious Mazes"
subtitle:   "Post-mortem of MP7!"
date:       2014-12-10 08:00:00
author:     "Chris Jang"
header-img: "img/posts/post-07/post-07-bg.png"
---

<p>So I finally finished the maze Machine Problem! I would like to add, that I finished it in 48 hours, and I am proud of that, haha. I was tight on time so I just worked on it straight through for that time. It was really fun though, implementing a variant of the different version of Breadth-First-Search I've already learned in class and using that to solve a randomly generated maze. So now let's talk about it:</p>

<h2>Generating the Maze</h2>

<p>First is creating the actual maze so that it is random enough and doesn't look like we are using a template over and over. To accomplish this, I first created a grid of a given width and length. So for example, a call to:</p>

    //create the maze
    makeMaze(10, 10);
    
<p>would first create a 10 by 10 grid to work with: </p>

<img src="{{ site.baseurl }}/img/posts/post-07/grid.png" align="center" style="float: center; width: 40%; margin-left: 30%; margin-bottom: 0.5em;">

<p>The next part is where we use a little style to make it "random". We first use a could standard library algorithms, like std::shuffle. Instead of creating a 2D vector to represent the Cells in the grid, we use a 1D vector, and just wrap around if we get to the end of a row. So it would look like this: </p>

<img src="{{ site.baseurl }}/img/posts/post-07/1dvector.png" align="center" style="float: center; width: 50%; margin-left: 30%; margin-bottom: 0.5em;">

<p>So next, we shuffle that 1 dimensional vector so the positions get randomized, like:</p>

    //not shuffled:
    <0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10>
    //shuffled:
    <6, 8, 1, 3, 5, 4, 10, 9, 2, 7, 0>
    
<p>Next, we iterate through those Cells, and then for each one we remove its right wall if we can, and then its bottom wall if we can. By "if we can", I mean if it doesn't create a cycle in the maze and that it isn't up against the bottom or right walls of the maze. By preventing cycles, we also prevent there being more than one way to get from one cell to another. Every time that we *do* remove a wall, we perform a setunion on those two elements in our DisjointSets data structure that represents each Cell in the maze. By using this data structure, we can find paths from one cell to another as well. </p>

<p>After removing all walls that we can without creating cycles, we might get something like the mazes below: </p>

<img src="{{ site.baseurl }}/img/posts/post-07/unsolved1.png" style="float: left; width: 30%; margin-left: 2%; margin-right: 3%; margin-bottom: 0.5em;">
<img src="{{ site.baseurl }}/img/posts/post-07/unsolved2.png" style="float: left; width: 30%; margin-right: 3%; margin-bottom: 0.5em;">
<img src="{{ site.baseurl }}/img/posts/post-07/unsolved3.png" style="float: left; width: 30%; margin-right: 0%; margin-bottom: 0.5em;">

<p style="clear: both;"></p>

<p>You might have noticed that the mazes have entraces at the top left corner, but no exit. This is intentional. We will create an exit as part of the solving algorithm. Of course we could make this vary, but we look for the longest path possible to place the exit.</p>

<h2>Solving the Maze</h2>

<p>Now we move on to solving the actual maze. I mentioned before that we create the exit after we find the longest possible path from the center to a cell in the bottom row of the maze. To do this, we use a Breadth-First-Search on each cell. We start at the center, and then we check if we can travel to the right of it, AND if that cell hasn't already been visited. If so, we enqueue it onto a Queue, and move on to the cell below the current one. We then go to the left, above, etc. By doing this, we effectively and efficiently find the shortest path from the beginning Cell to every other Cell in the maze, in O(n) time, where n represents how many Cells are in the maze!</p>

<p>After performing the BFS, we can now iterate through each Cell in the bottom row of the maze, keeping track of its distance from the starting Cell and storing the maximum. Once we find the maximum, we create the exit in that Cell, and then work our way backwards to the starting Cell, while keeping track of the appropriate directions (right, down, left, up). We reverse that directions vector at the end and then we go through each one, drawing a red line to represent the solution path along the way. A couple solutions might look like the following: </p>

<img src="{{ site.baseurl }}/img/posts/post-07/solved1.png" style="float: left; width: 30%; margin-left: 2%; margin-right: 3%; margin-bottom: 0.5em;">
<img src="{{ site.baseurl }}/img/posts/post-07/solved2.png" style="float: left; width: 30%; margin-right: 3%; margin-bottom: 0.5em;">
<img src="{{ site.baseurl }}/img/posts/post-07/solved3.png" style="float: left; width: 30%; margin-right: 0%; margin-bottom: 0.5em;">
