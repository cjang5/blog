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

<img src="{{ site.baseurl }}/img/posts/post-07/grid.png" align="center" style="float: center; width: 40%; margin-bottom: 0.5em;">



<img src="{{ site.baseurl }}/img/posts/post-07/unsolved1.png" style="float: left; width: 30%; margin-left: 2%; margin-right: 3%; margin-bottom: 0.5em;">
<img src="{{ site.baseurl }}/img/posts/post-07/unsolved2.png" style="float: left; width: 30%; margin-right: 3%; margin-bottom: 0.5em;">
<img src="{{ site.baseurl }}/img/posts/post-07/unsolved3.png" style="float: left; width: 30%; margin-right: 0%; margin-bottom: 0.5em;">

<p style="clear: both;"></p>

<p>You might have noticed that the mazes have entraces at the top left corner, but no exit. This is intentional. We will create an exit as part of the solving algorithm. Of course we could make this vary, but we look for the longest path possible to place the exit.</p>