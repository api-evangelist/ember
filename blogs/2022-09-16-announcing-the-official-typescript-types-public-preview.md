---
title: "Announcing the Official TypeScript Types Public Preview"
url: "https://blog.emberjs.com/announcing-official-typescript-types-public-preview"
date: "Fri, 16 Sep 2022 16:30:00 GMT"
author: ""
feed_url: "https://blog.emberjs.com/rss.xml"
---
<p>As of <code>ember-source@4.8.0-beta.2</code>, Ember is shipping a public preview of our official TypeScript support for the framework itself. This is the next step in implementing <a href="https://rfcs.emberjs.com/id/0724-road-to-typescript/">RFC 0724: Official TypeScript Support</a> and <a href="https://rfcs.emberjs.com/id/0800-ts-adoption-plan/">RFC 0800: TypeScript Adoption Plan</a>. Anyone using TypeScript with Ember 4.8.0 Beta 2 or later can opt into using these preview types by removing the corresponding <code>@types</code> packages and adding the following import in your <code>types/&lt;your app&gt;/index.d.ts</code> file:</p>
<pre><code class="ts language-ts">import 'ember-source/types';
import 'ember-source/types/preview';
</code></pre>
<p>This will set your app up to start using Ember's preview types <em>now</em> and to automatically benefit as we stabilize our types incrementally over the releases ahead. You won't have to do anything except add these once and then upgrade your app on your normal upgrade cadence!</p>

