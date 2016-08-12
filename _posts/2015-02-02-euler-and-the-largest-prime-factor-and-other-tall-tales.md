---
id: 8
title: Euler and the largest prime factor and other tall tales
date: 2015-02-02T18:09:45+00:00
author: Leslie
layout: post
guid: http://www.lesliepajuelo.com/blog/?p=8
permalink: /euler-and-the-largest-prime-factor-and-other-tall-tales/
categories:
  - Uncategorized
---
[<img class="aligncenter size-full wp-image-9" src="http://i2.wp.com/www.lesliepajuelo.com/blog/wp-content/uploads/2015/02/Euler.png?fit=260%2C54" alt="Euler" data-recalc-dims="1" />](http://projecteuler.net/)

&nbsp;

After an installfest and some simple, if grindy, html/css lessons [Project Odin](http://theodinproject.com) has made it to javascript. They linked the first section of Codeacademy&#8217;s javascript section plus a &#8220;choose your own adventure&#8221; game which really made sure you got the point of if loops.

The homework was then the 1st three [Project Euler](http://projecteuler.net) problems. Now, Euler asks that solutions aren&#8217;t posted so everyone can have fun playing. However, for the beginning problems I&#8217;m sure that [Stack Overflow](http://stackoverflow.com) is full of solutions. As the title suggests I had problems with:

[<img class="aligncenter wp-image-10 size-full" src="http://i0.wp.com/www.lesliepajuelo.com/blog/wp-content/uploads/2015/02/Screenshot-from-2015-02-01-212456.png?fit=555%2C180" alt="Euler problem" srcset="http://i0.wp.com/www.lesliepajuelo.com/blog/wp-content/uploads/2015/02/Screenshot-from-2015-02-01-212456.png?w=555 555w, http://i0.wp.com/www.lesliepajuelo.com/blog/wp-content/uploads/2015/02/Screenshot-from-2015-02-01-212456.png?resize=300%2C97 300w" sizes="(max-width: 555px) 100vw, 555px" data-recalc-dims="1" />](http://i0.wp.com/www.lesliepajuelo.com/blog/wp-content/uploads/2015/02/Screenshot-from-2015-02-01-212456.png)

&nbsp;

Factors, my old nemesis had returned. I&#8217;m not sure why but I never really learned how to factor numbers. I switched schools a few times in elementary and missed it. By the time they popped up again there was a fancy [TI-82](http://www.amazon.com/gp/product/B00000JBO8/ref=as_li_qf_sp_asin_il_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=B00000JBO8&linkCode=as2&tag=lesliepajuelo-20&linkId=MQVTVG56URQTDWVE) graphing calculator.

### Approach to solving:

Iterate through a range of numbers and test which are prime.

  1. Create function for prime/composite
  2. Loop through ALL the numbers
  3. Realize I should figure out a way to not do ALL the numbers.

On 1: Funny factoid, all prime numbers are neighbors with multiples of 6. Thank you Academic Decathalon.

Wikipedia provides this:

<h3 style="padding-left: 120px;">
  <span id="Trial_division" class="mw-headline">Trial division</span>
</h3>

<p style="padding-left: 120px;">
  The most basic method of checking the primality of a given integer <i>n</i> is called <i><a title="Trial division" href="http://en.wikipedia.org/wiki/Trial_division">trial division</a></i>. This routine consists of dividing <i>n</i> by each integer <i>m</i> that is greater than 1 and less than or equal to the <a title="Square root" href="http://en.wikipedia.org/wiki/Square_root">square root</a> of <i>n</i>.&#8221;
</p>

So, _n_ is our number 600,851,475,143 and _m_ is everything up to, but not including 24,5145. It&#8217;d still be nice to exclude more numbers, say multiples of 2, 3, and 5.

if     ( the remainder (%) is exactly equal(===) to 0) {then it&#8217;s not prime}.

<pre>if (n % 2 === 0 || n % 3 === 0|| n % 5 === 0) {return false;}</pre>

//In javascript there&#8217;s a difference between == and === mainly that with == it tries to figure out the types. The [Brackets.io](http://brackets.io/) delinter is adamant about that. And it&#8217;s not bad practice. For readability it also enforces a space between operators and operands.

&nbsp;

For (a number, let&#8217;s say 5 we square it, check that it&#8217;s smaller&#8230;. then skip down and do the stuff below. Which is

if the test number divides evenly into the number we&#8217;re testing or (||) adding 2 makes that possible (getting us the neighbor of 6) then it&#8217;s not prime. Come back to the &#8220;for&#8221; line and add 6 more numbers to m so we do fewer tests and continue. Otherwise it&#8217;s prime! whoo!

&nbsp;

<pre class="de1"><span class="kw1">for</span> <span class="br0">(</span><span class="kw1">var</span>  m <span class="sy0">=</span> <span class="nu0">5</span><span class="sy0">;</span> m <span class="sy0">*</span> m <span class="sy0">&lt;=</span> n<span class="sy0">;</span> m <span class="sy0">+=</span> <span class="nu0">6</span><span class="br0">)</span> <span class="br0">{</span>
        <span class="kw1">if</span> <span class="br0">(</span>n <span class="sy0">%</span> m <span class="sy0">===</span> <span class="nu0"></span> <span class="sy0">||</span> n <span class="sy0">%</span> <span class="br0">(m</span> <span class="sy0">+</span> <span class="nu0">2</span><span class="br0">)</span> <span class="sy0">===</span> <span class="nu0"></span><span class="br0">)</span> <span class="br0">{</span> <span class="kw1">return</span> <span class="kw2">false</span><span class="sy0">;</span> <span class="br0">}</span>
    <span class="br0">}</span>
    <span class="kw1">return</span> <span class="kw2">true</span><span class="sy0">;</span>
<span class="br0">}


</span></pre>

On to 2: Now, who knew javascript could do arrays&#8230;wasn&#8217;t covered in the &#8220;reading list&#8221; for the day. Tho was on the top of the Odin page for &#8220;points to ponder&#8221;. For some reason I thought lists were it. But no, it&#8217;s super easy to push into an array.

Lots of thing in common with lists actually. There&#8217;s array.valueOf() and array.join(). But best of all array.push() and array.pop()

<pre>factors = [];</pre>

while (num > 1; isPrime(num); i++){

factors.push(num);

}

return factors.pop()

It was embarrassingly long to think of looking up whether javascript had arrays.