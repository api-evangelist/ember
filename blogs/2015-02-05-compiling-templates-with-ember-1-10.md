---
title: "Compiling templates with Ember 1.10"
url: "https://blog.emberjs.com/compiling-templates-in-1-10-0"
date: "Thu, 05 Feb 2015 00:00:00 GMT"
author: ""
feed_url: "https://blog.emberjs.com/rss.xml"
---
As many of you know, Ember 1.10 will be the first version of Ember that uses HTMLBars as its templating engine. With this change you may need to change the way you compile your templates. The HTMLBars API is evolving and not 1.0.0 yet, so to ensure that templates are compiled compatibly with your Ember version we have updated the Ember build system to generate a ember-template-compiler.js file alongside every build of Ember.
