---
layout: post
title: Jekyll up
description: "Revamping a personal blog for performance"
modified: 2016-08-12
tags: [performance]
categories: [performance]
---

### Paragon of slowness

I recently went to [ForwardJS workshop, Extreme Web Performance](https://forwardjs.com/#extreme-web-performance-55) with Rob Firtman. That got me thinking about my mostly abandoned blog/portfolio site (here). One of the measurements discussed was the [Google RAIL Performance Model](https://developers.google.com/web/tools/chrome-devtools/profile/evaluate-performance/rail). 

![Response Animation Idle Loading](LesliePajuelo.github.io/images/RAIL.png)

The biggest lesson for me was getting the website to be loaded, or percieved to be loaded, in a second. That got me thinking, how does my trusty/rusty blog doing? **badly**

Using [webpagetest](www.webpagetest.org) my load time was 4.4 seconds, 2.8 on repeat views. With an initial view [speed index](https://sites.google.com/a/webpagetest.org/docs/using-webpagetest/metrics/speed-index) of 3045. Honestly, at 4 seconds to load the first time there won't be any repeat viewers. [Here are the results](https://www.webpagetest.org/result/160812_G5_1P06/), for as long as they're cached.  Now my old blog is some WordPress theme I downloaded years ago and just put up to have a place to write to myself.

Certainly, I could do better now, especially if I ditched wordpress. So I started over with a simple theme, this time using a Jekyll and GitHub pages to host. Same content, same images, different platform.

[**RESULTS**](https://www.webpagetest.org/result/160812_FS_1NWE/) 

Disheartening, 2.9s and 2.1 on repeat view, with an initial speed index of 1360. Which made me feel better as I'd heard from people in the know that 1500 speed index was good to shoot for.

![incriminating evidence](LesliePajuelo.github.io/images/waterfall.png)
The main culprit is share.yandex.ru... no idea what that is, except I've just learned an important lesson in using ready-made-themes.

The second culprit is a mystery gap in downloads between 0.8s and 1.3s. That's nearly half the time that's budgeted!

Third, fonts. For some reason, I have 3 different web fonts and to my eye, they look identical.

Over the weekend I'll tackle these issues and document any others I find and post for next week.