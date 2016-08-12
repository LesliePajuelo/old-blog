---
id: 303
title: 'Ember.js 2.0 &#8211; Data down, actions up'
date: 2016-01-28T18:21:35+00:00
author: Leslie
layout: post
guid: http://www.lesliepajuelo.com/blog/?p=303
permalink: /ember-js-2-0-data-down-actions-up/
dsq_thread_id:
  - 4786679171
categories:
  - web development
---
## <a href="http://emberjs.com/" target="_blank">Ember.js</a> &#8211; Data binding

With that tagline it made it irresistible to try. It&#8217;s got a reputation for being difficult for beginners. Since it is meant for big apps it&#8217;s also difficult to find small examples. Another difficulty is that last summer they had a big 2.0 release which changed the &#8216;best practices&#8217; for data binding. However! The community is friendly and they strive for the out of the box functionality of Rails.

The new way of doing things is to set attributes on a component and to trigger actions from templates when the data needs to be changed.

There are many examples showing the old way `{{edit-student value= student.name}}`. The new way would be `{{edit-student value=(readonly student.name) on-name-change(action (mut student.name))}}`

Ember provides helpers for wrapping behavior on properties as they are passed to the component. `mut` is a helper that will provide an `update` helper which sets the student name. The <readonly> helper disables the `set` on the property which obligates the update to be initiated from an action.

&nbsp;