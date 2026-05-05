---
title: "Announcing the Ember.js Security Policy"
url: "https://blog.emberjs.com/announcing-the-ember-security-policy"
date: "Fri, 05 Apr 2013 00:00:00 GMT"
author: ""
feed_url: "https://blog.emberjs.com/rss.xml"
---
<p>We know that building your apps on top of a framework requires
trust, and that trust is never put to the test more than when security
vulnerabilities are discovered.</p>
<p>While we're very fortunate to work on an open source project that runs
in a sandboxed environment, the browser, we realize that even JavaScript
applications can be vulnerable to attacks from malicious third-parties.</p>
<p>Ember.js is designed to mitigate common forms of attack. For example,
all values rendered using Handlebars are automatically escaped to
prevent XSS attacks, and developers must explicitly opt in to outputting
raw HTML.</p>
<p>To ensure that Ember applications stay safe, today we're announcing the
<a href="/security">Ember.js Security Policy</a>, to help security researchers and
developers responsibly disclose potential vulnerabilities in Ember and
Ember Data.</p>
<p>We have also set up the <a href="https://groups.google.com/forum/#!forum/ember-security">Ember.js security announcements mailing
list</a>. This is
an extremely low-traffic mailing list reserved solely for announcing
security releases of the framework. If you're deploying Ember to
production, you or your security team may wish to subscribe.</p>
<p>To be clear, there are no vulnerabilities we're aware of at this time
and there is not a security release forthcoming. We take security
extremely seriously and believe that having a procedure in place ahead of
time will allow us to respond most effectively should the
worst happen.</p>
<p>If you have any questions or concerns that are not addressed by the new
security policy, please email us at
<a href="mailto:security@emberjs.com">security@emberjs.com</a>.</p>
<p>I'd like to thank the Ruby on Rails security team, from whom our
security policy was lifted almost wholesale, for serving as a role model
for open source projects everywhere.</p>
<p>Lastly, my personal thanks to <a href="https://twitter.com/tenderlove">Aaron "tenderlove"
Patterson</a> and <a href="https://twitter.com/bascule">Tony "bascule"
Arcieri</a> for reviewing our policy and
answering many of my ignorant questions.</p>
<p>Let's stay safe out there.</p>
