---
id: 190
title: 'Backbone.js worflow, MVC, and backbone&#8217;s version of MV*'
date: 2015-11-02T02:55:09+00:00
author: Leslie
layout: post
guid: http://www.lesliepajuelo.com/blog/?p=190
permalink: /backbone-js-workflow-mvc-and-backbones-version-of-mv/
categories:
  - web development
---
## Traditional MVC workflow

[<img class="alignleft size-medium wp-image-191" src="http://i2.wp.com/www.lesliepajuelo.com/blog/wp-content/uploads/2015/10/MVC-236x300.png?fit=236%2C300" alt="flowchart showing relationships" srcset="http://i0.wp.com/www.lesliepajuelo.com/blog/wp-content/uploads/2015/10/MVC.png?resize=236%2C300 236w, http://i0.wp.com/www.lesliepajuelo.com/blog/wp-content/uploads/2015/10/MVC.png?w=516 516w" sizes="(max-width: 236px) 100vw, 236px" data-recalc-dims="1" />](http://i0.wp.com/www.lesliepajuelo.com/blog/wp-content/uploads/2015/10/MVC.png)Separation of concerns is a huge, concern, when building larger applications. In previous projects backbone was used behind the scenes but quickly came to the forefront as we were to build a music player with it. The workflow on the left is how the MVC model works. The DOM, usually a webpage of some sort receives an event, say a click, and that is sent to a controller which sends an intent to the model. The model as its name implies models the data. It can be a database, JSON, or text file. Once change is done to the data an event is sent to the view. the view has a listner usually coded as:

`thisView.on("change", doThis(){})`

The View then updates the DOM. There is a clear workflow and each action and reaction is separate. In this system if the webpage were to listen for swipes on a phone instead of a click only the event listener for the click would need to change. Everything else keeps chugging along.

&nbsp;

&nbsp;

&nbsp;

[<img class="alignright size-medium wp-image-204" src="http://i0.wp.com/www.lesliepajuelo.com/blog/wp-content/uploads/2015/11/Screenshot-from-2015-11-01-185232-211x300.png?fit=211%2C300" alt="Backbone workflow including routers" srcset="http://i1.wp.com/www.lesliepajuelo.com/blog/wp-content/uploads/2015/11/Screenshot-from-2015-11-01-185232.png?resize=211%2C300 211w, http://i1.wp.com/www.lesliepajuelo.com/blog/wp-content/uploads/2015/11/Screenshot-from-2015-11-01-185232.png?w=428 428w" sizes="(max-width: 211px) 100vw, 211px" data-recalc-dims="1" />](http://i1.wp.com/www.lesliepajuelo.com/blog/wp-content/uploads/2015/11/Screenshot-from-2015-11-01-185232.png)

## Backbone MV* workflow

<img class="alignleft size-medium wp-image-200" src="http://i2.wp.com/www.lesliepajuelo.com/blog/wp-content/uploads/2015/11/Screenshot-from-2015-11-01-184451-229x300.png?fit=229%2C300" alt="Flowchart showing backbone workflow with collections" srcset="http://i0.wp.com/www.lesliepajuelo.com/blog/wp-content/uploads/2015/11/Screenshot-from-2015-11-01-184451.png?resize=229%2C300 229w, http://i0.wp.com/www.lesliepajuelo.com/blog/wp-content/uploads/2015/11/Screenshot-from-2015-11-01-184451.png?w=370 370w" sizes="(max-width: 229px) 100vw, 229px" data-recalc-dims="1" />As you can see there is no Controller. Instead the View takes on that role, both receiving intents from the DOM and updating it. Additionally, there is this other structure called Collections. These collections can hold many models.

You&#8217;d want to put your models into collections to help you handle several related models. IT allows for loading them, saving the new models to the server and provides helper functions. It is an iterate array-like structure which allows for methods to be performed on the models. They also have their own events  which can listen for changes to any model from one location in code.

A more complete diagram on the right shows how a router handles the incoming HTTP requests.

Other than giving handy constructors there is the `.extend` method for subclassing which includes initialize and defaults for properties. Backbone is flexible and you can add any other methods on the prototype.

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;