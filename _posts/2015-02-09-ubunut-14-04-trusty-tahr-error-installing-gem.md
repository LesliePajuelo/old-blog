---
id: 29
title: Ubunut 14.04 Trusty Tahr error installing gem
date: 2015-02-09T14:01:06+00:00
author: Leslie
layout: post
guid: http://www.lesliepajuelo.com/blog/?p=29
permalink: /ubunut-14-04-trusty-tahr-error-installing-gem/
categories:
  - ubuntu
---
I tried to install Ruby and Rails using [Railsbridge Installfest](http://installfest.railsbridge.org/installfest/linux?back=choose_your_operating_system "Installfest") guide. All went well until I tried to install the Rails gem.

At which point I got:

<pre>ExecJS::RuntimeUnavailable
</pre>

Thanks to [SO](http://stackoverflow.com/questions/7092107/rails-could-not-find-a-javascript-runtime) the solution is to install Node.js so it brings all the dependencies that RoR also needs.

&nbsp;

<pre><code class="language-bash">sudo add-apt-repository ppa:chris-lea/node.js
sudo apt-get update
sudo apt-get install nodejs
</code></pre>

[Another good tutorial which](https://gorails.com/setup/ubuntu/14.10) also mentions node.js. Tho it&#8217;s for the next version of Ubuntu.