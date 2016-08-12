---
id: 40
title: ERB the templator
date: 2015-03-16T23:05:47+00:00
author: Leslie
layout: post
guid: http://www.lesliepajuelo.com/blog/?p=40
permalink: /erb-the-templator/
categories:
  - Uncategorized
---
ERB is used to generate HTML, XML, RSS and many more acronyms, I&#8217;m sure.

So far I&#8217;ve used it only for HTML.

To use ERB:

  1. require &#8216;erb&#8217; at the top of the file or in a gemfile
  2. add the specifc erb file at the end of the get
  3. create an erb file in a /views folder

<p style="padding-left: 30px;">
  Using Sinatra generating a page from a ruby script is simple:<br /> <code>get '/' do&lt;br />
&lt;content&gt;&lt;br />
end</code>
</p>

To use an erb template it changes to:

<p style="padding-left: 30px;">
  <code>get '/' do&lt;br />
@instance_variable = method_of_interest(variable)</code>
</p>

<p style="padding-left: 30px;">
  <code>erb :layout&lt;br />
end</code>
</p>

The layout.erb file will have the boilerplate HTML

<p style="padding-left: 30px;">
  <!DOCTYPE html>
</p>

<p style="padding-left: 30px;">
  <html><br /> <head>
</p>

<p style="padding-left: 30px;">
  <meta charset = &#8220;utf-8&#8221;><br /> <title>App</title><br /> </head>
</p>

<p style="padding-left: 30px;">
  <body>
</p>

<p style="padding-left: 30px;">
  <%= yield %>
</p>

<p style="padding-left: 30px;">
  </body><br /> </html>
</p>

The <%= yield %> is important because that allows for a single layout.erb with the structural HTML and then individual newpage.erb files which will override the yield and post their own content.