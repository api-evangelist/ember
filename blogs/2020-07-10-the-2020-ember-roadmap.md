---
title: "The 2020 Ember Roadmap"
url: "https://blog.emberjs.com/2020-ember-roadmap"
date: "Fri, 10 Jul 2020 00:00:00 GMT"
author: ""
feed_url: "https://blog.emberjs.com/rss.xml"
---
<p>The purpose of the Ember Roadmap process is to rally the community around a number of shared goals. This post documents those goals for 2020.</p>
<p>Since the Ember community cannot predict the future, we cannot be sure that we will achieve all of the individual items enumerated here. Instead, the purpose of this document is to give the community a common purpose to aspire towards.</p>
<p>This year our two headline priorities are:</p>
<ul>
<li>Polish the practical and conceptual details of Octane (tracked properties, Glimmer components, related tooling, accessibility, performance and payload improvements).</li>
<li>Make Ember easier to try and adopt, but also lower barriers for Ember developers when collaborating with the greater JavaScript project. We will do this through improvements and simplifications to the framework, and through focused communication with the greater JavaScript community.</li>
</ul>
<!-- READMORE -->
<hr />
<p>This document was started in fall 2019. It is a distillation of multiple sources:</p>
<ol>
<li>The <a href="https://emberjs.com/ember-community-survey-2019/">2019 Community Survey</a>.</li>
<li>Community <a href="https://twitter.com/hashtag/EmberJS2019?f=live">#EmberJS2019</a> blog posts authored in response to our call for posts.</li>
<li>Discussion on <a href="https://discuss.emberjs.com/">https://discuss.emberjs.com</a>, Discord, Twitter, and other public venues (see the <a href="https://emberjs.com/community/">community page</a> for how to access these communnities).</li>
<li>Deliberations among the Ember core teams.</li>
<li>Your comments and feedback on this document via <a href="https://github.com/emberjs/rfcs/pull/519">the RFC process</a>.</li>
</ol>
<p>The goal of the roadmap is to align the Ember community around a set of shared, achievable goals that balance the needs of existing users with the need to grow and support new users.</p>
<h2 id="ourroadmap">Our Roadmap</h2>
<p>Now that Ember Octane has shipped, it’s time to turn our attention to new efforts in 2020. Our goal is to build on Octane's release and capitalize on that cutting-edge foundation.</p>
<ul>
<li><strong>Invest in Octane.</strong> Octane's mental model and basic components are complete, but a number of practical and conceptual gaps remain. We will close these gaps with work on tooling, by deprecating classic APIs to simplify Ember for new users, and by introducing additional functionality where appropriate.</li>
<li><strong>Modernize our build system.</strong> This year we will prioritize improvements to the Ember application build pipeline, and to Ember itself, which will bring modern optimizations like tree shaking and code splitting to both new applications <em>and</em> existing codebases.</li>
<li><strong>Better a11y by default</strong>. We will better support assistive technologies via updates to the router. Additionally we will provide developers more tools for understanding and improving the accessibility of their Ember applications. Our goal is a great "out of the box" experience with Ember and assistive technologies.</li>
<li><strong>Share Octane outside our community.</strong> Octane's release put Ember in front of a lot of new eyes. We will continue that trend through 2020 by talking about the latest edition of Ember in front of new audiences.</li>
</ul>
<h3 id="investinoctane">Invest in Octane</h3>
<p>Ember Octane put the framework on a strong footing by modernizing its most foundational APIs. Teams are already productive using Octane, and from their experience have provided a torrent of real-world feedback. We will continue improving the developer experience (DX) of Octane throughout 2020.</p>
<p>Many of the rough edges in Octane aren't on the features themselves, but in the supporting tooling. The usefulness of stack traces from Glimmer, the ability to use TypeScript with Ember templates, how tracked properties and Glimmer components are reflected in the Ember Inspector, and the build speed of our application pipelines are all important parts of Octane's DX. We will invest in these areas of work.</p>
<p>For developers who are new to Ember, the presence of classic non-Octane APIs can be disorienting. We will look for creative solutions that make those features trivial for existing apps to continue using while also making them less expensive (in payload, performance, and mental model) for new adopters.</p>
<p>Finally there are some areas of Octane features which can still benefit from new feature work:</p>
<ul>
<li>The <code>@tracked</code> system, for example, limits the expression of state in an application to defined properties on an object. Real-world codebases often want to maintain state as a list or a map, and we can extend on the well-designed internals of Ember's reactivity model to support these cases.</li>
<li>Modifiers provide a hook into the DOM rendering lifecycle, but Octane has no APIs for hooking into other lifecycles in the rendering and object system. We will create these APIs.</li>
<li>We will continue a push to make Ember templates better analyzable at build time by introducing a strict-mode template and static imports.</li>
<li>We will make it easier to build ergonomic, reusable components by shipping named blocks.</li>
</ul>
<p>We will introduce new features in Ember which improve Octane in these and other areas.</p>
<h3 id="modernizeourbuildsystem">Modernize our build system</h3>
<p>Last year, we started work on Embroider, an overhaul of the Ember CLI compilation pipeline. This year, we will put the finishing touches on Embroider and start migrating the Ember ecosystem to this modernized build.</p>
<p>Embroider integrates Ember CLI with popular packagers like <a href="https://webpack.js.org/">webpack</a> and <a href="https://rollupjs.org/guide/en/">rollup</a>. It allows Ember apps to trivially import from any dependency published as standard JavaScript modules, and will unblock shipping Ember itself as npm packages in the <code>@ember</code> namespace.</p>
<p>This new approach, through its foundation on common packaging libraries, will also unlock new build time optimizations. These optimizations, like tree-shaking and route-based code-splitting, will allow Embroider to produce smaller asset payloads.</p>
<p>Additionally, we will introduce a system into Ember which allows apps to drop framework code supporting deprecated features unused by an app. This will result in smaller vendor assets for applications which don't rely on deprecated features. For example, a modern Octane application may not require <code>Ember.Component</code>, and can benefit from having the code supporting that API being dropped at build time.</p>
<p>Finally, we will make sure this modernization effort provides benefits to existing applications. If a team has been steadily upgrading their app for years now, they won't need to rewrite it to get the benefits of a modern build packager.</p>
<h3 id="bettera11ybydefault">Better a11y by default</h3>
<p>Ember applications should be accessible to everyone. Unfortunately, even seemingly small mistakes can make your app difficult or impossible to use with assistive technology like screen readers. We will do more to improve the out-of-the-box accessibility of Ember applications, and provide tools to help applications stay accessible as they grow.</p>
<ul>
<li><strong>Fix router accessibility</strong> so that page navigation is correctly announced by screen readers, without needing a third-party addon.</li>
<li>Incorporate <strong>accessibility checks</strong> into the built-in test helpers.</li>
<li><strong>Engage with standards bodies</strong> to help fill the gaps in existing web accessibility APIs.</li>
</ul>
<p>To contribute to this effort see <a href="https://github.com/emberjs/rfcs/issues/595">RFC Issue 595</a> which coordinates the Ember A11y Strike Team.</p>
<h3 id="sharingoctaneoutsideourcommunity">Sharing Octane outside our community</h3>
<p>There are more people building web applications than ever, and Ember must adapt to their changing needs and expectations in order to stay relevant. Octane better aligns Ember's API with what new users expect from a modern framework. We need to take advantage of that change.</p>
<p>This year, we’ll share with the world how Ember Octane is modern, productive, and <em>fun</em>. Through blog posts, videos, social media, meetups, and conferences, we will share our knowledge and experiences with the wider JavaScript community and encourage them to give Octane a try.</p>
<p>We will continue to make Octane more attractive to new users with a new documentation approach, more effective website, and with clearer communication about the Glimmer.js project.</p>
<hr />
<h2 id="loweringbarrierstoadoptionandcollaboration">Lowering barriers to adoption, and collaboration</h2>
<p>Making Ember more attractive to new users doesn't mean compromising on what has made the framework so very successful for existing codebases and teams.</p>
<p>The most basic value of the Ember project is that we solve problems together. While we intend to grow the number of framework users and modernize the framework in many ways, we won't optimize for growth at the expense of our existing community. Instead, we will collaborate on solutions that come with a curated adoption story.</p>
<p>Because we understand and value the power of collaboration, we know we must lower barriers, technical and non-technical, which not only make new users hesitate to adopt Ember but also discourage Ember developers from participating the greater JavaScript community.</p>
<p>A great example of our progress in this is Octane's embrace of native JavaScript classes: A JavaScript developer starting out with Ember today isn't immediately forced to learn a new, Ember-specific class API before they can get to writing code. On the other hand, a developer who starts off with Ember can also contribute to most OSS JavaScript projects without needing to first un-learn the Ember class system.</p>
<p>By sharing common solutions to common problems with other communities we not only make Ember more approachable, we also benefit from the opportunity to exchange more ideas. Everyone wins.</p>
<p>With our efforts to flesh out Octane, improve the build system and align it with the rest of the JavaScript community, raise the baseline support for accessible applications, and to better communicate in 2020 we will lower barriers to adoption of Ember, but also to our own collaboration with the greater JavaScript project.</p>
<p>Want to get involved? Visit our <a href="https://emberjs.com/community/">community page</a>
and feel free to join us on Discord (chat) or Discourse (forum discussion).</p>
