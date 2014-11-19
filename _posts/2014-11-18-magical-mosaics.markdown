---
layout:     post
title:      "Magical Mosaics"
subtitle:   "The second half of MP6 - Mosaics using a kd-tree"
date:       2014-11-18 10:15:00
author:     "Chris Jang"
header-img: "img/posts/post-04/post-04-bg.png"
---
<p align="center"> Original Image </p>
<img class="img-responsive" src="{{ site.baseurl }}/img/posts/post-04/tesla-model-s.png" align="middle">

<p align="center"> Mosaic-ified Image* </p>
<img class="img-responsive" src="{{ site.baseurl }}/img/posts/post-04/tesla-model-s-mosaic.png" align="middle">

<p> As you can see above, I finally got around to finishing the MP where we implement the actual mosaic creator. We did this using a "mapTiles" function that takes in a couple parameters: </p>
+ a **SourceImage** - Really what underlies this object is a PNG file - this is just the cpp representation for the purposes of the program.
+ a vector of **TileImages** - And these are the smaller images that will make up the mosaic at the end - also PNGs

<p> It was much simpler than implementing the kd-tree class in the first part of the project. It didn't even hit a 100 lines of code! What it took was for me to get the average colors of each "tile region" in the original source image - this is passed in through the terminal as a flag - and then create an std::map of type < Point<3> , TileImage>. What I effectively did here was map the RBG components in the form of a 3-D point to its respective TileImage in the original vector.</p>

<p> We create the kd-tree with the keys being the RGB values of the averages of each region in the source image. Then we perform a Nearest Neighbor Search (using quickselect as I said in the last blog post) and then I find its corresponding TileImage in the vector I created earlier. We then systematically set each TileImage in the final product using a nested for loop and the final product is created! </p>

<p> That's all for now, I'll see you guys in the next post! </p>

<p> *-The actual image was 8000 by 4000 or something huge, I had to make it much smaller for the blog!* </p>
