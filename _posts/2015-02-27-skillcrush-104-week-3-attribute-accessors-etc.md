---
id: 54
title: Skillcrush 104 week 3 Attribute accessors etc
date: 2015-02-27T00:32:05+00:00
author: Leslie
layout: post
guid: http://www.lesliepajuelo.com/blog/?p=54
permalink: /skillcrush-104-week-3-attribute-accessors-etc/
categories:
  - Uncategorized
---
OK instead of using set and get for each class we can use `attr_accessor`.

So the class looks like:
  
``OK instead of using set and get for each class we can use `attr_accessor`.

So the class looks like:
  
`` 

The : in front of the variables is a symbol
  
From ruby-doc.org we get this explanation:

> `Symbol` objects represent names and some strings inside the Ruby interpreter. They are generated using the `:name` and `:"string"` literals syntax, and by the various`to_sym` methods. The same `Symbol` object will be created for a given name or string for the duration of a program&#8217;s execution, regardless of the context or meaning of that name.

Which is to say thank you Skillcrush because that makes little sense. What I got was that a symbol represents a single address in memory. In a physical place. While strings, even if they have the same content is stored in separate places.

This is especially useful for hashes instead of using strings.

```OK instead of using set and get for each class we can use `attr_accessor`.

So the class looks like:
  
``OK instead of using set and get for each class we can use `attr_accessor`.

So the class looks like:
  
`` 

The : in front of the variables is a symbol
  
From ruby-doc.org we get this explanation:

> `Symbol` objects represent names and some strings inside the Ruby interpreter. They are generated using the `:name` and `:"string"` literals syntax, and by the various`to_sym` methods. The same `Symbol` object will be created for a given name or string for the duration of a program&#8217;s execution, regardless of the context or meaning of that name.

Which is to say thank you Skillcrush because that makes little sense. What I got was that a symbol represents a single address in memory. In a physical place. While strings, even if they have the same content is stored in separate places.

This is especially useful for hashes instead of using strings.

``` 
  
becomes

`variable = {:name = "kelly", :email = "kelly@gmail.com"}`

And so memory for the index value of the pair is created and stored once instead of for each.