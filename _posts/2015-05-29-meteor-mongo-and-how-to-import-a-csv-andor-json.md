---
id: 67
title: Meteor, mongo, and how to import a csv and/or json
date: 2015-05-29T00:25:29+00:00
author: Leslie
layout: post
guid: http://www.lesliepajuelo.com/blog/?p=67
permalink: /meteor-mongo-and-how-to-import-a-csv-andor-json/
dsq_thread_id:
  - 4098416721
categories:
  - HackReactor
  - Meteor
  - mongo
---
I felt like I had a pretty good grasp on the concepts they outlined and figured I better do some google-fu and find out what other people were saying. Came upon a [quora](http://www.quora.com/I-want-to-apply-for-Hack-Reactor-but-have-no-programming-knowledge-What-do-I-need-to-learn-to-apply-What-materials-should-I-use-to-get-there-How-can-I-make-myself-stand-out-so-Im-accepted) question that was answered by a cofounder which listed essentially some basic loops, accessing arrays and objects, some code challengelets like codery byte. And at the bottom said if you want to stand out, build something with Famo.us, Meteor, or Firebase. 

Now that question is from summer 2014 so I assume everyone who is serious about applying has something built. So I doubt it makes you stand out anymore. 

After poking around the three I chose Meteor because frankly it looks like an amazing platform to develop from. Not to knock the other two but Meteor is wow.

I did their tutorial, followed along the freebie book and felt pretty good. I even re-did the tutorial using methods to solidify things. I&#8217;ve been working on this map for the local Red Cross. It has a few layers imported from two geoJSON files. I thought it&#8217;d be a perfect project to build since it appears adding authorization is trivial with Meteor and that&#8217;s something I had been dreading to add. Also, with the templates I thought it&#8217;d be easier to filter through my files and create layers without cut/paste and changing variable names in 30 different places.

And here is where my wide-eyed amazement with Meteor ended. Since it&#8217;s built for webapps importing existing data doesn&#8217;t seem to be a priority. All of the map examples I could find that were open source consisted of adding point markers. Maybe it&#8217;s just my google-fu failing but so far no love. So I searched how to import JSON files and got HTTP requests to hosted JSON from services like Open Weather. Finally, I gave up and said let&#8217;s just import a freakin csv. Simple? no.

The Mongo that ships with Meteor doesn&#8217;t have any of the import libraries. So first, install the full mongo. Thank goodness I&#8217;m on ubuntu and that&#8217;s just an apt-get away.

Second from command line do this:

`<br />
 mongoimport -h localhost:3001 --db meteor --collection shelters --type csv --file shelters.csv --fields Name,Intervention,Type,latitude,longitude --headerline`

Thank you [Adilapapaya!](https://adilapapaya.wordpress.com/2014/03/12/things-i-wish-someone-told-me-when-i-first-started-learning-meteor-js/)