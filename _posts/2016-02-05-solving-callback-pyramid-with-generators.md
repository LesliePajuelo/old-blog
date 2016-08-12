---
id: 389
title: Solving callback pyramid with generators
date: 2016-02-05T17:45:02+00:00
author: Leslie
layout: post
guid: http://www.lesliepajuelo.com/blog/?p=389
permalink: /solving-callback-pyramid-with-generators/
dsq_thread_id:
  - 4786678126
categories:
  - web development
---


Callbacks in javascript are functions which are executed after another function is executed. If this sounds confusing and you&#8217;re not sure what I&#8217;m talking about, go to <a href="http://javascriptissexy.com/understand-javascript-callback-functions-and-use-them/" target="_blank">Javascript is Sexy</a> then play around in the console, then build something with node, then come back when you see the problem. It&#8217;s easy to create a pyramid of callbacks when doing any work which needs to be async such as file operations, if you need inspiration for a project code out the following pseudocode using callbacks.

    
    //Read a file with a list of page
      //store the results in an array
      //Check if the page is already on the disk
        //if not, get a copy of the page
          //save the page to the filesystem
        //regardless, open the page in the browser.
    

The standard ES5 solution to callback pyramid is to use a promise library such as <a href="http://bluebirdjs.com/docs/getting-started.html" target="_blank">bluebird</a> or <a href="http://documentup.com/kriskowal/q/" target="_blank">Q</a>.

Using promises the all callback <a href="https://github.com/kriskowal/q" target="_blank">pyramids look like</a>:

    
    Q.fcall(promisedStep1)
    .then(promisedStep2)
    .then(promisedStep3)
    .then(promisedStep4)
    .then(function (value4) {
        // Do something with value4
    })
    .catch(function (error) {
        // Something went horribly wrong somewhere
    })
    .done();
    

Which is fine, but now all the code is spreadout, not necessarily in the order used in the promise block making it harder to really understand what is going on.

To use generators let&#8217;s first code out what this problem would look like synchronously.

    
    var downloadPages = function (){
      // Read the file which contains the page list
      var list = fs.readFile('./sites.txt', 'utf8');
    
      // Store it in array
      var urls = list.res.toString().split('\n');
    
      for (var i = 0, l = urls.length; i < l; i ++) {
        // Check each page if it's already saved on the disk
        var file = fs.readFile ('./' + urls[i] + '.html', 'utf8');
        if (file.err) {
          // If not, get copy of the page
          var webPage = scrapePage('http://' + urls[i]);
          // Save it to disk
          fs.writeFile('./' + urls[i] + '.html', webPage.res);
          // After saving, open it on the browser
          open('./' + urls[i] + '.html', 'firefox');
        } else {
          //If it's already on disk, open it in browser
          open('./' + urls[i] + '.html', 'firefox');
        }
      }
    };

&nbsp;

Ok ok, fs.readFile and fs.writeFile are asynch, I just didn&#8217;t include the callbacks. Let&#8217;s just move forward and convert it to a generator by adding an asterisk

     var downloadPages = function* (){

That plus sprinkle a few yield keywords before every async call

    
    var downloadPages = function* (){
      var list = yield fs.readFile('./sites.txt', 'utf8');
    
      var urls = list.res.toString().split('\n');
    
      for (var i = 0, l = urls.length; i < l; i ++) {
        var file = yield fs.readFile('./' + urls[i] + '.html', 'utf8');
        if (file.err) {
          var webPage = yield scrapePage('http://' + urls[i]);
          yield fs.writeFile('./' + urls[i] + '.html', webPage.res);
          open('./' + urls[i] + '.html', 'firefox');
        } else {
          open('./' + urls[i] + '.html', 'firefox');
        }
      }
    };

And that is it! Even better support for async is coming <a href="https://tc39.github.io/ecmascript-asyncawait/" target="_blank">next year with ES7!</a>