<p>Note that there are some significant changes to these types compared to the types as they exist on DefinitelyTyped today. <strong>All public API remains supported, but in line with RFC 0800, we intentionally provide only minimal support for Ember Classic APIs around class definitions.</strong> Accordingly, you should migrate to native classes <em>before</em> attempting to adopt these types if you have not already done so!</p>
<p>The rest of this post is broken into four sections:</p>
<ul>
<li><a href="#toc_how-the-preview-period-will-work">How the preview period will work</a></li>
<li><a href="#toc_migrating-from-definitelytyped">Migrating from DefinitelyTyped</a></li>
<li><a href="#toc_new-typescript-users">New TypeScript users</a></li>
<li><a href="#toc_whats-next-on-ember’s-road-to-typescript">What's next on Ember’s road to TypeScript?</a></li>
</ul>
<p>If you’re curious about the details of how this approach to publishing TypeScript types for Ember works, check out <a href="https://github.com/emberjs/ember.js/pull/20180">the PR which introduced support</a>!</p>
<h2 id="howthepreviewperiodwillwork">How the preview period will work</h2>
<p>There are two type-only modules you import: <code>'ember-source/types'</code> and <code>'ember-source/types/preview'</code>. These represent the stable and preview types respectively. At the start of the preview period, there is nothing at all in the stable module: <em>all</em> the types are in the preview module.</p>
<p>The key difference between the stable and preview types is: our stable types <em>must</em> be generated from Ember's own TypeScript source code, while the preview types are hand-written type definitions. The hand-written definitions match up closely to the actual code, but small gaps are inevitable. Types published directly from Ember's own source code will not have that problem!</p>
<p>Over the course of the preview period, we will be doing two things:</p>
<ol>
<li><p>We will be fixing bugs in these types as they are identified, and releasing bug fix releases the same way we would for runtime errors. (This will be the new normal for Ember: fixes to types are exactly like fixes to runtime errors, because both are bugs!)</p></li>
<li><p>We will be working on Ember's build infrastructure and the structure of its internals to make it possible to publish types directly from the source, instead of using hand-authored types. These are the types which will be exposed via the <code>import 'ember-source/types';</code> statement.</p></li>
</ol>
<p>Once we are fully cut over to publishing types from Ember's source code, we will declare them "stable" and therefore subject to Ember's normal SemVer policy. For details on how we are handling SemVer for TypeScript, check out <a href="https://rfcs.emberjs.com/id/0800-ts-adoption-plan/#semantic-versioning">the relevant section of RFC 0800</a> and the <a href="https://www.semver-ts.org">Semantic Versioning for TypeScript</a> spec we authored and follow. We’ll also be updating the website with those details in the next few weeks.</p>
<p>We will make a best effort to avoid breaking changes in the types during the preview period, but the transition to the stable types will inevitably involve many bug fixes which may <em>feel</em> like breaking changes!</p>
<p>Also, given that these are <em>preview</em> types, we will continue to maintain the types on DefinitelyTyped until we stabilize these. If you try them out and hit issues you cannot resolve, that’s totally fine! There are two things we think you should do in that case:</p>
<ol>
<li>File an issue on <a href="https://github.com/emberjs/ember.js/issues">the ember.js repo</a> with a report about the issue you had.</li>
<li>Switch back to the <code>@types</code> packages!</li>
</ol>
<p>We will make sure there are no blocking bugs before stabilizing.</p>
<h2 id="migratingfromdefinitelytyped">Migrating from DefinitelyTyped</h2>
<p><em>This section only applies if you are an existing Ember TypeScript user who has been using the <code>@types</code> packages from <a href="https://github.com/DefinitelyTyped/DefinitelyTyped">DefinitelyTyped</a>. If you're trying out TypeScript for the first time now, you can skip it!</em></p>
<p>There are four steps involved in switching from the existing types published on DefinitelyTyped to these preview types.</p>
<ol>
<li><p>Remove the following packages from your <code>package.json</code>:</p>
<ul>
<li><code>@types/ember</code></li>
<li><code>@types/ember__application</code></li>
<li><code>@types/ember__array</code></li>
<li><code>@types/ember__component</code></li>
<li><code>@types/ember__controller</code></li>
<li><code>@types/ember__debug</code></li>
<li><code>@types/ember__destroyable</code></li>
<li><code>@types/ember__engine</code></li>
<li><code>@types/ember__error</code></li>
<li><code>@types/ember__helper</code></li>
<li><code>@types/ember__modifier</code></li>
<li><code>@types/ember__object</code></li>
<li><code>@types/ember__owner</code></li>
<li><code>@types/ember__polyfills</code></li>
<li><code>@types/ember__routing</code></li>
<li><code>@types/ember__runloop</code></li>
<li><code>@types/ember__service</code></li>
<li><code>@types/ember__string</code></li>
<li><code>@types/ember__template</code></li>
<li><code>@types/ember__test</code></li>
<li><code>@types/ember__utils</code></li></ul></li>
<li><p>Install a version of <code>ember-source</code> greater than <code>4.8.0-beta.2</code>. You should pick the latest beta of 4.8 <em>or</em> any stable version starting with 4.8.0 once it's out!</p></li>
<li><p>In the <code>types/&lt;your-app&gt;/index.d.ts</code> file generated for you automatically by <code>ember-cli-typescript</code>, add the new imports as the first items in the file, and remove the array prototype extensions support from the file. With the defaults generated for you, the result would look like this:</p>
<pre><code class="diff language-diff">+import 'ember-source/types';
+import 'ember-source/types/preview';
-import Ember from 'ember';
-
-declare global {
- // Prevents ESLint from "fixing" this via its auto-fix to turn it into a type
- // alias (e.g. after running any Ember CLI generator)
- // eslint-disable-next-line @typescript-eslint/no-empty-interface
- interface Array&lt;T&gt; extends Ember.ArrayPrototypeExtensions&lt;T&gt; {}
- // interface Function extends Ember.FunctionPrototypeExtensions {}
-}

