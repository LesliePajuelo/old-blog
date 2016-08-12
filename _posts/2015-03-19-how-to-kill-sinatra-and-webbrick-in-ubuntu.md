---
id: 58
title: How to kill Sinatra and Webbrick in Ubuntu
date: 2015-03-19T01:43:35+00:00
author: Leslie
layout: post
guid: http://www.lesliepajuelo.com/blog/?p=58
permalink: /how-to-kill-sinatra-and-webbrick-in-ubuntu/
categories:
  - ubuntu
---
Soooo <ctrl-C> stopped stopping my server I&#8217;m testing my baby webapp in. Kill is the obvious solution but how to find the PID? Netstat to the rescue!

[<img src="http://i0.wp.com/www.lesliepajuelo.com/blog/wp-content/uploads/2015/05/Screenshot-from-2015-05-09-184359-1024x158.png?fit=580%2C89" alt="Screenshot from 2015-05-09 18:43:59" class="aligncenter size-large wp-image-59" srcset="http://i0.wp.com/www.lesliepajuelo.com/blog/wp-content/uploads/2015/05/Screenshot-from-2015-05-09-184359.png?resize=1024%2C158 1024w, http://i0.wp.com/www.lesliepajuelo.com/blog/wp-content/uploads/2015/05/Screenshot-from-2015-05-09-184359.png?resize=300%2C46 300w, http://i0.wp.com/www.lesliepajuelo.com/blog/wp-content/uploads/2015/05/Screenshot-from-2015-05-09-184359.png?w=1154 1154w" sizes="(max-width: 580px) 100vw, 580px" data-recalc-dims="1" />](http://i0.wp.com/www.lesliepajuelo.com/blog/wp-content/uploads/2015/05/Screenshot-from-2015-05-09-184359.png)

That is:
  
`sudo netstat -lp |grep 4567`
  
Then after a few minutes the PID is all the way to the right.
  
`sudo kill -9 2991`

The -lp flag is the linux process which is what&#8217;s generating the PIDs.
  
The -9 flag on kill is an exit that cannot be blocked.