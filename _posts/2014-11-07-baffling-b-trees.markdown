---
layout:     post
title:      "Baffling B-Trees"
subtitle:   "I tackle this data structure in my latest assigned lab for class"
date:       2014-11-07 10:15:00
author:     "Chris Jang"
header-img: "img/posts/post-02/post-02-bg.png"
---

<p> So my first "real" blog post. I've been assigned a new lab in CS class today, pertaining to the fabulous data structure, the B-Tree. I think the B-Tree is probably one of my favorite data structures that we've touched on so far. They're used (to my understanding) for storing large, large amounts of data in Hard Disk Drives and Solid State Drives. Each node in the tree is made up of an array of key/data pairs, and it's children the same. *And*, it's all sorted, of course. Pretty cool </p>

<p> So we were assigned with implementing 4 functions: insertion_idx, find, split_child, and insert. </p>
+ **insertion_idx** simulates an insertion of a node and returns the appropriate index that it *would* be inserted into.
+ **find** is your typical find function, returning the value associated with the "key" we are searching for.
+ **split_child** performs the operation of splitting a child node if it exceeds the maximum allowed size. In the case of B-Trees, this size is m-1, m being the "order" of the B-Tree, which is determined at creation.
+ **insert** is the actual function that performs the insertion of a key/value pair into the tree.

<p>So I didn't have much trouble with this lab, I used a binary search instead of linear in both insertion_idx and insert, and for find I just needed to write a few lines, an if statement containing a recursive call to find. The problem was in split_child. I wasn't sure what to do with all the iterators we were given, but in the end I looked up the documentation and figured it out. It turns out that the iterators for vectors ".begin()" and ".end()" are quite different. .begin() will return the very first element, and .end() will return one *past* the end. So I had to fix a couple off-by-one errors in my code. </p>

    //assign elements to the new_right node
    new_right->elements.assign(mid_elem_itr + 1, child->elements.end());
    new_right->children.assign(mid_child_itr, child->children.end());


<p>I also discovered in the docs the 'erase' function for vector elements, and appropriately called this on the old median node in the child to be split, and thus completing the split.</p>

    parent->children.erase(child_itr + 1);

<p> All in all, it was a fun lab, and I learned (a lot) about iterators and how they work in C++. And to actually implement B-Trees was cool. I look forward to learning more data structures. Today we started learning about hash tables, and those were also really cool. Maybe I'll post about those once we have a lab about them! See you guys next time.</p>
