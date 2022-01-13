# Popper - Tooltip & Popover Positioning Engine

Source: Website
Status: Unprocessed
URL: https://popper.js.org/

![https://popper.js.org/images/popper-og-image.jpg](https://popper.js.org/images/popper-og-image.jpg)

---

Weighs just **3 kB!**

![Popper%20-%20Tooltip%20&%20Popover%20Positioning%20Engine%204dc902e1ee7649af98f266f7c3270db2/popcorn-box-f16f5d64e675baca26519478e88e4961.svg](Popper%20-%20Tooltip%20&%20Popover%20Positioning%20Engine%204dc902e1ee7649af98f266f7c3270db2/popcorn-box-f16f5d64e675baca26519478e88e4961.svg)

**Click on the dots** to place the tooltip. There are 12 different placements to choose from.

```
import { createPopper } from '@popperjs/core';const popcorn = document.querySelector('#popcorn');const tooltip = document.querySelector('#tooltip');createPopper(popcorn, tooltip, {  placement: 'top',
```

**Scroll the container** (or the whole page) to see the tooltip stay within the boundary. Once the opposite edges of the popcorn and tooltip are aligned, the tooltip is allowed to overflow to prevent detachment.

```
import { createPopper } from '@popperjs/core';const popcorn = document.querySelector('#popcorn');const tooltip = document.querySelector('#tooltip');createPopper(popcorn, tooltip, {  placement: 'right',
```

**Scroll the container** (or the whole page) to see the tooltip flip to the opposite side once it's about to overflow the visible area. Once enough space is detected on its preferred side, it will flip back.

```
import { createPopper } from '@popperjs/core';const popcorn = document.querySelector('#popcorn');const tooltip = document.querySelector('#tooltip');createPopper(popcorn, tooltip);
```

### In a nutshell, Popper:

- **Places your tooltip or popover relative to the reference** taking into account their sizes, and positions its arrow centered to the reference.
- **Takes into account the many different contexts it can live in** relative to the reference (different offsetParents, different or nested scrolling containers).
- **Keeps your tooltip or popover in view as best as possible**. It prevents it from being clipped or cut off (overflow prevention) and changes the placement if the original does not fit (flipping).

### Granular configuration with sensible defaults

Popper aims to "just work" without you needing to configure much. Of course, there are cases where you need to configure Popper beyond its defaults – in these cases, Popper shines by offering high granularity of configuration to fine-tune the position or behavior of your popper.

You can extend Popper with your own modifiers (or plugins) to make your popper work for you, no matter how advanced the scenario.

### No compromises

- **No detachment**. Position updates take less than a millisecond on average devices. Popper doesn't debounce the positioning updates of the tooltip to the point where it will *ever* detach from its reference, but this doesn't come at the cost of poor performance.
- **You don't have to change the DOM context of your tooltip or popover element**; it will work no matter where your popper and reference elements live, even in the most complex scenarios like nested scrolling containers or alternative offsetParent contexts.
- **Still lightweight**. Handling all of this complexity is still done in an efficient manner. The base Popper is only 2 kB minzipped.

### Free open-source, used by millions

Popper has billions of hits across the web, is trusted by millions of developers in production, and used in popular libraries like Bootstrap and Material UI.

[Support us](https://opencollective.com/popperjs)

### Ready to start?