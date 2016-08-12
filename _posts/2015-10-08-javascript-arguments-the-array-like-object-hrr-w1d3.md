---
id: 164
title: 'Javascript Arguments: the array-like object HRR w1D3'
date: 2015-10-08T08:18:45+00:00
author: Leslie
layout: post
guid: http://www.lesliepajuelo.com/blog/?p=164
permalink: /javascript-arguments-the-array-like-object-hrr-w1d3/
categories:
  - HackReactor
---
We had our first &#8220;warm-up&#8221; self-assessment and half of the tests for a function failed because of the &#8220;array-like&#8221; part of arguments.

&nbsp;

### How I used arguments &#8211; somewhere I had learned it was an array of all the possible arguments.

<pre>//this works
var args =[];
for ( var i = 2; i &lt; arguments.length; i++ ) {
  args.push(arguments[i])
}

//this works. 
//notice that it's func.apply... like for an array
result <span class="pl-k">=</span> func.<span class="pl-c1">apply</span>(<span class="pl-v">null</span>, arguments);

//this works, depending on your javascript interpreteror and how _.each is defined.
_.each(arguments, function(argument){
  return argument};

</pre>

Why? why does it depend? we used it as an array, it responds like an array, why isn&#8217;t it a duck?
  
Because it&#8217;s an object&#8230;. an array-like **object**.

The value at arguments[0] is an object. The remaining arguments are the actual arguments passed in at time of invocation and other items which may not act as expected depending on your javascript engine.

### How to use arguments.

<a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/arguments" target="_blank">MDN</a> has the standard way of accessing arguments as:

<pre><span class="pl-k">//Notice the slice.call for an object
var</span> args <span class="pl-k">=</span> <span class="pl-c1">Array</span>.<span class="pl-c1">prototype</span>.slice.<span class="pl-c1">call</span>(arguments, <span class="pl-c1">2</span>);
</pre>

With a note that V8 and possibly other javascript engines cannot optimize for speed. So instead of nailing this down like an object. We&#8217;re back to array-like.
  
To use

<pre>arguments</pre>

<a href="https://github.com/petkaantonov/bluebird/wiki/Optimization-killers#3-managing-arguments" target="_blank">safely and efficiently:</a>

<pre>function doesntLeakArguments() {
 //.length is just an integer, this doesn't leak
 //the arguments object itself
 var args = new Array(arguments.length);
   for(var i = 0; i &lt; args.length; ++i) {
 //i is always valid index in the arguments object
     args[i] = arguments[i];
   }
 return args;
 }</pre>