export {};
</code></pre></li>
<li><p>Account for the differences between the preview types and the definitions on DefinitelyTyped. These differences all fall into one of these broad categories:</p>
<ul>
<li>Fixes to problems in the existing definitions.</li>
<li>Removal of our (poor!) support for Ember Classic class features in favor of native classes.</li>
<li>Changes to type registry handling</li>
<li>Removal of legacy (private) routing APIs</li></ul></li>
</ol>
<h3 id="fixestoproblemsintheexistingdefinitions">Fixes to problems in the existing definitions</h3>
<p>For the preview types, we started by copying over the community-maintained type definitions from DefinitelyTyped. We then updated them to use more robust type testing tools that DefinitelyTyped allows, which exposed a bunch of bugs to fix. We also did a basic comparison of the types we are publishing with the corresponding types in Ember's own code, which has been written in TypeScript for years and got a huge improvement from <a href="https://github.com/wagenet">@wagenet</a> earlier this year.</p>
<p>As a result, you may find some differences when you switch over. In every case, these represent <em>bug fixes</em>, but we recognize they may involve some work!</p>
<h4 id="introducingaresolvertype">Introducing a <code>Resolver</code> type</h4>
<p>The types on DefinitelyTyped supply a definition of <code>Resolver</code> from <code>ember-resolver</code>, which is where most Ember users get their resolver. However, <code>ember-resolver</code> and other resolvers work because they implement <em>Ember’s</em> contract for what a resolver is. A future RFC will introduce a public type import for this. (It was missed during the work on <a href="https://rfcs.emberjs.com/id/0821-public-types/">RFC 0821</a> because the type presently does <em>not</em> come from Ember!)</p>
<p>For now, the type exists at <code>@ember/-internals/resolver</code>, and is introduced to be type-compatible with the type for <code>ember-resolver</code> on DefinitelyTyped. (See <a href="https://github.com/ember-cli/ember-resolver/issues/795">this issue</a> for an issue tracking publishing types from <code>ember-resolver</code>, which is likely gated on a public type import from Ember, but until we ship stable types, can be managed via careful types work on DefinitelyTyped.)</p>
<h4 id="removingsupportforarrayprototypeextensions">Removing support for <code>Array</code> prototype extensions</h4>
<p>This work also exposed a number of errors in the existing types, especially around <code>Array</code> prototype extensions. As a result, these types <em>do not support</em> <code>Array</code> prototype extensions, and it is unlikely that future work will be able to add that support. (The support provided via the types on DefinitelyTyped only worked because the types were defined incorrectly, resulting in a variety of kinds of unsafety.)</p>
<p>Notably, Array prototype extensions are <a href="https://github.com/emberjs/rfcs/pull/848">being deprecated</a>, so moving off of them is work you will need to do <em>anyway</em>.</p>
<h3 id="emberclassicsupport">Ember Classic support</h3>
<p>As specified in <a href="https://rfcs.emberjs.com/id/0800-ts-adoption-plan/">RFC 0800</a>, there are also a number of breaking changes from the types in DefinitelyTyped regarding support for Ember Classic features:</p>
<blockquote>
  <p>Per the edition support policy, we will provide minimal support for Ember Classic features:</p>
  <ul>
  <li><p><strong>Ember's classic class system</strong>: we will provide minimal definitions for the <code>.create()</code>, <code>.extend()</code>, <code>.reopen()</code>, <code>.reopenClass()</code>, methods, which make no attempt to use them to actually update the types of the items they modify.…</p></li>
  <li><p><strong>Ember’s <code>get</code> and <code>set</code> helpers:</strong> we will not provide types to make <code>get</code> and <code>set</code> type-safe beyond property lookups on objects—i.e. no support for nested path lookups.…</p></li>
  <li><p><strong>Classic computed property handling:</strong> we will not provide “safe” types for the classic form of computed properties.</p></li>
  </ul>
