---
id: 276
title: Breadth First and Depth First searches
date: 2016-01-14T21:48:00+00:00
author: Leslie
layout: post
guid: http://www.lesliepajuelo.com/blog/?p=276
permalink: /breadth-first-and-depth-first-searches/
dsq_thread_id:
  - 4786678646
categories:
  - web development
---
First to compare the two types of searches:
  
<img class="aligncenter size-full wp-image-279" src="http://i1.wp.com/www.lesliepajuelo.com/blog/wp-content/uploads/2016/01/BFS-and-DFS.png?fit=754%2C383" alt="Breadth first and depth first diagrams" srcset="http://i1.wp.com/www.lesliepajuelo.com/blog/wp-content/uploads/2016/01/BFS-and-DFS.png?w=754 754w, http://i1.wp.com/www.lesliepajuelo.com/blog/wp-content/uploads/2016/01/BFS-and-DFS.png?resize=300%2C152 300w" sizes="(max-width: 754px) 100vw, 754px" data-recalc-dims="1" />
  
What we will be doing is essentially flattening the tree in two different ways.

### BFS

Starting with Breadth First Search the pseudocode is:

    Save the root node in a queue
    While (the queue isn't empty)
    nextElement = the next element from the queue
    save all the children of element in the queue
    do something to nextElement

Since we are looking at each neighbor element before diving deep a queue, First In First Out approach is useful. As we flatten the tree by saving the next element and its children, every time we dequeue a nextElement it will be a neighbor. Only once we&#8217;re out of neighbors will we descend.

A possible solution following the pseudocode for a binary search tree could be:

     BinarySearchTree.prototype.breadthFirst = function(callback) {
       var queue = new Queue(); 
       var element;
     
       queue.enqueue(this);
       while (queue.size() > 0) {  
         element = queue.dequeue();
         if (element._left) {
           queue.enqueue(element._left);
         }
         if (element._right) {
           queue.enqueue(element._right);
         }
         callback(element._value);
       }
     };

### DFS

In this case we will traverse down a &#8220;family&#8221; tree from grandparent to parent to child and so on before back tracking and exploring any of the sibling nodes. A useful data structure for this type of search is a stack. A stack takes a Last In First Out approach. The basic algorithm is that if there is a child node to explore, then go do it, and only go up in levels when there is no opportunity to go down anymore.

The pseudocode for this is identical to that for breadth first except substituting stack for queue. The code is a little different as it is much easier to both reason about and write the code for a depth first recursively.

     BinarySearchTree.prototype.depthFirstLog = function(callback) {
    2   callback(this._value);
    3   if (this._left) {
    4     this._left.depthFirstLog(callback);
    5   }
    6   if (this._right) {
    7     this._right.depthFirstLog(callback);
    8   }
    9 };