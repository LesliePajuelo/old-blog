---
id: 14
title: 'jQuery/Highcharts won&#8217;t work on my desktop D:'
date: 2015-02-04T12:21:51+00:00
author: Leslie
layout: post
guid: http://www.lesliepajuelo.com/blog/?p=14
permalink: /jqueryhighcharts-wont-work-on-my-desktop-d/
categories:
  - ubuntu
---
It&#8217;s not a problem with either of those. It&#8217;s a security setting in chrome.

launch from Terminal:

<pre>google-chrome -allow-file-access-from-files
</pre>

It&#8217;s an [old problem](https://code.google.com/p/chromium/issues/detail?id=40787&q=ajax%20local&colspec=ID%20Stars%20Pri%20Area%20Feature%20Type%20Status%20Summary%20Modified%20Owner%20Mstone%20OS) that is &#8220;fixed&#8221; by the flag. I&#8217;ve ran into it before but forgot how I fixed it, before I had just gotten in the habit of running everything on a LAMP. Since my recent upgrade to Trusty Tahr it wasn&#8217;t installed. Oops