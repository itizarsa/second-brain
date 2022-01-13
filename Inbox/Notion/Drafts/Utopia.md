# Utopia

Source: Website
Status: Unprocessed
URL: https://utopia.app/

![https://utopia.app/og-card.png](https://utopia.app/og-card.png)

---

![og-card.png](Utopia%203575ba40fafa40629c9761ed656661bc/og-card.png)

Today we’re announcing the alpha version of Utopia, a design and coding environment for React projects and components that runs in the browser. It combines VSCode with a design and preview tool, and full two-way synchronisation: **design and code update each other, in real time**. And unlike any design tool out there, it uses React code as the source of truth.

We built Utopia to combine the speed of design tools with the power of code. And we wanted to do this so that it works with real code, in real projects. Recent years have seen an explosion in better collaboration tooling, handover tooling, code export, prototyping plugins. But all too often they also add complexity, increase brittleness, and introduce more failure points.

Utopia is different. Ultimately, designs are only as good as what was actually shipped! So we asked ourselves the question: if that’s the goal, why not start there? The result is a product that reads, runs, understands, and manipulates production-level React code. No “code export” that doesn’t follow your conventions, no bulk rewrites, and no diffs. And most importantly, we made it safe: whatever Utopia doesn’t (yet) understand, it leaves as-is.

We wanted Utopia to be incredibly fast and easy to pick up. Part of this is making it feel natural - bringing behaviours, features, and keyboard shortcuts you already have muscle memory for. And since Utopia is an editor - not a library, not a framework - you can use (and learn!) vanilla Javascript and React. If you have a preferred way of styling your components, managing state, or splitting your code across files, it’ll work.

In its simplest form, you can use it as an online coding playground for React projects, and include custom assets, and external packages and component libraries via node. To edit the code, we included VSCode, Microsoft’s open source code editor - complete with ESLint, Prettier, theme support. There’s a console for debugging, an external preview for sharing your creations with the world, and runtime error messages. And there’s a canvas that lets you render one or many components, and that updates as-you-type.

Utopia’s superpowers really come to the fore once you switch the canvas into edit mode. Every element and component on the canvas becomes selectable, configurable, and editable. We had ambitious objectives here, and in particular wanted to create a tool that was familiar, powerful, and also adapted to the unique challenge of editing real, production-grade code. Here are some of the ways in which this works:

**Follow me lets you stay in sync:** Utopia defaults to a “follow me” mode, where clicking on an element in the design automatically opens up the file, scrolls to the right place, and places the cursor. And this works the other way around as well!

**Components are first class concepts.** Utopia was built from the ground up to work with nested components that can be configured via props. For instance, you can quickly switch between seeing the instance of one to editing the component itself, in place, without context switching.

**Working with generated and conditional content:** Real UIs aren’t just “powered by data”, but frequently generated from them. And they contain a lot of conditionally rendered content. Utopia handles generated and conditional content with relative ease, and understands what “source” they refer back to. For conditions, you can see where they apply, toggle them manually, and make the changes you want.

**Layouts with real CSS:** We built Utopia to deal with real layouts. This includes not only layout systems like Flexbox / Autolayout, but also content-driven sizing, and cascades of nested block-level elements you find in many components.

**Code-aware design:** Frequently, parts of your UI are populated by variables and function calls. That’s passed-in style props, colours and backgrounds picked from a theme, or conditionally applied text colours. For some of these, we already have tools built in to edit them. And for all of them, our editor understands they’re there, clearly calls them out to you, and even lets you quickly override them. Or jump directly to the code.

**Designing with real css:** CSS-based layouts are a far cry from absolutely positioned boxes in a global layout system you find in most design tools. Elements size themselves based on their content, content may overflow or get cut off, and layout systems like Flexbox or Grid are everywhere. While these ways of dealing with layouts are more scalable and adaptable, they also make for a pretty slow and unintuitive design experience. To get around this, we built new tools that take the spirit of “just grab the box and drag it” but made it fit for real-life layout systems. And we added dozens of little conveniences to make working with multi-level nested layouts more intuitive.

How ready is Utopia? The coding playground side of Utopia works well, and we’ve been using it internally to prototype and experiment with parts of the editor itself! The design tool is still quite early, but we’d love to see what you can do with it. Our ambition is to give the React community the fastest way to get from idea to production-grade code, and our roadmap for the remainder of the year includes a lot of improvements to the design and build experience.

To make that ambition a reality, we have one more thing to share: Utopia is an open-source, MIT-licensed software project hosted on Github. If you’re interested in connecting design and code, want to contribute and discuss ideas about anything from product-centric colour pickers to ideas for visually manipulating data flows, or are excited about real-time code manipulation, we’d love to hear from you (whether you write code or not!). Play with Utopia, check out Github, and join our Discord.