---
title: "Upcoming deprecation of baseURL in Ember CLI 2.7"
url: "https://blog.emberjs.com/baseURL"
date: "Thu, 28 Apr 2016 00:00:00 GMT"
author: ""
feed_url: "https://blog.emberjs.com/rss.xml"
---
The baseURL configuration option and the accompanying <base> tag in Ember CLI applications are often and tragically misunderstood. There have been at least 67 issues opened for Ember CLI referencing baseURL , making it one of the most common points of discussion. As a result, in Ember CLI's canary channel, we have deprecated baseURL and removed the default <base> inside of index.html .
