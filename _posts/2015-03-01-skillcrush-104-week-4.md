---
id: 56
title: Skillcrush 104 week 4
date: 2015-03-01T00:45:48+00:00
author: Leslie
layout: post
guid: http://www.lesliepajuelo.com/blog/?p=56
permalink: /skillcrush-104-week-4/
dsq_thread_id:
  - 4142607707
categories:
  - Uncategorized
---
## Github, gems, and a webapp

## Gems!

OK we learned about gems and how they&#8217;re basically libraries. The main advantage it seems is that there&#8217;s a centralized repository of ruby gems and that they can be added to a gemfile which automagically downloads the require gems for your app.

### Nokigiri

A scrapper which has search functions and it&#8217;s possible to specify where you&#8217;re looking for through the DOM. This example was an exercise to find the ingredients for recipes on the martha stewart site:
  
`require 'nokogiri'<br />
require 'open-uri'`
  
``## Github, gems, and a webapp

## Gems!

OK we learned about gems and how they&#8217;re basically libraries. The main advantage it seems is that there&#8217;s a centralized repository of ruby gems and that they can be added to a gemfile which automagically downloads the require gems for your app.

### Nokigiri

A scrapper which has search functions and it&#8217;s possible to specify where you&#8217;re looking for through the DOM. This example was an exercise to find the ingredients for recipes on the martha stewart site:
  
`require 'nokogiri'<br />
require 'open-uri'`
  
`` 

We also used Twilio and sending a text to my phone was amazing! Somehow will play more with this. Tho it was a brief foray the documentation at Twilio is great.

### webapp. Yahoo-weatherman

So, the &#8220;capstone&#8221; of the 104 class was to create a console app which used a gem to pull weather for a day and for a 5 day forecast.

[Rubygems.org](https://rubygems.org/gems/yahoo-weather/versions/1.2.0) is amazing. However, it the documentation varies in quality.  For some reason just accessing the gem was difficult for me.

The documentation has:
  
`require 'rubygems'<br />
require 'yahoo-weather'`
  
```## Github, gems, and a webapp

## Gems!

OK we learned about gems and how they&#8217;re basically libraries. The main advantage it seems is that there&#8217;s a centralized repository of ruby gems and that they can be added to a gemfile which automagically downloads the require gems for your app.

### Nokigiri

A scrapper which has search functions and it&#8217;s possible to specify where you&#8217;re looking for through the DOM. This example was an exercise to find the ingredients for recipes on the martha stewart site:
  
`require 'nokogiri'<br />
require 'open-uri'`
  
``## Github, gems, and a webapp

## Gems!

OK we learned about gems and how they&#8217;re basically libraries. The main advantage it seems is that there&#8217;s a centralized repository of ruby gems and that they can be added to a gemfile which automagically downloads the require gems for your app.

### Nokigiri

A scrapper which has search functions and it&#8217;s possible to specify where you&#8217;re looking for through the DOM. This example was an exercise to find the ingredients for recipes on the martha stewart site:
  
`require 'nokogiri'<br />
require 'open-uri'`
  
`` 

We also used Twilio and sending a text to my phone was amazing! Somehow will play more with this. Tho it was a brief foray the documentation at Twilio is great.

### webapp. Yahoo-weatherman

So, the &#8220;capstone&#8221; of the 104 class was to create a console app which used a gem to pull weather for a day and for a 5 day forecast.

[Rubygems.org](https://rubygems.org/gems/yahoo-weather/versions/1.2.0) is amazing. However, it the documentation varies in quality.  For some reason just accessing the gem was difficult for me.

The documentation has:
  
`require 'rubygems'<br />
require 'yahoo-weather'`
  
``` 
  
`<br />
print<br />
{response.temp}`

Which seems straight forward but I couldn&#8217;t get it to work. Luckily Skillcrush to the rescue and there was a partial example:
  
`<br />
require 'yahoo_weatherman’`

`client = Weatherman::Client.new`

weather = client.lookup\_by\_location(&#8216;90210&#8217;)
  
weather.temp
  
</code>

Which is to say, what the hell with the curly brackets on the doc? Basically my fault for just copying without understanding everything.