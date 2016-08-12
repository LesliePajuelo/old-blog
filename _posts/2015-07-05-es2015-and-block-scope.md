---
id: 93
title: ES2015 and block scope
date: 2015-07-05T01:38:23+00:00
author: Leslie
layout: post
guid: http://www.lesliepajuelo.com/blog/?p=93
permalink: /es2015-and-block-scope/
categories:
  - web development
---
Javascript is getting block scope, to someone who didn&#8217;t really understand scope at all a couple of months ago this is great.

Before variables would be available in the function they were created and any inner functions. If they were created outside of a function they would be globals.

Now, with the `let` keyword they are limited to the block they were created in. A block being an `if` or `for` loop. I&#8217;m still unclear if an inner block or inner function would still have access or if we&#8217;d have to use a `var`.

`const` is another new keyword which as it&#8217;s name implies create constants which cannot be changed. They also have block scope. The convention from other languages is to capitalize constants. Const also needs to be assigned then used. No more on-the-fly creation