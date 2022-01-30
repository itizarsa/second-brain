# The Third Age of JavaScript

Source: Article
Status: Unprocessed
URL: https://www.swyx.io/js-third-age/

[https://res.cloudinary.com/practicaldev/image/fetch/s--8Hk5vH1Y--/c_imagga_scale,f_auto,fl_progressive,h_420,q_auto,w_1000/https://pbs.twimg.com/media/EYe3aBjXkAUrRzD%3Fformat%3Dpng%26name%3Dsmall](https://res.cloudinary.com/practicaldev/image/fetch/s--8Hk5vH1Y--/c_imagga_scale,f_auto,fl_progressive,h_420,q_auto,w_1000/https://pbs.twimg.com/media/EYe3aBjXkAUrRzD%3Fformat%3Dpng%26name%3Dsmall)

---

A bunch of things are moving in JavaScript - it is quite feasible that the JS of 10 years from now will look totally unrecognizable #reflections #javascript

Every 10 years there is a changing of the guard in JavaScript. I think we have just started a period of accelerated change that could in future be regarded as the **Third Age of JavaScript**.

![The%20Third%20Age%20of%20JavaScript%20e6f08a8a4ff14dedadbc11a95065d346/rlixanixq8pyrpg9ivrv.png](The%20Third%20Age%20of%20JavaScript%20e6f08a8a4ff14dedadbc11a95065d346/rlixanixq8pyrpg9ivrv.png)

**The first age of JS, from 1997-2007**, started with a bang and ended with a whimper. You all know Brendan Eich's story, and perhaps it is less known how the ES4 effort faltered amidst strong competition from closed ecosystems like Flash/Actionscript. The full origin story of JS is better told by its principal authors, Brendan Eich and Allen Wirfs-Brock, in [JavaScript: The First 20 Years](https://www.swyx.io/writing/js-20-years/).

![The%20Third%20Age%20of%20JavaScript%20e6f08a8a4ff14dedadbc11a95065d346/ecmascript-history.png](The%20Third%20Age%20of%20JavaScript%20e6f08a8a4ff14dedadbc11a95065d346/ecmascript-history.png)

**The second age of JS, from 2009-2019**, started with the *annus mirabilis* of 2009, where npm, Node.js, and ES5 were born. With Doug Crockford showing us [its good parts](http://shop.oreilly.com/product/9780596517748.do), users built a whole host of [JS Build Tools](https://www.swyx.io/writing/jobs-of-js-build-tools/) and libraries, and extended JS' reach to both desktop and new fangled smart phones. Towards 2019 we even saw the emergence of specialized runtimes for JS on phones like [Facebook's Hermes](https://github.com/facebook/hermes) as well as compiler first frontend frameworks like [Svelte 3](https://svelte.dev/blog/svelte-3-rethinking-reactivity).

2020 feels like the start of a new Age. If the First Age was about building out a language, and the Second Age was about users exploring and expanding the language, the Third Age is about clearing away legacy assumptions and collapsing layers of tooling.

> Note: I have pitched the Collapsing Layers thesis before!
> 

The main legacy assumption being cleared away is the JS ecosystem's reliance on CommonJS, which evolved as a series of compromises. Its replacement, ES Modules, has been waiting in the wings for a while, but lacked the momentum to truly take a leap because existing tooling was slow but "good enough". On the frontend, modern browsers are equipped to handle these in small amounts too, but [important details haven't yet been resolved](https://v8.dev/features/modules#bundle). The [Pika/Snowpack](https://www.snowpack.dev/) project is positioned to accelerate this future by providing a facade that can disappear as ES Modules get worked out. As a final bonus, IE11 will begin its slow march to [end of life starting this year and ending in 2029](https://www.swyx.io/writing/ie11-eol/).

The other assumption going away is that JavaScript tools must be built in JavaScript. The potential for type safety and [10x-100x performance speedup](https://github.com/evanw/esbuild) in hot paths is too great to ignore. The "for JS in JS" ideal was chipped away with the [near complete takeover of JavaScript by TypeScript](https://twitter.com/swyx/status/1260888049958838272?s=20) and now Deno, Relay, [Parcel](https://v2.parceljs.org/blog/beta3/) and [Volta](https://volta.sh/) are proving that people will learn Rust to contribute to core JS tools. [Brandon Dail predicts](https://twitter.com/aweary/status/1001874375472168960?s=20) this conversion will be done by 2023. We will continue to write JavaScript and TypeScript for the majority of surrounding tooling where approachability outweighs performance. Where we used to think about "[Functional Core, Imperative Shell](https://www.destroyallsoftware.com/screencasts/catalog/functional-core-imperative-shell)", we are now moving to "**Systems Core, Scripting Shell**".

> Note - this is contested, and Python's PyPy indicates this isn't a foregone conclusion.
> 

**Layers are also collapsing in interesting ways**. Deno ([now a startup](https://deno.com/blog/the-deno-company)) takes a radical approach of writing a whole new runtime, collapsing a bunch of common tools doing tasks like testing, formatting, linting and bundling into one binary, speaking TypeScript, and even including a [standard lib](https://deno.land/manual/standard_library). Rome ([now a startup](https://rome.tools/blog/announcing-rome-tools-inc/), [pitch deck here](https://drive.google.com/file/d/1gOUJshwbJpxmrqLjOmrpTCKjBWT6dp7Y/view)) takes a different tack, collapsing all those layers atop of Node.js (as far as I know, I'm not too close to it).

Something that didn't exist 10 years ago and now is a fact of life is public clouds (AWS, Azure, GCP, et al). JavaScript has an interesting relationship with the cloud that I cannot quite articulate - Cloud platform devs wouldn't touch JS with a 10 foot pole, but yet JS is their biggest consumer. AWS Lambda launched with JS first. There's also a clear move to collapse layers between your IDE and your cloud and remove the pesky laptop in between. Glitch, Repl.it, Codesandbox, [GitHub Codespaces](https://twitter.com/github/status/1258068851809497089), Stackblitz and more are all [Cloud Distros](https://www.swyx.io/writing/cloud-distros/) leveraging JS to explore this space. Meanwhile, [JAMstack](http://jamstack.org/) providers like Netlify and Vercel tackle it from the PoV of collapsing layers between your CI/CD and your CDN, and removing the pesky running server in between.

Even in frontend frameworks, the activity going on is fascinating. Svelte [collapsed everything from animations to state management into a compiler](https://www.swyx.io/speaking/svelte-space-elevator/). React is exploring [metaframeworks](https://www.swyx.io/writing/react-distros/) and [client-server integration](https://twitter.com/dan_abramov/status/1259614150386425858). And Vue is [working on an "unbundler" dev server project named Vite](https://github.com/vuejs/vite).

In summary: Third Age JS tools will be

- Faster
- ESM first
- Collapsed Layers (One thing doing many things well instead of many things doing one thing well)
- Typesafe-er (built with a strongly typed language at core, and supporting TS in user code with zero config)
- Secure-er (from dependency attacks, or lax permissions)
- Polyglot
- Neo-Isomorphic (recognizing that much, if not most, JS should run first at buildtime or on server-side before ever reaching the client)

The result of all of this work is **both a better developer experience** (faster builds, industry standard tooling) and **user experience** (smaller bundles, faster feature delivery). It is the final metamorphosis of JavaScript from site scripting toy language to full application platform.

If [Gary Bernhardt's predictions hold true](https://www.destroyallsoftware.com/talks/the-birth-and-death-of-javascript), the Third Age may be JavaScript's last (his timeline gives JS until 2035). There is always the looming specter of Web Assembly - even Brendan Eich has pivoted his famous saying to "Always Bet on JS - and WASM". He originally thought JS could be "the universal virtual machine", but [told me once that](https://twitter.com/BrendanEich/status/1001307081725562882?s=20) WASM now is the ultimate fulfillment of that idea.

If so - **we're in the Endgame now**.

**What will the end of JavaScript's Third Age around ~2030 look like?** Let me know your guess 👇

[The%20Third%20Age%20of%20JavaScript%20e6f08a8a4ff14dedadbc11a95065d346/EYe3aBjXkAUrRzD](The%20Third%20Age%20of%20JavaScript%20e6f08a8a4ff14dedadbc11a95065d346/EYe3aBjXkAUrRzD)

Notable Takes: Chris Coyier on JavaScript in 2021 [Tweet thread](https://twitter.com/chriscoyier/status/1362542264749346816?s=20) and [podcast discussion](https://shoptalkshow.com/452/)

[https://www.javascriptjanuary.com/blog/the-last-and-next-decade-of-javascript-and-other-web-technologies](https://www.javascriptjanuary.com/blog/the-last-and-next-decade-of-javascript-and-other-web-technologies)

interesting projects to track (Robin Cussol maintains a repo here for [JS tools not in JS](https://github.com/RobinCsl/awesome-js-tooling-not-in-js))