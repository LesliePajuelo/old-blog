---
id: 209
title: POST methods in bare nodejs, sql, and with sequelizejs
date: 2015-11-02T03:27:11+00:00
author: Leslie
layout: post
guid: http://www.lesliepajuelo.com/blog/?p=209
permalink: /post-methods-in-bare-nodejs-sql-and-with-sequelizejs/
categories:
  - HackReactor
---
Today we&#8217;ll examine three different ways to store messages with Node. First to an array, then to mysql, then to mysql with Sequalize.js

Normally, the response would also be abstracted out as a separate function.

<pre>'POST': function(request, response){
      collectData(request, function(message){
      messages.push(message);
     
      response.writeHead(200, {'Content-type': 'application/json', "access-control-allow-methods;: 'GET','POST'"});
      response.end();
    });</pre>

<pre>collectData = function(request, callback){
  var data = "";
  request.on('data', function(chunk){
    data += chunk;
  });
  request.on('end', function(){
    callback(JSON.parse(data));
  });
</pre>

What is happening is that when a POST request comes in the incoming data is first parsed with the collectData function. the `request.on('data', callback)` is being held open as each 7 kB packet of data comes in. It will continue to aggregate those chunks into the data variable until the `request.on('end', callback)` message is received only then will it pass it to the `messages.push(message) which will of course append our now complete message to the messages array.`

The same method might be written like this

<pre>POST: function (req, res) {
      collectData(req.body, function(message){
       var querySQL = ("INSERT INTO messages VALUES (message)";";
       database.query(querySQL,[optional paramaters], callback){
        callback(  
        response.writeHead(200, {'Content-type': 'application/json', "access-control-allow-methods:'POST'"});
        response.end();
      });
    });
  };,</pre>

Lastly, with <a href="http://docs.sequelizejs.com/en/latest/" target="_blank">sequelize.js</a> an ORM (Object Relational Model) which is used instead of writing SQL for both database and table construction but also for data manipulation.

<pre>post: function (req, res, callback) {
      var user = req.body
      var newUser = db.users.build({ username: user.username });
      newUser.save().then( callback );
      
     res.writeHead(201, {'Content-type': 'application/json', "access-control-allow-methods:'POST'"});
     res.end(data);
    }
  }</pre>