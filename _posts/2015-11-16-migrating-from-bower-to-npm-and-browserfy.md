---
id: 218
title: Migrating from Bower to npm and Browserfy
date: 2015-11-16T17:05:14+00:00
author: Leslie
layout: post
guid: http://www.lesliepajuelo.com/blog/?p=218
permalink: /migrating-from-bower-to-npm-and-browserfy/
dsq_thread_id:
  - 4327105941
categories:
  - web development
---
It started with a Heroku deploy fail

&nbsp;

<pre>EvC@0.0.0 /tmp/build_a439dbdb513f88da54eacde425cd6aba
   └── (empty)&lt;

       npm verb exit [ 0, true 
       npm ERR! code 1

-----&gt; Build failed</pre>

After chasing that error through a dozen build attempts I ended up with this.

&nbsp;
  
       `sh: 1: bower: not found`

Somehow it could no longer hook into bower even tho that hadn't changed. After more searching and finding doom messages about the future of bower and since it was at the core of what was going awry with my Heroku build slugs I decided to move this project over to npm and browserfy.

Step 1.
  
If you don't already have a package.json file going for that project, start one
  
`npm init`

Step 2.
  
`npm install -g browserify`

If you get `Error: EACCES, mkdir '/usr/local/lib/node_modules/browserify'` it can be resolved with sudo but it's best to resolve the root of the issue, a great resource is <a href="https://gist.github.com/isaacs/579814" target="_blank">Issacs' code snippets.</a>

Step 3.
  
`npm install --save`
  
For all your bower dependencies.

Sigh, if I have to do this again I"ll probably make a script that does this. But this is a small project I did it manually.

Step 4.
  
`angular = require('angular');` etc for all your dependencies in each file.

Step 5.
  
`browserify app.js -o bundle.js`

-o is for output

> #### <a href="https://github.com/substack/browserify-handbook#how-browserify-works" target="_blank">How Browerfiy works</a>
> 
> Browserify starts at the entry point files that you give it and searches for any require() calls it finds using static analysis of the source code's abstract syntax tree.
  
> For every require() call with a string in it, browserify resolves those module strings to file paths and then searches those file paths for require() calls recursively until the entire dependency graph is visited.

&nbsp;

In your main index.html file add ``

What if the dependency you want is only available as a bower component? There's <a href="https://github.com/eugeneware/debowerify" target="_blank">debowerfy</a>

Optional if you're just converting a project but if you plan to do more development it'd be easier to add <a href="https://www.npmjs.com/package/watchify" target="_blank">watchify</a> and run `watchify app.js -o bundle.js`