</blockquote>
<h4 id="embersclassicclasssystem">Ember's classic class system</h4>
<p>The definitions on DefinitelyTyped attempted to make <code>.create()</code> and <code>.extend()</code> actually create updated types, and tried to make <code>.create()</code>, <code>.extend()</code>, <code>.reopen()</code>, and <code>.reopenClass()</code> have the correct type for <code>this</code> within their bodies. These were always extremely fragile and mostly did not work. Since Ember 3.6, Ember users have been able to use native classes instead of Ember’s classic class system, and this has been the recommended way of writing Ember code since the release of the Octane edition in Ember 3.15.</p>
<p>In the preview types, these methods are present and are safe to use since they are still part of Ember’s public API. However, <code>.create()</code> and <code>.extend()</code> do not create new types. The <code>.create()</code> method <em>does</em> still check that the values you pass match those defined on the class body, but the types do not attempt to make <code>this</code> have the right type within the bodies of <code>.create()</code>, <code>.extend()</code>, <code>.reopen()</code>, or <code>.reopenClass()</code>.</p>
<p>To migrate, you should:</p>
<ul>
<li>Convert all your own classic classes to native classes.</li>
<li>Eliminate your use of mixins.</li>
</ul>
<p>(Most Ember TypeScript users have already done this, because these worked so poorly with TypeScript.)</p>
<p>The <code>.create()</code> call can always be replaced with a normal <code>class</code> definition in JavaScript. For each of the others, you can also use <a href="http://www.typescriptlang.org/docs/handbook/declaration-merging.html">declaration merging</a> to represent the <em>behavior</em> of the method in question.</p>
<h5 id="extend"><code>.extend()</code></h5>
<p>For the case where you are only defining a new class, convert to a native class instead. However, if you have code which still relies on mixins like <code>Evented</code>, you can represent it using interface merging like this:</p>
<pre><code class="ts language-ts">import EmberObject from '@ember/object';
import Evented from '@ember/object/evented';
import type Owner from '@ember/owner';

// A native class which still applies the Evented mixin
class ExtendsDemo extends EmberObject.extend(Evented) {
  moreStuff = true;

  constructor(owner: Owner) {
    super(owner);
    this.on('custom', this, 'boundMethod');
  }

  willDestroy(): void {
    this.off('custom', this, 'boundMethod');
  }

  boundMethod = () =&gt; {
    alert('do something');
  };
}

// Make that work for the *type* by merging the type of the class
// (`interface ExtendsDemo`) with the type of the mixin (`Evented`)
interface ExtendsDemo extends Evented {}

const instance = ExtendsDemo.create({
  moreStuff: false,
});

instance.trigger('custom');
</code></pre>
<p>Note: you will have to disable the <code>@typescript-eslint/no-empty-interface</code> ESLint rule for this.</p>
<p>You can do the same for your own mixins while transitioning by defining an interface which represents the type of the mixin:</p>
<pre><code class="ts language-ts">import Mixin from '@ember/object/mixin';

// Creates the runtime mixin code
const Alertable = Mixin.create({
  alert(value: string) {
    alert(`The value is ${value}`);
  }
})

// Creates the type for TypeScript to see.
interface Alertable extends Mixin {
  alert(value: string): void;
}

// Exports them as a single name in both value and type space.
export default Alertable;
</code></pre>
<h5 id="reopen"><code>.reopen()</code></h5>
<p>In general, <code>.reopen()</code> is an antipattern, because it makes it very hard to understand where a given part of a class’ state or behavior lives, and you should move away from it! You should prefer to <em>delegate</em> to a class instead of dynamically adding behavior to it, both for maintainability and for performance. However, for the transition, you can represent it using interface merging.</p>
<pre><code class="ts language-ts">import EmberObject from '@ember/object';

class Foo extends EmberObject {
  someProp = 123;
}

// This is what makes the change work at runtime...
Foo.reopen({
  extra: 'hello',
});

// ...while this is what makes it visible to the type system.
interface Foo {
  extra: string;
}

// Now when calling `Foo.create`, or when working with an instance of the
// class, both `someProp` and `extra` will be checked.
const instance = Foo.create({
  someProp: 456,
  extra: 'goodbye',
});
</code></pre>
<h5 id="reopenclass"><code>.reopenClass()</code></h5>
<p>As with <code>.reopen()</code>, the use of <code>.reopenClass()</code> is an antipattern you should move away from over time, preferring to use regular functions in module scope or normal static methods on native classes. In the meantime, you can use <em>namespace merging</em> to represent how it works:</p>
<pre><code class="ts language-ts">import EmberObject from '@ember/object';

class Foo extends EmberObject {
  static someStatic = true;
}

// This adds the method to the Foo class at runtime...
Foo.reopenClass({
  anotherStatic(): string {
    return 'hello';
  },
});

// ...and this makes it visible to TypeScript as a static method.
declare namespace Foo {
  export function anotherStatic(): string;
}

