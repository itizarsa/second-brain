# UI Devtools for Tailwind CSS

Source: Website
Status: Unprocessed
URL: https://www.ui-devtools.com/

![https://ui-devtools.com/summary_card.png](https://ui-devtools.com/summary_card.png)

---

But, authoring styles in code feels a bit awkward.

Styling is a visual task, to do it in text feels like you have the wrong tools.

This friction is especially visible if you use a utility or tokens based framework like Tailwind CSS. You need to continously shift your focus between the code and preview in a hit and trial attempt to get to the right class.

![UI%20Devtools%20for%20Tailwind%20CSS%20a32cbf3cc20c4614b344c58fc1f4ee0d/color-trial.gif](UI%20Devtools%20for%20Tailwind%20CSS%20a32cbf3cc20c4614b344c58fc1f4ee0d/color-trial.gif)

try and try again till you succeed to pick the perfect color.

I hope that your compile step is fast enough to at least give you feedback quickly. Wouldn't wish the frustrations of working with a slow feedback loop even on my enemies!

Browser devtools were built to help us with this. But, when the abstraction level of the devtool (css / hex codes) doesn't match the abstraction at which you author code (tokens based utility classes), it stops being as useful.

![UI%20Devtools%20for%20Tailwind%20CSS%20a32cbf3cc20c4614b344c58fc1f4ee0d/copy-color.gif](UI%20Devtools%20for%20Tailwind%20CSS%20a32cbf3cc20c4614b344c58fc1f4ee0d/copy-color.gif)

I miss copy paste

You can translate the raw css to the abstraction level you author in (#9061f9 → purple-500, 40px → 2.5rem)

OR

You can upgrade your tooling to the abstraction level you author in.

## Better tooling

UI Devtools is an attempt at better tooling for developers. This is what the above task looks like with the right tool:

![UI%20Devtools%20for%20Tailwind%20CSS%20a32cbf3cc20c4614b344c58fc1f4ee0d/instant-color.gif](UI%20Devtools%20for%20Tailwind%20CSS%20a32cbf3cc20c4614b344c58fc1f4ee0d/instant-color.gif)

Make visual choices visually with instant feedback before making a decision.

Colors are picked from your tailwind config.

So are the space units:

![UI%20Devtools%20for%20Tailwind%20CSS%20a32cbf3cc20c4614b344c58fc1f4ee0d/margin2.gif](UI%20Devtools%20for%20Tailwind%20CSS%20a32cbf3cc20c4614b344c58fc1f4ee0d/margin2.gif)

The right medium with the right options

It's not a design tool.

It's a developer tool, for design tasks.

## Save changes back to source.

All changes you make "visually" are made back to the source with the correct Tailwind CSS classes based on your config - exactly like you would.

This is a big productivity boost!

![UI%20Devtools%20for%20Tailwind%20CSS%20a32cbf3cc20c4614b344c58fc1f4ee0d/code-sync.gif](UI%20Devtools%20for%20Tailwind%20CSS%20a32cbf3cc20c4614b344c58fc1f4ee0d/code-sync.gif)

Changes are committed back to code.

## How does it work?

Three steps:

1

import { Devtools } from '@ui-devtools/tailwind' and wrap your application root with <Devtools>

2

npx devtools-server -c tailwind.config.js in the terminal to run the server that syncs changes back to source (for React projects)

## See it in action:

Syncing changes back to source code only works with React projects today.

## Get access

UI Devtools for Tailwind CSS is maintained as sponsorware.

To ensure this project:

- stays updated with breaking and non-breaking releases of TailwindCSS
- keeps improving as a visual tool
- adds support for other stacks like Vue and good old HTML
- doesn't fade away over time
- is run as a sustainable open source project

It is available only to GitHub Sponsors till it reaches the sustainability goal of 100 sponsors. After that, it will be open source.

As a GitHub sponsor, you get access to the private package and code repository today, several months before everyone else, and help shape the project with your feedback.

Thank you to the folks who sponsor my work: