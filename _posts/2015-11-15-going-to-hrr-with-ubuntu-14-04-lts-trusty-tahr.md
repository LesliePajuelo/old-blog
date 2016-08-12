---
id: 215
title: Going to HRR with Ubuntu 14.04 LTS, Trusty Tahr
date: 2015-11-15T01:15:12+00:00
author: Leslie
layout: post
guid: http://www.lesliepajuelo.com/blog/?p=215
permalink: /going-to-hrr-with-ubuntu-14-04-lts-trusty-tahr/
dsq_thread_id:
  - 4319617981
categories:
  - HackReactor
  - ubuntu
---
The highly recommended computer for Hack Reactor is a mac. Not only is it recommended on the assignments when directions are given they are mac only. Which is mostly fine if you’re on a *nix system. Keep in mind that help desk is staffed by more mac users. Out of the 60 or so students right now only 2 of us are on linux. So it’s best to be prepared and get everything installed and working correctly on day 1.

  1. node
  2. npm
  3. grunt
  4. bower
  5. mysql
  6. mongo

## Node and nvm

You’ll actually want nvm first as it’s a node version manager. With the big change of Node from 0.12 to 5.0 there are some other packages which haven’t caught up yet and you’ll need to switch between the two.

<pre>nvm
 curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.29.0/install.sh | bash</pre>

<pre>Now install node using nvm with
 nvm install 5.0
 nvm install 4.0
 nvm install 0.12.7</pre>

And pick a version before starting a project with

<pre>nvm use 5.0</pre>

npm
  
Use the trusty apt-get

<pre><span class="crayon-e">sudo </span><span class="crayon-v">apt</span><span class="crayon-o">-</span><span class="crayon-e">get </span><span class="crayon-e">install </span><span class="crayon-v">npm</span></pre>

Common problem:
  
Sometimes this process goes awry and you can then only use npm with sudo. While not horrible for your time at Hack Reactor not ideal either. If you have the time try to fix it

<pre>curl https://www.npmjs.org/install.sh | sh
 <a href="https://gist.github.com/isaacs/579814" target="_blank">More ideas by isaacs</a></pre>

## Grunt

You’ll install it locally on each project by running

<pre>npm install grunt --save</pre>

That’ll install it and save it to your package.json folder that npm creates on npm init.

## Bower

Same as above, local install on every project

## Mysql

Ubuntu has an official guide follow that until you run into problems

Common problems:
  
Last time I did it that way it installed an older version. Specify the one you want

<pre>sudo apt-get install mysql-server-5.6
 sudo apt-get install mysql-client-5.6</pre>

Yes, 5.7 is out but the homebrew kids on their macs are installing 5.6 and you’ll want the same as your partner.

Once installed check it out

<pre>mysql -u root -p</pre>

the first time it’ll prompt you for a password, which for HRR I recommend not setting as you will be sharing the db config files with your partner and you’ll have to change it on each build or remove the password later.
  
REMOVE MYSQL PASSWORD

<pre>mysqladmin -u root -p password ''</pre>

## Mongo

<pre>sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 7F0CEB10
 echo "deb http://repo.mongodb.org/apt/ubuntu trusty/mongodb-org/3.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.0.list
 sudo apt-get update
 sudo apt-get install -y mongodb-org</pre>

Then fire it up

<pre>sudo service mongod start</pre>

Common problems
   
Mongo runs great the first time then if it doesn’t shut down properly you’ll get
   
old lock file: \data\db\mongod.lock. probably means unclean shutdown
   
or
   
exception in initAndListen: 10309 Unable to create/open lock file: /data/mongod.lock errno:13 Permission denied Is a mongod instance already running?,
  
When there is clearly no other instances running and you have killed all the mongods

<pre>The answer is:
 sudo rm /data/db/mongod.lock</pre>

/data folder lives in your main File System folder. You get to it by cd .. twice