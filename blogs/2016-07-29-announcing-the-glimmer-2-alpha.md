---
title: "Announcing The Glimmer 2 Alpha"
url: "https://blog.emberjs.com/announcing-the-glimmer-2-alpha"
date: "Fri, 29 Jul 2016 00:00:00 GMT"
author: ""
feed_url: "https://blog.emberjs.com/rss.xml"
---
<p>In this year's <a href="https://www.youtube.com/watch?v=OInJBwS8VDQ&amp;list=PL4eq2DPpyBblc8aQAd516-jGMdAhEeUiW">EmberConf keynote</a>,  Yehuda mentioned that we are working on a highly optimized rendering engine for Ember called Glimmer 2.</p>
<p>On behalf of all the contributors who have lent a hand along the way, I am very excited to announce that we have released Ember 2.9.0-alpha.1, the first official build with Glimmer 2 included.</p>
<h2 id="akeymilestone">🔑 A Key Milestone 🔑</h2>
<p>During the alpha testing period, we will publish new alpha builds on a weekly cadence, following the <a href="http://emberjs.com/builds/#/beta">beta releases schedule</a>. The alpha releases will be cut from the <code>master</code> branch, but with all <a href="https://guides.emberjs.com/v2.7.0/configuring-ember/feature-flags/">experimental features</a> other than <code>ember-glimmer</code> stripped from the builds.</p>
<p>The purpose of the alpha releases is to enable our community – especially the addon and tooling ecosystem – to start testing the new engine for compatibility and offer feedback. Needless to say, the alpha releases are not intended for production use.</p>
<p>To test your apps with the alpha builds, run <code>bower install --save ember#alpha</code> and follow the prompt to persist the resolution.</p>
<p>From Ember's perspective, integrating Glimmer 2 does not expose any new user-facing features. Even though it is a complete rewrite under the hood, <strong>we expect the final release to be a drop-in, completely backwards compatible upgrade</strong> for virtually all Ember users. Notably, we will follow our usual <a href="http://semver.org">SemVer</a> guarantee and ensure all public APIs continue to function as advertised. At this point, we do not expect to introduce any new deprecations along with the initial release.</p>
<p>That being said, despite our <a href="https://github.com/emberjs/ember.js/issues/13127">best efforts</a>, we might not have gotten every detail right in our very first attempt, hence the alpha releases. We would really appreciate it if you could start testing your applications and report any regressions. You may refer to the <a href="https://github.com/emberjs/ember.js/issues/13949">GitHub issue</a> for a list of known issues.</p>
<p>It is worth noting that the version number (2.9.0-alpha.1) does not imply the new engine will be automatically included in the 2.9 final release. Like any other changes, the Glimmer 2 integration is subject to the usual rigor and stability requirements of our <a href="http://emberjs.com/blog/2013/09/06/new-ember-release-process.html">release process</a>. The core team will make the final decision on when to promote the feature into beta and stable releases based on our learnings from the alpha period.</p>
<p>Based on current information, the 2.8-LTS release (when available) will likely be the final <a href="http://emberjs.com/blog/2016/02/25/announcing-embers-first-lts.html">LTS release</a> to include the current-generation rendering engine, which will be supported with critical bugfixes until at least May 2017 and security patches until at least October 2017.</p>
<h2 id="anoteonperformance">🚀 A Note On Performance 🚀</h2>
<p>While one of the overarching goals of Glimmer 2 is to improve performance, the immediate priority in the alpha phase is maximal compatibility. We are barely scratching the surface with the possible optimizations unlocked by the new engine, and once the dust settles there will be ample headroom for further improvements.</p>
<p>That being said, you should start seeing some improvements in rendering performance with each alpha release, as well as reduced download/parsing time thanks to the new templates serialization format.</p>
<p>We are also aware of a few minor bugs that cause performance problems in the first alpha release, which we plan to address quickly. However, it is also possible that we inadvertently regressed performance in certain scenarios. If you noticed certain common patterns have become slower, please report them as bugs.</p>
<p>As always – when running performance benchmarks, <strong>please make sure you are using the minified production build</strong> (<code>ember.min.js</code>). The debug builds contain a lot of helpful development aids that are known to impact performance negatively.</p>
<h2 id="awholelotmoretocome">🎁 A Whole Lot More To Come 🎁</h2>
<p>Besides performance, Glimmer 2 has laid a solid foundation for us to build on.</p>
<p>The project originally started when Tom, Yehuda and I spiked on implementing "angle bracket components" in the HTMLBars ("Glimmer 1") engine over a year ago. This exercise highlighted some fundamental misalignments between the current rendering stack and the direction Ember is headed.</p>
<p>While HTMLBars handled basic templating, it left the implementation of many of Ember's view layer features (notably components) up to Ember itself. Not only did it make new features more difficult to implement, it made it hard to implement them <em>efficiently</em> out of the gate.</p>
<p>As Ember has moved towards components and "data-down, actions-up", we wanted to do many optimizations that weren't a good fit for the HTMLBars architecture. The lessons we learned from the spike ultimately leading us down the journey that is now known as the Glimmer 2 architecture. The underlying technologies are very interesting, but I will save those details for another time.</p>
<p><strong>As an Ember user, you can expect the new engine to unlock some long-awaited features</strong>, such as FastBoot rehydration and a refreshed approach to components once the initial integration is complete.</p>
<h2 id="abigthankyou">❤️ A Big Thank You ❤️</h2>
<p>Since <a href="https://github.com/tildeio/glimmer/compare/rip-htmlbars…master">forking HTMLBars</a>, the Glimmer repo has received over 700 commits, not to mention the <a href="https://github.com/emberjs/ember.js/issues?page=1&amp;q=label%3AGlimmer2+is%3Aclosed">integration effort</a> that happened on the Ember side, all of which would not be possible without the help from our community.</p>
<p>Thank you to every one who helped us get here – from the <a href="http://emberjs.com/sponsors/">companies</a> who donated employees' time to the individual contributors who made personal sacrifices to make this happen.</p>
<p>With all of that out of the way – <em>happy alpha testing</em>! 🍾🎊🎉</p>
<hr />
<h2 id="furtherreadingwatching">📚 Further Reading/Watching 📚</h2>
<ul>
<li>🔜 Stay tuned for more <em>Inside Glimmer 2</em> articles from this blog</li>
<li>🚧 <a href="https://github.com/tildeio/glimmer/blob/master/guides/01-introduction.md">Glimmer Architecture Guides</a></li>
<li><a href="https://www.youtube.com/watch?v=OInJBwS8VDQ&amp;list=PL4eq2DPpyBblc8aQAd516-jGMdAhEeUiW&amp;index=1">Opening Keynote</a> from EmberConf 2016</li>
<li><a href="https://www.youtube.com/watch?v=dpx9P1cz37k&amp;list=PL4eq2DPpyBblc8aQAd516-jGMdAhEeUiW&amp;index=23">The Future of Ember Templating</a> from EmberConf 2016</li>
<li><a href="https://www.youtube.com/watch?v=vg5A_UOGShg">Inside Glimmer 2: What Is A Compiler?</a></li>
<li><a href="https://www.youtube.com/watch?v=vL8sCi1Bv6E">Glimmer 2 Deep Dive</a></li>
</ul>
