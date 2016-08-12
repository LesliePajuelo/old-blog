---
id: 187
title: 'Week 3 recap &#8211; HRR'
date: 2015-10-26T02:55:15+00:00
author: Leslie
layout: post
guid: http://www.lesliepajuelo.com/blog/?p=187
permalink: /week-3-recap-hrr/
categories:
  - HackReactor
---
No technical post this week, felt too overwhelmed to finish either of the two that are started.

  1. Chat client
  2. Music player
  3. Blackjack

1.We created a chat client with jquery and AJAX requests to <a href="https://parse.com/" target="_blank">Parse</a>. We&#8217;ll be replacing Parse tomorrow with our own server written in node. The basic AJAX requests were straightforward. Less so was the styling etc with jQuery. Which despite having wrangled a very similar problem in pre-course(minus server) still turned out to be frustrating. Having just done D3 my partner and I found ourselves occasionally typing the wrong syntax.

[<img class="size-medium wp-image-188 alignleft" src="http://i1.wp.com/www.lesliepajuelo.com/blog/wp-content/uploads/2015/10/Screenshot-from-2015-10-25-194126-300x168.png?fit=300%2C168" alt="Flow of mytunes" srcset="http://i1.wp.com/www.lesliepajuelo.com/blog/wp-content/uploads/2015/10/Screenshot-from-2015-10-25-194126.png?resize=300%2C168 300w, http://i1.wp.com/www.lesliepajuelo.com/blog/wp-content/uploads/2015/10/Screenshot-from-2015-10-25-194126.png?w=946 946w" sizes="(max-width: 300px) 100vw, 300px" data-recalc-dims="1" />](http://i1.wp.com/www.lesliepajuelo.com/blog/wp-content/uploads/2015/10/Screenshot-from-2015-10-25-194126.png)

2. The music player was done with backbone.js. The simplified diagram of how it all connected. I&#8217;m tempted to post the more complex but still missing pieces from the lecture but don&#8217;t want to give away the secret sauce. Needless to say backbone needs a lot of connections. As I&#8217;m now suspecting all MV* systems need and the reason why Meteor.js touts itself as a solution to having to wire the different pieces together.

My partner and I spent a couple of hours talking through how everything connected. In retrospect we should have picked the 1st feature to implement and follow that single feature through the chain. Once we we did that all of the talking we did earlier made more sense.

&nbsp;

&nbsp;

3. Blackjack in CoffeeScript aaand backbone again. Armed with a greater understanding of backbone we were bogged down by CoffeeScript. While the lack of curly braces, semi-colons, and parens is a huge selling point for people coming from other languages at this point those are so familiar now that not having them led to syntax problems. Especially with nested if statements as the spacing is critical. Luckily, the <a href="http://coffeescript.org/#try:alert%20%22Hello%20CoffeeScript!%22" target="_blank">CoffeeScript</a> site has a browser based transpiler which helped us spot indenting errors. It was helpful to be able to think from a higher-level than the quick to implementation way that I usually jump to. This sprint I was able to communicate in English better what I wanted to accomplish mostly because I couldn&#8217;t default to just dictating to my partner when navigating. However, with ES2015/ES6, TypeScript with Angular coming up it is unlikely I&#8217;ll return to CoffeeScript unless I end up working at a place that uses it.