if (Foo.someStatic) {
  Foo.anotherStatic().length;
}
</code></pre>
<p>Note: you will have to disable the <code>@typescript-eslint/no-namespace</code> ESLint rule for this.</p>
<h3 id="typeregistries">Type registries</h3>
<p>These types, as a fairly direct extraction from DefinitelyTyped, currently maintain the service and controller type registries. Given the lack of support for classic computed properties, which are the main way to take advantage of those at present, <strong>it is fairly likely some or all of these will be removed before stabilizing the types.</strong> The major remaining use case is type-safe lookup using the <code>Owner.lookup</code> APIs, so if you have thoughts on that, please reach out in <a href="https://discord.com/channels/480462759797063690/786312479620726804"><code>#dev-typescript</code></a>.</p>
<h3 id="legacyroutingtypelocations">Legacy routing type locations</h3>
<p>In line with <a href="https://rfcs.emberjs.com/id/0821-public-types/">RFC 0821: Public API for Type-Only Imports</a>, this PR also removes support for importing the types for <code>Transition</code>, <code>RouteInfo</code>, and <code>RouteInfoWithMetadata</code> from the private locations that DefinitelyTyped presently supports for backwards compatibility. Users will need to migrate to using the correct import paths when switching to use these imports.</p>
<ul>
<li><code>import Transition from '@ember/routing/-private/transition'</code> → <code>import Transition from '@ember/routing/transition'</code></li>
<li><code>import RouteInfo from '@ember/routing/-private/route-info'</code> → <code>import RouteInfo from '@ember/routing/route-info'</code></li>
<li><code>import { RouteInfoWithMetadata } from '@ember/routing/-private/route-info-with-metadata'</code> → <code>import { RouteInfoWithMetadata } from '@ember/routing/route-info'</code></li>
</ul>
<h2 id="newtypescriptusers">New TypeScript users</h2>
<p><em>This section only applies if you are trying out the types for the first time!</em></p>
<p>For the moment, the best way to get started with these types is to install <code>ember-cli-typescript</code> and use its generators, then <em>remove</em> a lot of what it does. We will be fixing this in the weeks ahead!</p>
<p>Here’s the process as of today:</p>
<ol>
<li><p>Set up <code>ember-cli-typescript</code> by running <code>ember install ember-cli-typescript</code>.</p></li>
<li><p>Remove the following newly-added packages from your <code>package.json</code>:</p>
<ul>
<li><code>@types/ember</code></li>
<li><code>@types/ember__application</code></li>
<li><code>@types/ember__array</code></li>
<li><code>@types/ember__component</code></li>
<li><code>@types/ember__controller</code></li>
<li><code>@types/ember__debug</code></li>
<li><code>@types/ember__destroyable</code></li>
<li><code>@types/ember__engine</code></li>
<li><code>@types/ember__error</code></li>
<li><code>@types/ember__helper</code></li>
<li><code>@types/ember__modifier</code></li>
<li><code>@types/ember__object</code></li>
<li><code>@types/ember__owner</code></li>
<li><code>@types/ember__polyfills</code></li>
<li><code>@types/ember__routing</code></li>
<li><code>@types/ember__runloop</code></li>
<li><code>@types/ember__service</code></li>
<li><code>@types/ember__string</code></li>
<li><code>@types/ember__template</code></li>
<li><code>@types/ember__test</code></li>
<li><code>@types/ember__utils</code></li></ul></li>
<li><p>Install a version of <code>ember-source</code> greater than <code>4.8.0-beta.2</code>. You should pick the latest beta of 4.8 <em>or</em> any stable version starting with 4.8.0 once it's out!</p></li>
<li><p>In the <code>types/&lt;your-app&gt;/index.d.ts</code> file generated for you automatically by <code>ember-cli-typescript</code>, add the new imports as the first items in the file, and remove the array prototype extensions support from the file. With the defaults generated for you, the result would look like this:</p>
<pre><code class="diff language-diff">+import 'ember-source/types';
+import 'ember-source/types/preview';
-import Ember from 'ember';
-
-declare global {
- // Prevents ESLint from "fixing" this via its auto-fix to turn it into a type
- // alias (e.g. after running any Ember CLI generator)
- // eslint-disable-next-line @typescript-eslint/no-empty-interface
- interface Array&lt;T&gt; extends Ember.ArrayPrototypeExtensions&lt;T&gt; {}
- // interface Function extends Ember.FunctionPrototypeExtensions {}
-}

