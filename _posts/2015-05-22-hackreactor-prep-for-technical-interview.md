---
id: 64
title: HackReactor prep for technical interview
date: 2015-05-22T23:35:06+00:00
author: Leslie
layout: post
guid: http://www.lesliepajuelo.com/blog/?p=64
permalink: /hackreactor-prep-for-technical-interview/
categories:
  - HackReactor
---
I recently applied to HackReactor and have my technical interview set for June 10th.

The 3 big things I was told to know were callbacks, closures, and anonymous functions.

**Anonymous functions** are easy, I&#8217;ve used those all the time. Anyone who&#8217;s used jQuery has used them

`$(document).on("mouseover", ".feature-row", function(e) {<br />
highlight.clearLayers().addLayer(L.circleMarker([$(this).attr("lat"), $(this).attr("lng")], highlightStyle));<br />
});`

That function(e){} is the anonymous function. It&#8217;s nameless, is executed immediately. 

**Callbacks**, the example above is also a callback, a function being passed as an argument. In this case it is run immediately tho it is often used in asynchronous applications. I&#8217;ll be looking into that more with node.js which is apparently all callback and closures.

Which brings us to **closures**. They are functions that can make variables private. It involves at least two functions and the outer function only has access to global variables and it&#8217;s own. While the inner function can access global variables, the outer functions&#8217; variables, and it&#8217;s own&#8230;which no outside function can access. 

I suppose there could be functionception with various levels of nesting functions and have each inner function use a reference to variables from an outer function.

``I recently applied to HackReactor and have my technical interview set for June 10th.

The 3 big things I was told to know were callbacks, closures, and anonymous functions.

**Anonymous functions** are easy, I&#8217;ve used those all the time. Anyone who&#8217;s used jQuery has used them

`$(document).on("mouseover", ".feature-row", function(e) {<br />
highlight.clearLayers().addLayer(L.circleMarker([$(this).attr("lat"), $(this).attr("lng")], highlightStyle));<br />
});`

That function(e){} is the anonymous function. It&#8217;s nameless, is executed immediately. 

**Callbacks**, the example above is also a callback, a function being passed as an argument. In this case it is run immediately tho it is often used in asynchronous applications. I&#8217;ll be looking into that more with node.js which is apparently all callback and closures.

Which brings us to **closures**. They are functions that can make variables private. It involves at least two functions and the outer function only has access to global variables and it&#8217;s own. While the inner function can access global variables, the outer functions&#8217; variables, and it&#8217;s own&#8230;which no outside function can access. 

I suppose there could be functionception with various levels of nesting functions and have each inner function use a reference to variables from an outer function.

`` 

A simple example of an anonymous function being the inner function to another anonymous function. It&#8217;s a closure because the inner function accesses counter, a variable created in the other function.

Because the inner function uses a reference to the outer variables those variables can change before the functions are done executing. For example:

`function foo(x) {<br />
  var tmp = 3;</p>
<p>  return function (y) {<br />
    return(x + y + (++tmp)); //is 16, not 15 because it incremented then added.<br />
  }<br />
}</p>
<p>var bar = foo(2); // bar is now a closure.<br />
bar(10);`

Remember to use <a href="http://www.pythontutor.com/" target="_blank">Python Tutor</a> extensively if the result is not as expected.