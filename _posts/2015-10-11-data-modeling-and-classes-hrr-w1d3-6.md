---
id: 162
title: 'Data Modeling and Classes &#8211; HRR w1d3-6'
date: 2015-10-11T23:53:14+00:00
author: Leslie
layout: post
guid: http://www.lesliepajuelo.com/blog/?p=162
permalink: /data-modeling-and-classes-hrr-w1d3-6/
categories:
  - web development
---
# The days are long but week is short.

After the review we covered data modeling, classes, data structures, and time complexity.

[Data Stack from Wikipedia](https://en.wikipedia.org/wiki/Stack_(abstract_data_type)#/media/File:Data_stack.svg)

## 

## Data modeling &#8211; Stacks and Queues

### Stacks

<a href="https://en.wikipedia.org/wiki/Stack_(abstract_data_type)" target="_blank"><img class="wp-image-171" src="http://i0.wp.com/www.lesliepajuelo.com/blog/wp-content/uploads/2015/10/391px-Data_stack.svg_.png?resize=200%2C144" alt="Data Stack Illustration" srcset="http://i0.wp.com/www.lesliepajuelo.com/blog/wp-content/uploads/2015/10/391px-Data_stack.svg_.png?w=391 391w, http://i0.wp.com/www.lesliepajuelo.com/blog/wp-content/uploads/2015/10/391px-Data_stack.svg_.png?resize=300%2C216 300w" sizes="(max-width: 200px) 100vw, 200px" data-recalc-dims="1" /></a>

<a href="https://en.wikipedia.org/wiki/Stack_(abstract_data_type)" target="_blank">Image from wikipedia</a>

Ordered like a good ol&#8217; fashioned stack of paper. Or like working at a union shop. &#8220;Last hired &#8211; first fired&#8221;. Or the commonly used &#8220;Last in, first out&#8221; (LIFO)

### 

<div id="attachment_172" style="width: 210px" class="wp-caption alignleft">
  <a href="http://i2.wp.com/www.lesliepajuelo.com/blog/wp-content/uploads/2015/10/405px-Data_Queue.png"><img class="wp-image-172" src="http://i2.wp.com/www.lesliepajuelo.com/blog/wp-content/uploads/2015/10/405px-Data_Queue.png?resize=200%2C131" alt="Illustration of a queue" srcset="http://i2.wp.com/www.lesliepajuelo.com/blog/wp-content/uploads/2015/10/405px-Data_Queue.png?resize=300%2C196 300w, http://i2.wp.com/www.lesliepajuelo.com/blog/wp-content/uploads/2015/10/405px-Data_Queue.png?w=405 405w" sizes="(max-width: 200px) 100vw, 200px" data-recalc-dims="1" /></a>
  
  <p class="wp-caption-text">
    <a href="https://en.wikipedia.org/wiki/Queue_(abstract_data_type)" target="_blank">Image from wikipedia</a>
  </p>
</div>

### Queue

Like it&#8217;s name implies, if you&#8217;re British, it&#8217;s just a line.

&nbsp;

&nbsp;

&nbsp;

<div id="attachment_173" style="width: 310px" class="wp-caption alignleft">
  <a href="http://nick.balestra.ch/2015/depthFirst-vs-breadthFirst/" target="_blank"><img class="wp-image-173 size-medium" src="http://i1.wp.com/www.lesliepajuelo.com/blog/wp-content/uploads/2015/10/tree-traversal-algos-300x175.png?fit=300%2C175" alt="Two trees being traversed by different methods" srcset="http://i0.wp.com/www.lesliepajuelo.com/blog/wp-content/uploads/2015/10/tree-traversal-algos.png?resize=300%2C175 300w, http://i0.wp.com/www.lesliepajuelo.com/blog/wp-content/uploads/2015/10/tree-traversal-algos.png?w=520 520w" sizes="(max-width: 300px) 100vw, 300px" data-recalc-dims="1" /></a>
  
  <p class="wp-caption-text">
    Nick Balestra&#8217;s image
  </p>
</div>

I couldn&#8217;t think of how these concepts would be useful until my class shepherd <a href="http://nick.balestra.ch/2015/depthFirst-vs-breadthFirst/" target="_blank">Nick Balestra</a> posted on how each method affects searching through a tree structure. His post explains very well how each method affects metrics.

## 

## 

## 

## 

## Class Patterns

[<img class="alignleft size-thumbnail wp-image-174" src="http://i0.wp.com/www.lesliepajuelo.com/blog/wp-content/uploads/2015/10/fxn2D3-150x150.png?resize=150%2C150" alt="Chart of 4 javascript classes" data-recalc-dims="1" />](http://www.ryanatkinson.io/javascript-instantiation-patterns/)Functional, functional shared, prototypal, and psuedoclassical. I tried to make my own code sample to example, and I think I learned from making it but still found <a href="http://www.ryanatkinson.io/javascript-instantiation-patterns/" target="_blank">Ryan Atkinson&#8217;s</a> diagram more useful.

&nbsp;

## 

## 

## Advanced Data Structures

  * #### <a href="https://en.wikipedia.org/wiki/Linked_list" target="_blank">Linked Lists</a> (single and double)
    
      * <a href="https://en.wikipedia.org/wiki/Tree_(data_structure)" target="_blank">Tree</a> 
          * <a href="https://en.wikipedia.org/wiki/Binary_search_tree" target="_blank">Binary search tree</a>
      * <a href="https://en.wikipedia.org/wiki/Graph_(abstract_data_type)" target="_blank">Graph</a>

[<img class="alignleft wp-image-177 size-medium" src="http://i0.wp.com/www.lesliepajuelo.com/blog/wp-content/uploads/2015/10/GUID-300x195.png?fit=300%2C195" alt="Depiction of the graph data structure connecting cities in the american mid-west" srcset="http://i1.wp.com/www.lesliepajuelo.com/blog/wp-content/uploads/2015/10/GUID.png?resize=300%2C195 300w, http://i1.wp.com/www.lesliepajuelo.com/blog/wp-content/uploads/2015/10/GUID.png?w=568 568w" sizes="(max-width: 300px) 100vw, 300px" data-recalc-dims="1" />](http://i1.wp.com/www.lesliepajuelo.com/blog/wp-content/uploads/2015/10/GUID.png)

These are grouped together because a linked list, a node with a value and a pointer to the next node, is the basis for the other data structures below it. Well at least it definitely is for trees. A good use of single linked lists are itineraries, like a road trip (a thought for thesis or maybe solo project), doubly linked lists are seen everywhere with <ctrl-z> and <ctrl-y>, undo/redo. Trees are the basic structure of web pages. A binary search trees is really a header for a slew of specific data structures which optimize for different use scenarios. Graphs(pictured left) are used in topography and in GIS calculations of cost-analysis.

&nbsp;

&nbsp;
  
<a href="https://en.wikipedia.org/wiki/Set_(abstract_data_type)" target="_blank">Sets</a> &#8211; Sets, sets, sets, how are you useful? Wikipedia doesn&#8217;t know either. I&#8217;ll update this once I find a use case, maybe.

> Implementations described as &#8220;general use&#8221; typically strive to optimize the `element_of`, `add`, and `delete` operations. A simple implementation is to use a [list](https://en.wikipedia.org/wiki/List_(abstract_data_type) "List (abstract data type)"), ignoring the order of the elements and taking care to avoid repeated values. This is simple but inefficient, as operations like set membership or element deletion are _O_(_n_), as they require scanning the entire list.<sup id="cite_ref-14" class="reference"><a href="https://en.wikipedia.org/wiki/Set_(abstract_data_type)#cite_note-14">[d]</a></sup> Sets are often instead implemented using more efficient data structures, particularly various flavors of [trees](https://en.wikipedia.org/wiki/Tree_(data_structure) "Tree (data structure)"), [tries](https://en.wikipedia.org/wiki/Trie "Trie"), or [hash tables](https://en.wikipedia.org/wiki/Hash_tables "Hash tables"){.mw-redirect}.

&nbsp;

<div id="attachment_178" style="width: 310px" class="wp-caption alignleft">
  <a href="https://en.wikipedia.org/wiki/Hash_table"><img class="wp-image-178 size-medium" src="http://i0.wp.com/www.lesliepajuelo.com/blog/wp-content/uploads/2015/10/315px-Hash_table-300x219.png?fit=300%2C219" alt="A small contact list as a hash table" srcset="http://i0.wp.com/www.lesliepajuelo.com/blog/wp-content/uploads/2015/10/315px-Hash_table.png?resize=300%2C219 300w, http://i0.wp.com/www.lesliepajuelo.com/blog/wp-content/uploads/2015/10/315px-Hash_table.png?w=315 315w" sizes="(max-width: 300px) 100vw, 300px" data-recalc-dims="1" /></a>
  
  <p class="wp-caption-text">
    &#8220;<a href="https://commons.wikimedia.org/wiki/File:Hash_table_3_1_1_0_1_0_0_SP.svg#/media/File:Hash_table_3_1_1_0_1_0_0_SP.svg">Hash table 3 1 1 0 1 0 0 SP</a>&#8221; by <a title="User:Jorge Stolfi" href="//commons.wikimedia.org/wiki/User:Jorge_Stolfi">Jorge Stolfi</a> &#8211;  Licensed under <a title="Creative Commons Attribution-Share Alike 3.0" href="http://creativecommons.org/licenses/by-sa/3.0">CC BY-SA 3.0</a> via <a href="https://commons.wikimedia.org/wiki/">Commons</a>.
  </p>
</div>

&nbsp;

<a href="https://en.wikipedia.org/wiki/Hash_table" target="_blank">Hash Tables</a>: Great for finding key: value pairs really fast! Say for caching. I&#8217;m sure a great many other things.

&nbsp;

&nbsp;

&nbsp;

&nbsp;

## 

## <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/bind" target="_blank">Bind</a>

It&#8217;s possible to bind what &#8216;this&#8217; refers to by calling .bind without passing arguments like you do for call and apply. I&#8217;m certain this is useful. I&#8217;m not sure how yet and we didn&#8217;t really go over it. Was simply introduced to the idea without a practical application. It&#8217;s used in <a href="http://backbonejs.org/" target="_blank">backbone.js</a>, a lot.

&nbsp;

whew, that was 4 days.

##