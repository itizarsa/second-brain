# Cooltipz.css - Cool customisable tooltips made from pure CSS

Source: Website
Status: Unprocessed
URL: https://cooltipz.jackdomleo.dev/

![https://cooltipz.jackdomleo.dev/img/open-graph.png](https://cooltipz.jackdomleo.dev/img/open-graph.png)

---

![open-graph.png](Cooltipz%20css%20-%20Cool%20customisable%20tooltips%20made%20fro%20937d11e3de724f9dab674faa2ca22ac5/open-graph.png)

To get started using Cooltipz.css in your project, all you need to do is:

1. [Install](https://cooltipz.jackdomleo.dev/) cooltipz-css via CDN, npm or yarn
2. Add an `aria-label` and a [direction](https://cooltipz.jackdomleo.dev/) to any non self-closing HTML tag
3. (Optional) Add any modifiers and/or [customise](https://cooltipz.jackdomleo.dev/) your own tooltip

Depending on your preference, you can choose to use classes or `data-` attributes.

### CDN

In the below CDN links:

- Replace `:version` with a version [listed here](https://www.npmjs.com/package/cooltipz-css?activeTab=versions) (latest version is always recommended). If you always want to get the latest stylesheet, remove `@:version` completely (Not recommended).
- Replace `:file` with one of the below
    - `cooltipz.css` (Expanded stylesheet)
    - `cooltipz.min.css` (Minified stylesheet)
- Then import via HTML or CSS

```
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/cooltipz-css@:version/:file" />
```

```
@import url('https://cdn.jsdelivr.net/npm/cooltipz-css@:version/:file');
```

### Package manager (npm or yarn)

*Or*, import the SCSS or CSS into your Sass/SCSS

In the below imports, replace `:file` with one of the options below:

- `src/cooltipz` (.scss file)
- `cooltipz.css` (Expanded .css)
- `cooltipz.min.css` (Minified .css)

```
/* Webpack */
@import '~cooltipz-css/:file';

/* Non webpack */
@import 'path/to/node_modules/cooltipz-css/:file';
```

**Exactly one** direction value is required.

```
<button aria-label="Tooltip message" data-cooltipz-dir="top">...</button>
<!-- OR -->
<button aria-label="Tooltip message" class="cooltipz--top">...</button>
```

Now you have your basic tooltip, try some of the modifiers and try customising your own tooltip.

By default, the tooltip's content will not wrap. If you want the tooltip content to wrap, use one of the *size modifiers* below.

```
<button aria-label="Tooltip message" data-cooltipz-dir="top" data-cooltipz-size="fit">...</button>
<!-- OR -->
<button aria-label="Tooltip message" class="cooltipz--top cooltipz--fit">...</button>
```

You can disable animation for a single tooltip:

```
<button aria-label="Tooltip message" data-cooltipz-dir="top" data-cooltipz-static>...</button>
<!-- OR -->
<button aria-label="Tooltip message" class="cooltipz--top cooltipz--static">...</button>
```

Or you can disable animation on **all** tooltips by customising the `--cooltipz-timing` custom property:

```
:root {
  --cooltipz-timing: 0;
}
```

Animation is automatically disabled if the user's preferences are set to [prefers reduced motion](https://developer.mozilla.org/en-US/docs/Web/CSS/@media/prefers-reduced-motion).

You can make a tooltip always appear:

```
<button aria-label="Tooltip message" data-cooltipz-dir="top" data-cooltipz-visible>...</button>
<!-- OR -->
<button aria-label="Tooltip message" class="cooltipz--top cooltipz--visible">...</button>
```

This can also be useful if you need to programmatically show a tooltip.

Not a problem.

```
<button aria-label="&copy; &reg; &#9742; &#9850; &#8709; 😎🚗🍔💩👏✔❤ ਸਤ ਸ੍ਰੀ ਅਕਾਲ" data-cooltipz-dir="top" data-cooltipz-visible>...</button>
```

A **little** setup is required to use Font Awesome's unicode values in the tooltip's `aria-label` attribute.

You will need to set a value for the `--cooltipz-fontawesome` custom property.

```
<button aria-label="&#xf03e; &#xf200; &#xf188; &#xf007;" data-cooltipz-dir="top">...</button>
```

### Font Awesome 4

### Font Awesome 5

There are **13** custom properties for you to customise your own tooltips.

To customise **all** tooltips, place your custom properties in the `:root` selector:

```
:root {
  --cooltipz-bg-color: #ffffff;
  --cooltipz-text-color: #000000;
  --cooltipz-font-size: 1.2rem;
}
```

Or you can customise specific tooltips. The below example will customise any tooltips on the `.custom` element **and** and children of it:

```
.custom {
  --cooltipz-arrow-size: 1.5rem;
  --cooltipz-cursor: help;
  --cooltipz-timing: 0;
}
```

See our [CodePen](https://codepen.io/jackdomleo7/pen/mderEeG) for lots of examples of customisation:

**Important**: Cooltipz.css uses the `::before` and `::after` psuedo elements to display the tooltips, so be cautious of the following:

- Tooltips will not work on self-closing HTML elements because they don't have a `::before` and `::after` psuedo element.
- If the HTML element already has existing `::before` or `::after` styling, these could conflict with the Cooltipz.css styles and cause unexpected outputs.

We appreciate any feedback, good or bad and are always looking for new ideas to improve the user experience (UX), developer experience (DX) and accessibility of the tooltips. You may want to consider:

Cooltipz.css is licensed under [MIT](https://github.com/jackdomleo7/Cooltipz.css#license). As a minimum, you are required to KEEP AND NOT REMOVE the following code at the beginning of your downloaded/installed Cooltipz.css CSS, where `:version` is replaced with the version number you are using:

```
/*! Cooltipz.css v:version | MIT License | github.com/jackdomleo7/Cooltipz.css */
```

Cooltipz.css is FREE for personal and commercial use.

Commercial use should consider a small donation on [Buy Me a Coffee](https://www.buymeacoffee.com/jackdomleo7).