export {};
</code></pre></li>
</ol>
<h2 id="knownissues">Known issues</h2>
<p>The first beta release has the following known issues (which we will fix during the beta period):</p>
<ul>
<li>The <code>@types/ember-data</code> packages are not compatible with these types, because they assume the presence of many of the Ember Classic types we removed in this migration. If you are using Ember Data with TypeScript, you will need to wait for a future update.</li>
<li>The import file for stable types does not exist yet, so TypeScript will warn you that there is no type for the module. We expect to fix this before releasing <code>4.8.0-beta.3</code>!</li>
</ul>
<h2 id="whatsnextonembersroadtotypescript">What's next on Ember’s road to TypeScript?</h2>
<p>Now that we have these preview types in place, we can begin publishing types in a stable way as soon as our build tooling for Ember itself supports it. As we do so, more and more the types will be provided by the <code>import 'ember-source/types';</code> import, and fewer from the <code>import 'ember-source/types/preview';</code> import. That will largely be transparent to you as an end user. Where there are be small differences, we will note them as it happens!</p>
<p>We <em>hope</em> to progressively switch over from these preview types to the stable types in the 4.9–4.11 time frame—that is, before the 4.12 LTS candidate release comes out. As always with software, and especially open source software, there are no guarantees, though!</p>
<p>We are also working on a “quest” issue for getting the rest of <a href="https://rfcs.emberjs.com/id/0800-ts-adoption-plan/">RFC 0800</a> implemented. There are a <em>lot</em> of other core packages which need to publish types for us to get all the way to our goal of having first-class TypeScript support for the ecosystem. We could use your help! If you’d like to pitch in, check out <a href="https://github.com/emberjs/ember.js/issues/20162">the tracking issue</a> and reach out <a href="https://discord.com/channels/480462759797063690/786312479620726804">in <code>#dev-typescript</code> on Discord</a>!</p>
<p>In parallel, there are two other big efforts in flight:</p>
<ol>
<li><p>The Ember TypeScript team is making steady progress on getting <a href="https://typed-ember.gitbook.io/glint">Glint</a> to its 1.0 release.</p>
<ul>
<li><p>We recently shipped basic support for TypeScript <a href="https://www.typescriptlang.org/docs/handbook/project-references.html">project references</a>, i.e. the <code>--build</code> command, and expect to finish that up by supporting <code>--build --watch</code> mode in the next month or two.</p></li>
<li><p>We supported Framework Core team member emeritus <a href="https://github.com/chadhietala">@chadhietala</a> in landing full support for <a href="https://github.com/glimmerjs/glimmer-experimental">GlimmerX</a> in Glint.</p></li>
<li><p>We identified a significant refactor we can make which will let us give <em>much</em> better type errors and eliminate a number of tricky edge cases. (If you’ve hit the “Expected 3 arguments but got 2” error for an item which only <em>has</em> two arguments, this will fix that and a bunch of others as well!)</p></li></ul></li>
<li><p>The Ember Learning team is working closely with the Ember TypeScript team and to build out support for TypeScript in our API docs and the Guides. The effort is being led by a community member, <a href="https://github.com/ttbach">@ttbach</a>—and she could also use your help, too! Most of the work here does <em>not</em> require TypeScript expertise, only the ability to work on Node tools, so it’s another great spot to jump in. Reach out to <code>@thaobach</code> in <a href="https://discord.com/channels/480462759797063690/480777444203429888"><code>#dev-ember-learning</code></a> if you would like to contribute!</p></li>
</ol>
<p>That’s it for now, but keep your eyes open for further blog posts about the TypeScript effort and other parts of Polaris!</p>
