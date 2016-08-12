---
id: 180
title: 'Inspecting _.reduce, again &#8211; HRR w1d7'
date: 2015-10-12T15:00:18+00:00
author: Leslie
layout: post
guid: http://www.lesliepajuelo.com/blog/?p=180
permalink: /inspecting-_-reduce-again-hrr-w1d7/
categories:
  - HackReactor
---
A group of us got together to review what we had done week 1. Which included underscore again. To not waste time and energy on the basic functions I filled in \_.each, \_.map, \_.indexOf, and \_.reduce. The group thought we should do \_.reduce together and since I had just done it I navigated. And realized that I had muscle memory for the implementation of \_reduce but some holes in my understanding. So let&#8217;s go over this again.

## Define: _.reduce

Reduce steps through a collection, performs some action, and returns a single value. So from collection to number or string.

#### Examples:

<pre>var whoooNumbers = [2,3,1,4,5];

//Find the sum of the numbers
 
 _.reduce(whoooNumbers, function(previousItem, currentItem) {
   return previousItem + currentItem;
}
</pre>

It&#8217;s important to note that the return is adding to the current accumulator. So that line, using a loop, would read accumulator = accumulator + currentItem

It&#8217;s possible to filter, without using _.filter, for the largest number

<pre>_.reduce(whoooNumbers, function(previousItem, currentItem) {
  if(previousItem &gt; currentItem) {
    return previousItem;
  }
  else {
    return currentItem;
  }
 });
}
</pre>

As _.reduce steps over each number in the collection, whoooNumbers, it is comparing the previous item with the current item, if it is larger it is returning the previous item if not it is returning the currentItem.

Remember the return statement means accumulator = previousItem or accumulator = currentItem. Not accumulator += previousItem.
  
Examples from <a href="http://reactivex.io/learnrx/" target="_blank">http://reactivex.io/learnrx/</a>

<pre>//Some data</pre>

<pre>[{
  boxarts = [
			{ width: 200, height:200, url:"http://cdn-0.nflximg.com/images/2891/Fracture200.jpg" },
			{ width: 150, height:200, url:"http://cdn-0.nflximg.com/images/2891/Fracture150.jpg" },
			{ width: 300, height:200, url:"http://cdn-0.nflximg.com/images/2891/Fracture300.jpg" },
			{ width: 425, height:150, url:"http://cdn-0.nflximg.com/images/2891/Fracture425.jpg" }
		];

</pre>

Find the largest boxart

<pre>return _.reduce(boxart, function(previousItem,currentItem) {
		if (previousItem.width * previousItem.height &gt; currentItem.width * currentItem.height) {
		  return previousItem;
		}
		else {
		  return currentItem;
		}
	  }).
	  _.map(boxart, function(art) {
		return art.url;
	  });
}
</pre>

## Implementation

<pre>//Reduce takes a collection, an iterator, and an accumulator. If there is no accumulator it sets the first item as the accumulator.
  //If the accumulator is a truthy value (has a value)
    //then replace the accumulator with the first item in the collection.
  //If not, then for each item in the collection run the the iterator function with the accumulator and current item and replace the accumulator.
   // which is returned and added to the accumulator.

</pre>

<pre>_.reduce = function (collection, iterator, accumulator) {
            
            if (accumulator === undefined) {
                accumulator = collection[0];
                collection = collection.slice(1);
            }
            _.each(collection, function (item) {
                accumulator = iterator(accumulator, item);
            });
            return accumulator;
        };</pre>

Thank you to <a href="https://twitter.com/jeffcousins" target="_blank">Jeff Cousins </a>who very painfully walked me through understanding this again. On our day off, at night.