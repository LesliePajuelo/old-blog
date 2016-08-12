---
id: 124
title: Ternary Operators or Conditional Operators
date: 2015-08-28T02:18:08+00:00
author: Leslie
layout: post
guid: http://www.lesliepajuelo.com/blog/?p=124
permalink: /ternary-operators-or-conditional-operators/
categories:
  - Uncategorized
---
Ternary operators are a short way to write if/else statements.

`if(value === 17){<br />
return true;<br />
} else {<br />
return false;}`

Would be written like:

`return value === 17 ? true : false;`

In english it&#8217;s: If value is strictly equal to 17 ? return true : else return false They&#8217;re great for making short code and are fairly easy to read in one line for a simple if/else statement. Nesting ternary operators is harder to read. My suggestion is to read it aloud or deliberately in your head to understand it.
  
`value = option === 0 ? true :<br />
option ==== 1 ? newValue :<br />
false;`
  
The &#8220;more readable&#8221; way to write that is:
  
`if (m_seedsfilter == 0)<br />
{<br />
value = true;<br />
}<br />
else if (m_seedsfilter == 1)<br />
{<br />
value = newValue;<br />
}<br />
else<br />
{<br />
value = false;<br />
}`