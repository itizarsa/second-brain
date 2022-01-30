# A Complete Guide to Grid | CSS-Tricks

Source: Article
Status: Unprocessed
URL: https://css-tricks.com/snippets/css/complete-guide-grid/

[https://css-tricks.com/wp-json/social-image-generator/v1/image/343682](https://css-tricks.com/wp-json/social-image-generator/v1/image/343682)

---

As of March 2017, most browsers shipped native, unprefixed support for CSS Grid: Chrome (including on Android), Firefox, Safari (including on iOS), and Opera. Internet Explorer 10 and 11 on the other hand support it, but it’s an old implementation with an outdated syntax. The time to build with grid is now!

To get started you have to define a container element as a grid with , set the column and row sizes with  and , and then place its child elements into the grid with  and . Similarly to flexbox, the source order of the grid items doesn’t matter. Your CSS can place them in any order, which makes it super easy to rearrange your grid with media queries. Imagine defining the layout of your entire page, and then completely rearranging it to accommodate a different screen width all with only a couple lines of CSS. Grid is one of the most powerful CSS modules ever introduced.

![A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/template-columns-rows-01.svg](A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/template-columns-rows-01.svg)

![A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/template-column-rows-02.svg](A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/template-column-rows-02.svg)

![A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/dddgrid-template-areas.svg](A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/dddgrid-template-areas.svg)

![A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/dddgrid-gap.svg](A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/dddgrid-gap.svg)

![A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/justify-items-start.svg](A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/justify-items-start.svg)

![A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/justify-items-end.svg](A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/justify-items-end.svg)

![A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/justify-items-center.svg](A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/justify-items-center.svg)

![A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/justify-items-stretch.svg](A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/justify-items-stretch.svg)

![A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/align-items-start.svg](A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/align-items-start.svg)

![A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/align-items-end.svg](A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/align-items-end.svg)

![A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/align-items-center.svg](A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/align-items-center.svg)

![A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/align-items-stretch.svg](A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/align-items-stretch.svg)

![A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/justify-content-start.svg](A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/justify-content-start.svg)

![A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/justify-content-end.svg](A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/justify-content-end.svg)

![A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/justify-content-center.svg](A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/justify-content-center.svg)

![A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/justify-content-stretch.svg](A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/justify-content-stretch.svg)

![A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/justify-content-space-around.svg](A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/justify-content-space-around.svg)

![A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/justify-content-space-between.svg](A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/justify-content-space-between.svg)

![A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/justify-content-space-evenly.svg](A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/justify-content-space-evenly.svg)

![A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/align-content-start.svg](A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/align-content-start.svg)

![A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/align-content-end.svg](A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/align-content-end.svg)

![A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/align-content-center.svg](A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/align-content-center.svg)

![A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/align-content-stretch.svg](A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/align-content-stretch.svg)

![A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/align-content-space-around.svg](A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/align-content-space-around.svg)

![A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/align-content-space-between.svg](A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/align-content-space-between.svg)

![A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/align-content-space-evenly.svg](A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/align-content-space-evenly.svg)

![A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/grid-auto-columns-rows-01.svg](A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/grid-auto-columns-rows-01.svg)

![A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/grid-auto-columns-rows-02.svg](A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/grid-auto-columns-rows-02.svg)

![A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/grid-auto-columns-rows-03.svg](A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/grid-auto-columns-rows-03.svg)

![A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/grid-auto-flow-01.svg](A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/grid-auto-flow-01.svg)

![A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/grid-auto-flow-02.svg](A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/grid-auto-flow-02.svg)

![A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/grid-column-row-start-end-01.svg](A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/grid-column-row-start-end-01.svg)

![A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/grid-column-row-start-end-02.svg](A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/grid-column-row-start-end-02.svg)

![A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/grid-column-row.svg](A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/grid-column-row.svg)

![A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/grid-area.svg](A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/grid-area.svg)

![A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/justify-self-start.svg](A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/justify-self-start.svg)

![A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/justify-self-end.svg](A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/justify-self-end.svg)

![A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/justify-self-center.svg](A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/justify-self-center.svg)

![A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/justify-self-stretch.svg](A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/justify-self-stretch.svg)

![A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/align-self-start.svg](A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/align-self-start.svg)

![A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/align-self-end.svg](A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/align-self-end.svg)

![A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/align-self-center.svg](A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/align-self-center.svg)

![A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/align-self-stretch.svg](A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/align-self-stretch.svg)

![A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/place-self-center.svg](A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/place-self-center.svg)

![A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/place-self-center-stretch.svg](A%20Complete%20Guide%20to%20Grid%20CSS-Tricks%20684090053cb94cb5891212d69e7c5506/place-self-center-stretch.svg)