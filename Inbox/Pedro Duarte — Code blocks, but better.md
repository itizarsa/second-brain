# Pedro Duarte — Code blocks, but better

Source: Article
Status: Unprocessed
URL: https://ped.ro/blog/code-blocks-but-better

[https://i.microlink.io/https%3A%2F%2Fcards.microlink.io%2F%3Fpreset%3Dpedro%26title%3DCode%20blocks%2C%20but%20better%26domain%3Dhttps%3A%2F%2Fped.ro%2Fblog%2Fcode-blocks-but-better](https://i.microlink.io/https%3A%2F%2Fcards.microlink.io%2F%3Fpreset%3Dpedro%26title%3DCode%20blocks%2C%20but%20better%26domain%3Dhttps%3A%2F%2Fped.ro%2Fblog%2Fcode-blocks-but-better)

---

I've been exploring ways to improve the user experience of code blocks.

I've been spending a lot of time writing documentation for the [Modulz](https://modulz.app/) products. Specifically for [Stitches](https://stitches.dev/) and [Radix](https://radix-ui.com/). And I wanted more than just pretty colors.

This was my wishlist:

- Syntax highlight
- Apply multiple themes
- Highlight specific lines
- Highlight specific words
- Interact with the content
- Make specific words link to other pages
- Show line numbers
- Make it collapsible/expandable
- Render a preview

In this post, I'll share with you how I built a custom code block component.

Disclaimer: this is not a tutorial, but I hope you can discover something new.

## But first, demos

I'll be using the code block of my own website as the demo. It looks like this:

### Syntax highlight

A minimal demo, showing the syntax highlighting:

```
  const [count, setCount] = React.useState(initialCount);
{count}

```

### Apply multiple themes

Render the code block in different styles. Like this orange theme:

```
  const [count, setCount] = React.useState(initialCount);
{count}

```

Or this pink theme:

```
  const [count, setCount] = React.useState(initialCount);
  return (
{count}

```

Or turquoise:

```
  const [count, setCount] = React.useState(initialCount);
  return (
{count}

```

### Highlight specific lines

Drive attention to specific parts in the code:

```
  const [count, setCount] = React.useState(initialCount);
  return (
{count}
  );

```

### Highlight specific words

Drive attention to specific words in the code:

```
  const [count, setCount] = React.useState(initialCount);
  return (
{count}
  );

```

### Interact with the content

Create connections between the content and the code block.

Try it yourself, `hover me` and watch the code block:

```
  const [count, setCount] = React.useState(initialCount);
  return (
{count}
  );

```

### Make specific words link to other pages

Click a highlighted word to navigate to a different page:

```
  const [count, setCount] = React.useState(initialCount);
  return (
{count}
  );

```

### Show line numbers

Choose whether to display line numbers or not:

```
  const [count, setCount] = React.useState(initialCount);
  return (
{count}
  );

```

### Render a preview

Render an interactive preview of what your code block is showing. Click the button!

```
<Counter initialCount={32} />

```

### Make it collapsible/expandable

Option to have the code block collapsed:

## Context

I've built this to work on Next.js projects. For `.mdx` support, I've used it with [mdx-bundler](https://github.com/kentcdodds/mdx-bundler) and [next-mdx-remote](https://github.com/hashicorp/next-mdx-remote).

However, any framework/library that supports rehype plugins should work fine.

I've split the code in two parts: rehype and UI. I think it's easier to show the entire files at first, and how they work together. Then I'll breakdown some useful steps.

## Part 1 - MDX and rehype

This part is where the code block features happen. Syntax, line and word highlighting and MDX component substitution.

### Dependencies

```
yarn add unist-util-visit refractor hast-util-to-string hast-util-to-html unified rehype-parse parse-numeric-range

```

### rehype-highlight-code

This is the main rehype plugin. This is where we handle syntax (thanks to [refractor](https://github.com/wooorm/refractor)), line and word highlighting. Inspired by [mdx-prism](https://github.com/j0lv3r4/mdx-prism).

```
const rangeParser = require('parse-numeric-range');
const visit = require('unist-util-visit');
const nodeToString = require('hast-util-to-string');
const refractor = require('refractor');
const highlightLine = require('./rehype-highlight-line');
const highlightWord = require('./rehype-highlight-word');
  return (tree) => {
    visit(tree, 'element', visitor);
  };
    if (parentNode.tagName === 'pre' && node.tagName === 'code') {
      const lang = node.properties.className ? node.properties.className[0].split('-')[1] : 'md';
      let result = refractor.highlight(nodeToString(node), lang);
      const linesToHighlight = rangeParser(node.properties.line || '0');
      result = highlightLine(result, linesToHighlight);
      result = highlightWord(result);
      node.children = result;

```

### rehype-highlight-line

This is a rehype utility for highlighting lines.

```
const hastToHtml = require('hast-util-to-html');
const unified = require('unified');
const parse = require('rehype-parse');
  let lineNumber = lineNum;
  return ast.reduce(
      if (node.type === 'text') {
        if (node.value.indexOf('\n') === -1) {
          node.lineNumber = lineNumber;
          result.nodes.push(node);
          return result;
        const lines = node.value.split('\n');
        for (let i = 0; i < lines.length; i++) {
          if (i !== 0) ++lineNumber;
          if (i === lines.length - 1 && lines[i].length === 0) continue;
          result.nodes.push({
            type: 'text',
          });
        result.lineNumber = lineNumber;
        return result;
      if (node.children) {
        node.lineNumber = lineNumber;
        const processed = lineNumberify(node.children, lineNumber);
        node.children = processed.nodes;
        result.lineNumber = processed.lineNumber;
        result.nodes.push(node);
        return result;
      result.nodes.push(node);
      return result;
    { nodes: [], lineNumber: lineNumber }
};
const wrapLines = function wrapLines(ast, linesToHighlight) {
  const highlightAll = linesToHighlight.length === 1 && linesToHighlight[0] === 0;
  const allLines = Array.from(new Set(ast.map((x) => x.lineNumber)));
  let i = 0;
  const wrapped = allLines.reduce((nodes, marker) => {
    const line = marker;
    const children = [];
    for (; i < ast.length; i++) {
      if (ast[i].lineNumber < line) {
        nodes.push(ast[i]);
      if (ast[i].lineNumber === line) {
        children.push(ast[i]);
      if (ast[i].lineNumber > line) {
    nodes.push({
      type: 'element',
      tagName: 'div',
      properties: {
        className: 'highlight-line',
        dataHighlighted: linesToHighlight.includes(line) || highlightAll ? 'true' : 'false',
      children: children,
    });
    return nodes;
  }, []);
  return wrapped;
};
const applyMultilineFix = function (ast) {
  let html = hastToHtml(ast);
  );
  const hast = unified().use(parse, { emitParseErrors: true, fragment: true }).parse(html);
  return hast.children;
};
module.exports = function (ast, lines) {
  const formattedAst = applyMultilineFix(ast);
  const numbered = lineNumberify(formattedAst).nodes;
  return wrapLines(numbered, lines);

```

### rehype-highlight-word

This is a rehype utility for highlighting a word.

```
const visit = require('unist-util-visit');
const hastToHtml = require('hast-util-to-html');
const unified = require('unified');
const parse = require('rehype-parse');
module.exports = (code) => {
  const html = hastToHtml(code);
  const hast = unified().use(parse, { emitParseErrors: true, fragment: true }).parse(result);
  return hast.children;

```

### rehype-meta-attribute

This plugin passes the `meta` as props when substituting components. More [info here](https://github.com/wooorm/xdm#syntax-highlighting-with-the-meta-field).

```
const visit = require('unist-util-visit');
var re = /\b([-\w]+)(?:=(?:"([^"]*)"|'([^']*)'|([^"'\s]+)))?/g;
  return (tree) => {
    visit(tree, 'element', visitor);
  };
    if (node.tagName === 'code' && node.data && node.data.meta) {
      re.lastIndex = 0; // Reset regex.
      while ((match = re.exec(node.data.meta))) {
        node.properties[match[1]] = match[2] || match[3] || match[4] || '';
        parentNode.properties[match[1]] = match[2] || match[3] || match[4] || '';

```

### mdx-bundler

Now I need to tell mdx-bundler to use the `rehype-highlight-code` and the `rehype-meta-attribute` plugins. This is done via the [xmdOptions](https://github.com/kentcdodds/mdx-bundler#xdmoptions).

```
import rehypeHighlightCode from './rehype-highlight-code';
import rehypeMetaAttribute from './rehype-meta-attribute';
bundleMDX(source, {
    options.rehypePlugins = [
      ...(options.rehypePlugins ?? []),
    ];
    return options;
});

```

## Part 2 - UI

Next, these are the dependencies I rely on:

### Dependencies

### Pre component

The `rehype-highlight-code` plugin wraps the content of my code block in various `span` elements with different classes, such as `function`, `operator`, `keyword`, etc.

I was then able to target these classes and style them. To do this in a maintainable way, I used [Stitches](https://stitches.dev/).

With Stitches, I can create a theme and then use its tokens to later style the syntax highlight. But if you don't want to create your own, you can use [Prism themes](https://github.com/PrismJS/prism-themes).

```
export const { styled } = createCss({
  theme: {
      mono: 'Fira Mono, monospace',
      1: '12px',
      2: '14px',
      black: 'rgba(19, 19, 21, 1)',
      white: 'rgba(255, 255, 255, 1)',
      gray: 'rgba(128, 128, 128, 1)',
      blue: 'rgba(3, 136, 252, 1)',
      red: 'rgba(249, 16, 74, 1)',
      yellow: 'rgba(255, 221, 0, 1)',
      pink: 'rgba(232, 141, 163, 1)',
      turq: 'rgba(0, 245, 196, 1)',
      orange: 'rgba(255, 135, 31, 1)',
      1: '4px',
      2: '8px',
      3: '16px',
      1: '2px',
      2: '4px',
});

```

Now that Stitches is set up, I could import the `styled` function and use it to style the `pre` element.

```
export const Pre = styled('pre', {
  $$background: 'hsla(206 12% 89.5% / 5%)',
  $$text: '$colors$white',
  $$syntax1: '$colors$orange',
  $$syntax2: '$colors$turq',
  $$syntax3: '$colors$pink',
  $$syntax4: '$colors$pink',
  $$comment: '$colors$gray',
  $$removed: '$colors$red',
  $$added: '$colors$turq',
  boxSizing: 'border-box',
  padding: '$3',
  overflow: 'auto',
  fontFamily: '$mono',
  fontSize: '$2',
  lineHeight: '$3',
  whiteSpace: 'pre',
  backgroundColor: '$$background',
  color: '$$text',
  '& > code': { display: 'block' },
  '.token.parameter': {
    color: '$$text',
  '.token.tag, .token.class-name, .token.selector, .token.selector .class, .token.function': {
    color: '$$syntax1',
  '.token.attr-value, .token.class, .token.string, .token.number, .token.unit, .token.color': {
    color: '$$syntax2',
  '.token.attr-name, .token.keyword, .token.rule, .token.operator, .token.pseudo-class, .token.important': {
    color: '$$syntax3',
  '.token.punctuation, .token.module, .token.property': {
    color: '$$syntax4',
  '.token.comment': {
    color: '$$comment',
  '.token.atapply .token:not(.rule):not(.important)': {
    color: 'inherit',
  '.language-shell .token:not(.comment)': {
    color: 'inherit',
  '.language-css .token.function': {
    color: 'inherit',
  '.token.deleted:not(.prefix), .token.inserted:not(.prefix)': {
    display: 'block',
    px: '$4',
    mx: '-$4',
  '.token.deleted:not(.prefix)': {
    color: '$$removed',
  '.token.inserted:not(.prefix)': {
    color: '$$added',
  '.token.deleted.prefix, .token.inserted.prefix': {
    userSelect: 'none',
});

```

Let me go through it step-by-step.

### 1. Creating a component

I'm importing the `styled` function from `stitches.config.ts`. That's where we did the setup, to provide Stitches with our theme. Then I use the `styled` function to create a Stitches component.

```
export const Pre = styled('pre', {...});

```

### 2. Creating locally scoped tokens

I took advantage of Stitches' [locally-scoped tokens](https://stitches.dev/docs/api#locally-scoped-tokens) to define some variables that I'll then use to highlight the syntax.

This came in super handy when creating additional themes. Keep reading...

```
export const Pre = styled('pre', {
  $$background: 'hsla(206 12% 89.5% / 5%)',
  $$text: '$colors$white',
  $$syntax1: '$colors$orange',
  $$syntax2: '$colors$turq',
  $$syntax3: '$colors$pink',
  $$syntax4: '$colors$pink',
  $$comment: '$colors$gray',
  $$removed: '$colors$red',
  $$added: '$colors$turq',
});

```

### 3. Adding base styles

Then I added the base styles for the `pre` and `code` elements.

```
export const Pre = styled('pre', {
  boxSizing: 'border-box',
  padding: '$3',
  overflow: 'auto',
  fontFamily: '$mono',
  fontSize: '$2',
  lineHeight: '$3',
  whiteSpace: 'pre',
  backgroundColor: '$$background',
  color: '$$text',
  '& > code': { display: 'block' },
});

```

### 4. Adding syntax styles

I could target the classes generated by the rehype plugin and add syntax highlighting. I referenced the locally-scoped tokens with Stitches by using `$$` (two dollar signs).

```
export const Pre = styled('pre', {
  '.token.parameter': {
    color: '$$text',
  '.token.tag, .token.class-name, .token.selector, .token.selector .class, .token.function': {
    color: '$$syntax1',
  '.token.attr-value, .token.class, .token.string, .token.number, .token.unit, .token.color': {
    color: '$$syntax2',
  '.token.attr-name, .token.keyword, .token.rule, .token.operator, .token.pseudo-class, .token.important': {
    color: '$$syntax3',
  '.token.punctuation, .token.module, .token.property': {
    color: '$$syntax4',
  '.token.comment': {
    color: '$$comment',
  '.token.atapply .token:not(.rule):not(.important)': {
    color: 'inherit',
  '.language-shell .token:not(.comment)': {
    color: 'inherit',
  '.language-css .token.function': {
    color: 'inherit',
  '.token.deleted:not(.prefix), .token.inserted:not(.prefix)': {
    display: 'block',
    px: '$4',
    mx: '-$4',
  '.token.deleted:not(.prefix)': {
    color: '$$removed',
  '.token.inserted:not(.prefix)': {
    color: '$$added',
  '.token.deleted.prefix, .token.inserted.prefix': {
    userSelect: 'none',
});

```

### Creating multiple themes

I relied on the Stitches [Variant API](https://stitches.dev/docs/variants) to create multiple variations of the `Pre` component.

Creating multiple themes was as simple as overriding the previously created locally-scoped tokens. Love it!

```
export const Pre = styled('pre', {
        $$background: 'rgb(255 135 31 / 10%)',
        $$syntax1: '$colors$pink',
        $$syntax2: '$colors$turq',
        $$syntax3: '$colors$orange',
        $$syntax4: '$colors$orange',
        $$background: 'hsl(345deg 66% 73% / 20%)',
        $$syntax1: '$colors$orange',
        $$syntax2: '$colors$turq',
        $$syntax3: '$colors$pink',
        $$syntax4: '$colors$pink',
        $$background: 'rgba(0, 245, 196, 0.15)',
        $$syntax1: '$colors$orange',
        $$syntax2: '$colors$pink',
        $$syntax3: '$colors$turq',
        $$syntax4: '$colors$turq',
});

```

### Adding line highlight styles

I also used the Stitches Variant power to add styles specific to line highlighting.

```
export const Pre = styled('pre', {
      true: {
        '.highlight-line': {
          position: 'relative',
          paddingLeft: '$4',
          '&::before': {
            content: 'attr(data-line)',
            position: 'absolute',
            left: -5,
            top: 0,
            color: '$$lineNumbers',
});

```

### Preview component

I created a `Preview` component, which was made available within MDX files. This will come in handy when combining a preview and a code block together, like this [this example](https://ped.ro/blog/code-blocks-but-better).

Note: I've left out the styles, but this is just a React Component, so you can style it however you want.

## Part 3 - Component substitution

I used XDM's [component substitution](https://github.com/kentcdodds/mdx-bundler#component-substitution) to replace the MDX components with React components.

```
const components = {
{children}
    const isCollapsible = typeof collapsible !== 'undefined';
    const [isOpen, setIsOpen] = React.useState(!isCollapsible);
    return isCollapsible ? (
    ) : (
    const isExternal = href.startsWith('http');
    React.useEffect(() => {
      const codeBlock = document.getElementById(id);
      if (!codeBlock) return;
      const allHighlightWords = codeBlock.querySelectorAll('.highlight-word');
      const target = allHighlightWords[index - 1];
      if (!target) return;
      target.replaceWith(
        Object.assign(document.createElement('a'), {
          innerHTML: target.innerHTML,
          className: target.className,
          ...(isExternal ? { target: '_blank', rel: 'noopener' } : {}),
    }, []);
    return null;
    const triggerRef = React.useRef < HTMLElement > null;
    React.useEffect(() => {
      const trigger = triggerRef.current;
      const codeBlock = document.getElementById(id);
      if (!codeBlock) return;
      const allHighlightWords = codeBlock.querySelectorAll('.highlight-word');
      const targetIndex = rangeParser(index).map((i) => i - 1);
      if (Math.max(...targetIndex) >= allHighlightWords.length) return;
      const addClass = () => targetIndex.forEach((i) => allHighlightWords[i].classList.add('on'));
      const removeClass = () =>
        targetIndex.forEach((i) => allHighlightWords[i].classList.remove('on'));
      trigger.addEventListener('mouseenter', addClass);
      trigger.addEventListener('mouseleave', removeClass);
      return () => {
        trigger.removeEventListener('mouseenter', addClass);
        trigger.removeEventListener('mouseleave', removeClass);
    }, []);

```

Let me explain a little bit what's going on here.

- Meta properties are automatically passed in as props to both the `pre` and `code` functions, thanks to the `rehype-meta-attribute` rehype plugin
- The `pre` element gets replaced with the `Pre` component
- The `code` element is used both by inline code and code blocks
- The `RegisterLink` component is used to [make-specific-words-link-to-other-pages](https://ped.ro/blog/code-blocks-but-better)

## Part 4 - Usage

Finally, this section shows how each feature can be used.

### Using a basic code block

Similarly to markdown, in mdx you open a code block with triple backticks `````. The language is added immediately after it.

For example, an HTML code block:

```
```html
<h1>Hello world</h1>
```

```

Or a JSX code block:

```
```jsx
import React from 'react'

function Hello() {
  return <h1>Hello world</h1>
}
```

```

### Using themes

I can choose which theme I want to use directly in MDX by passing it as a meta property.

If I want to use the orange theme:

```
```jsx theme=orange
import React from 'react';

function Hello() {
  return <h1>Hello world</h1>;
}
```

```

Or the pink theme:

```
```jsx theme=pink
import React from 'react';

function Hello() {
  return <h1>Hello world</h1>;
}
```

```

### Using line highlights

Line highlights can be turned via the `line` meta property.

If I want to select line 3:

I can also use ranges:

Or multiple unique lines:

### Using word highlights

I can highlight specific words in the code block by wrapping them in `__` (double underscores).

```
```jsx
import React from '__react__';

function Hello() {
  return <h1>Hello world</h1>;
}
```

```

### Interacting with the content

I created a custom `H` component (for highlight), and that's what I use to create an interaction between the content and a highlighted word.

For it to work, I need to add an `id` to the code block. Then, I need to tell the `H` which `id` and which `index` to interact with. The index can also be a range.

It works like this:

### Registering links

I created a custom `RegisterLink` component, and that's what I use to make a highlighted word clickable.

For it to work, I need to add an `id` to the code block. Then, I need to render a self-closing `RegisterLink` component, providing the `id`, the `index` and the `href`.

It works like this:

### Showing line numbers

I can optionally show line numbers by passing it as a meta property.

### Rendering a preview

I can use the `Preview` component to render a preview of the code block.

I then use CSS adjacent selectors to style them, so they look like one UI.

### Making it collapsible/expandable

I can optionally make the code block collapsible by passing it as a meta property.

This is powered by the [Radix Collapsible Primitive](https://radix-ui.com/primitives/docs/components/collapsible).

## Conclusion

Are you still here? :D

I spent months thinking about building a custom code block. No jokes. I was scared of how much work it'd be and how long it'd take. I was worried about the maintenance debt.

But actually, it's really not as complex as it looks.

You're probably already familiar with a lot of what's going here if you use MDX component substitution.

It feels really good to have control over these code blocks. I spent a lot of time writing documentation for the [Modulz](https://modulz.app/) products and having access to these features really help me tell a better story.

I'm not planning on open-sourcing this or offering it as a package. It's not really an "isolated" thing. A lot of it depends on the power of MDX and styling.

But I hope this article motivates you and inspires you to create your own ❤️.