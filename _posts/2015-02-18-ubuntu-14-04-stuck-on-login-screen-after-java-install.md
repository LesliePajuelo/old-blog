---
id: 34
title: Ubuntu 14.04 stuck on login screen after java install
date: 2015-02-18T23:23:12+00:00
author: Leslie
layout: post
guid: http://www.lesliepajuelo.com/blog/?p=34
permalink: /ubuntu-14-04-stuck-on-login-screen-after-java-install/
categories:
  - ubuntu
---
It should have been expected. I messed with a system file and the system bit back.

Instead of downloading and installing JDK 7 I looked for a ppa or other apt-get method for getting it installed. Allegedly, there&#8217;s now an Ubuntu Developer Tools Center. Unfortunately, I&#8221;m getting an error about not being able to parse the website it&#8217;s pointing to. An already reported bug in launchpad.

So, I followed [this tutorial by Koen Vlaswinkle](https://www.digitalocean.com/community/tutorials/how-to-install-java-on-ubuntu-with-apt-get) which was a nicely formatted version of other walkthroughs.

`sudo apt-get install default-jdk`

and to install the Oracle JDK as opposed to OpenJDK7

``It should have been expected. I messed with a system file and the system bit back.

Instead of downloading and installing JDK 7 I looked for a ppa or other apt-get method for getting it installed. Allegedly, there&#8217;s now an Ubuntu Developer Tools Center. Unfortunately, I&#8221;m getting an error about not being able to parse the website it&#8217;s pointing to. An already reported bug in launchpad.

So, I followed [this tutorial by Koen Vlaswinkle](https://www.digitalocean.com/community/tutorials/how-to-install-java-on-ubuntu-with-apt-get) which was a nicely formatted version of other walkthroughs.

`sudo apt-get install default-jdk`

and to install the Oracle JDK as opposed to OpenJDK7

`` 

```It should have been expected. I messed with a system file and the system bit back.

Instead of downloading and installing JDK 7 I looked for a ppa or other apt-get method for getting it installed. Allegedly, there&#8217;s now an Ubuntu Developer Tools Center. Unfortunately, I&#8221;m getting an error about not being able to parse the website it&#8217;s pointing to. An already reported bug in launchpad.

So, I followed [this tutorial by Koen Vlaswinkle](https://www.digitalocean.com/community/tutorials/how-to-install-java-on-ubuntu-with-apt-get) which was a nicely formatted version of other walkthroughs.

`sudo apt-get install default-jdk`

and to install the Oracle JDK as opposed to OpenJDK7

``It should have been expected. I messed with a system file and the system bit back.

Instead of downloading and installing JDK 7 I looked for a ppa or other apt-get method for getting it installed. Allegedly, there&#8217;s now an Ubuntu Developer Tools Center. Unfortunately, I&#8221;m getting an error about not being able to parse the website it&#8217;s pointing to. An already reported bug in launchpad.

So, I followed [this tutorial by Koen Vlaswinkle](https://www.digitalocean.com/community/tutorials/how-to-install-java-on-ubuntu-with-apt-get) which was a nicely formatted version of other walkthroughs.

`sudo apt-get install default-jdk`

and to install the Oracle JDK as opposed to OpenJDK7

`` 

``` 

Where I got into problems was in setting &#8220;JAVA_HOME&#8221; since it was &#8220;needed by some programs&#8221; I figured why not. It involved editing /etc/environment and replacing the line that was there. Which was:

<pre>PATH="/usr/local/sbin:/usr/local/bin:/usr/bin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games"
</pre>

All good until restart when it was stuck on a login screen. It&#8217;d take my correct password and loop back around.

<pre>&lt;ctrl&gt;&lt;alt&gt;&lt;F2&gt;
</pre>

To get to command line/terminal and then to undo what I tried to do by changing PATH.

<pre>sudo nano /etc/environment

&lt;ctrl&gt;-o to "write out" or save

startx

</pre>

And then all was good in the world again. Hopefully, no program I run across will need the path changed.