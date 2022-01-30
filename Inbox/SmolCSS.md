# SmolCSS

Source: Website
Status: Unprocessed
URL: https://smolcss.dev/

![https://smolcss.dev/smolcss.png](https://smolcss.dev/smolcss.png)

---

Create an intrinsically responsive grid layout, optionally using a CSS custom property to extend to variable contexts. Each column will resize at the same rate, and items will begin to break to a new row if the width reaches the `--min` value.

Create an intrinsically responsive grid layout, optionally using a CSS custom property to extend to variable contexts. Each column will resize at the same rate *until* reaching the `--min` width. At that point, the last item will break to a new row and fill any available space.

**Put down the CSS centering jokes**! This modern update is often the solution you're looking for to solve your centering woes.

Just in case you're not convinced, [see more centering solutions](https://moderncss.dev/complete-guide-to-centering-in-css/) on ModernCSS.dev

Several layers of delicous modern CSS goodness here! First, we're using `fit-content` to handle the sidebar sizing. This allows the sidebar to grow *up to* the defined value, but only if it *needs to*, else it will use/shrink to the equivalent of `min-content`.

Next, we use `minmax` for the main content. Why? Because if we only use `1fr` then eventually our sidebar and main will share 50% of the space, and we want the main area to always be wider. We also nest `min` to ask the browser to use the minimum of *either* of the options. The result in this case is use of `50vw` on mobile-sized viewports, and `30ch` on larger viewports. And, when there's room, it also stretches to `1fr` for the *max* part of `minmax` 🙌🏽

This smol demo is using `clamp()` for responsive padding. The order of `clamp()` values can be interpreted as: the minimum allowed value is `1rem`, the ideal value is `5%` (which will be relative to the element), and the max allowed value is `3rem`.

In other words, as the element is placed in different contexts and resized across viewports, that value will grow and shrink. But it will always compute to a value within the range of `1rem` to `3rem`.

Another suggested option for the middle ideal value is to use a viewport unit, like `4vw`, which works great for components such as models or setting padding on the `body`.

Gummi bears gummies cheesecake donut liquorice sweet roll lollipop chocolate cake macaroon. Dragée powder biscuit. Dessert topping jelly beans liquorice cake sesame snaps oat cake chocolate bar marshmallow. Cookie danish jelly-o pudding tart chocolate. Jelly sweet tiramisu fruitcake dessert muffin chocolate cake dragée. Donut dragée carrot cake icing. Macaroon lemon drops muffin.

The `aspect-ratio` property is nearing support in all major modern browsers, and by combining it with `object-fit` and flexbox, we can create a smol responsive gallery. If you're using Chrome or Edge, check out the CSS via your your browser Inspector to modify the CSS custom properties on `.smol-aspect-ratio-gallery` and see how they affect this layout.

For now, we're using `@supports` checks to fallback to setting a height for list items if `aspect-ratio` is not yet supported to achieve a similar effect cross-browser.

Note that `aspect-ratio` isn't just for images, but any element!

> This solution also uses the Smol Responsive Flexbox Grid.
> 
- 
    
    [SmolCSS%206f2bc656a3594d88a02d1ae5fdc5b220/photo-1596401463492-1ca39cdf7575](SmolCSS%206f2bc656a3594d88a02d1ae5fdc5b220/photo-1596401463492-1ca39cdf7575)
    
- 
    
    [SmolCSS%206f2bc656a3594d88a02d1ae5fdc5b220/photo-1591756985756-6e231184528b](SmolCSS%206f2bc656a3594d88a02d1ae5fdc5b220/photo-1591756985756-6e231184528b)
    
- 
    
    [SmolCSS%206f2bc656a3594d88a02d1ae5fdc5b220/photo-1556195947-316050222289](SmolCSS%206f2bc656a3594d88a02d1ae5fdc5b220/photo-1556195947-316050222289)
    
- 
    
    [SmolCSS%206f2bc656a3594d88a02d1ae5fdc5b220/photo-1597264121870-2f1b4d43d2f6](SmolCSS%206f2bc656a3594d88a02d1ae5fdc5b220/photo-1597264121870-2f1b4d43d2f6)
    
- 
    
    [SmolCSS%206f2bc656a3594d88a02d1ae5fdc5b220/photo-1465566829994-b8da8cae5909](SmolCSS%206f2bc656a3594d88a02d1ae5fdc5b220/photo-1465566829994-b8da8cae5909)
    

For an alternate method to `aspect-ratio` on this solution, check out my [flexbox gallery egghead lesson](https://egghead.io/lessons/flexbox-create-an-automatically-responsive-flexbox-gallery?af=2s65ms). You may also enjoy my [egghead lesson on `object-fit`](https://egghead.io/lessons/css-apply-aspect-ratio-sizing-to-images-with-css-object-fit?af=2s65ms).

This component features `aspect-ratio` and leans heavily on the pseudo selectors of `:not()`, `:first-child`, and `:last-child`. The result is a composable card component that *just works* with your desired semantic internal content.

With [CSS Selectors Level 4](https://drafts.csswg.org/selectors-4/#negation), the enhanced version of `:not()` now allows a selector list. This ability is fairly [well supported in modern browsers](https://caniuse.com/css-not-sel-list).

**Note**: `aspect-ratio` is in progress rolling out to the latest versions of modern browsers. So, you may need to create fallbacks for your unique audience and consider this solution as a progressive enhancement. Fallback considerations are included as noted with comments.

> This solution also uses the Smol Responsive CSS Grid to contain the cards.
> 
- 
    
    [SmolCSS%206f2bc656a3594d88a02d1ae5fdc5b220/photo-1607274227313-08146c819e6f](SmolCSS%206f2bc656a3594d88a02d1ae5fdc5b220/photo-1607274227313-08146c819e6f)
    
    Card Headline 1
    
    Chocolate cake macaroon tootsie roll pastry gummies.
    
    Apple pie jujubes cheesecake ice cream gummies sweet roll lollipop.
    
- 
    
    Chocolate cake macaroon tootsie roll pastry gummies.
    
- 
    
    Apple pie jujubes cheesecake ice cream gummies sweet roll lollipop.
    

Learn more about CSS selectors in my two part guide, where part one covers [selectors and combinators](https://moderncss.dev/guide-to-advanced-css-selectors-part-one/) and part two covers [pseudo classes and pseudo elements](https://moderncss.dev/guide-to-advanced-css-selectors-part-two/).

This smol stacked layout is a grid feature that can often replace older techniques that relied on absolute positioning. It works by defining a single `grid-template-area` and then assigning all direct children to that `grid-area`. The children are then "stacked" and can take advantage of grid positioning, such as the centering technique in the demo.

At first glance you might not notice, but that's a video background in the demo. And all we had to do was set `width: 100%` to ensure it filled the grid area. Then, we make use of `place-self` on the `h3` to center it. The rest is completely optional design styling!

Bonus features in this demo include defining the `h3` size using `clamp()` for *viewport relative sizing*, and also using `aspect-ratio` to size the container to help reduce [cumulative layout shift](https://web.dev/cls/).

[video.mp4](https://smolcss.dev/assets/video.mp4)

### Into The Unknown

For more examples of creating smol stack layouts, review my guide to [website hero designs](https://moderncss.dev/3-popular-website-heroes-created-with-css-grid-layout/), see how it's used for [creating custom checkboxes](https://moderncss.dev/pure-css-custom-checkbox-style/), and learn to use it to [position animated image captions](https://moderncss.dev/animated-image-gallery-captions-with-bonus-ken-burns-effect/).

This smol component, which you may also know as a [facepile](https://indieweb.org/facepile), is possible due to the ability of CSS grid to easily create overlapping content. Paired with CSS custom properties and `calc()` we can make this a contextually resizeable component.

Based on devices capabilities, the grid columns are adjusted to slightly narrower than the `--avatar-size`. Since nothing inherent to CSS grid stops the content overflowing, it forces an overlap based on DOM order of the list items. To ensure perfect circle images, we first use the `--avatar-size` value to explicitly set the list item dimensions. Then by setting both width and height to `100%` on the `img` in addition to `object-fit: cover` and `border-radius: 50%`, we can be assured that regardless of actual image dimensions the contents will be forced into a circle appearance.

**Bonus trick #1** is the use of layered `box-shadow` values that only set a *spread* to create the appearance of borders without adding to the computed dimensions of the image. The spread values are set with `em` so that they are relative to the avatar size. And that works because we set the list's `font-size` to `--avatar-size`.

**Bonus trick #2** is using the *general sibling combinator* (`~`) so that on hover or `:focus-within` of an `li`, all linked images that follow animate over to reveal more of the hovered avatar. If the number of avatars will cause wrapping, you may want to choose a different effect such as changing the layering via `z-index`.

🔎 Pop open your browser devtools and experiment with changing the `--avatar-size` value!

ICYMI earlier - check out my quick [video lesson on object-fit](https://egghead.io/lessons/css-apply-aspect-ratio-sizing-to-images-with-css-object-fit?af=2s65ms) to learn more about how it works. Or you might enjoy more [methods for creating CSS borders](https://moderncss.dev/the-3-css-methods-for-adding-element-borders/) or see an additional [example of using `:focus-within`](https://moderncss.dev/css-only-accessible-dropdown-navigation-menu/). *Source images from [avataaars](https://getavataaars.com/)*.

This set of performant CSS transition utility classes include CSS custom properties for scaling the transition property and duration. We're doing a few things in this demo that you may want to keep in mind if you use them.

First, we're triggering the transition of the *child elements* on `:hover` of the parent. The reason for this is that for transitions that move the element, it could end up moving out from under the mouse and causing a flicker between states. The `rise` transition is particularly in danger of that behavior.

Second, we wrap our effect class in a media query check for `prefers-reduced-motion: reduce` that instantly jumps the transition to the final state. This is to comply with the request for reduced motion by effectively disabling the animated part of the transition.

Modern CSS has gifted us a series of properties that enable setting up more controlled scrolling experiences. In this demo, you'll find that as you begin to scroll, the middle items "snap" to the center of the scrollable area. Additionally, you are unable to scroll past more than one item at a time.

To align the scroll items, we're using grid and updating the orientation of child items using `grid-auto-flow: column`. Then the width of the grid children is set using `min()` which selects the *minimum computed value* between the options provided. The selected width options in this demo results in a large section of neighboring items being visible in the scrollable area for large viewports, while on smaller viewports the scrollable area is mostly consumed by the current scroll item.

*While this is a very cool feature set, use with care!* Be sure to test your implementation to ensure its not inaccessible. Test across a variety of devices, and with desktop zoom particularly at levels of 200% and 400% to check for overlap and how a changed aspect ratio affects scroll items. Try it out with a screen reader and make sure you can navigate to all content.

**Note**: Have caution when attempting to mix fullscreen scroll snap slideshows followed by normal flow content. This can damage the overall scrolling experience and even prevent access to content. Fullscreen scroll areas are also prone to issues for users of high desktop zoom due to high risk of overlapping content as the aspect ratio changes. In addition, fullscreen versions that use `y mandatory` result in "scroll hijacking" which can be frustrating to users.

Also - you may have a pleasant smooth scroll experience on a touchpad or magic mouse. But mouse users who rely on interacting with the scroll bar arrows or use a click wheel can have a jarring experience. This is due to browser and OS inconsistencies in handling the snapping based on input method (an issue was specifically reported for this demo using Chrome and Edge on PC).

- 
    
    Topping candy canes ice cream gummi bears gingerbread marshmallow. Chocolate cake powder sugar plum topping.
    
- 
    
    Cake marshmallow carrot cake. Pie liquorice liquorice sweet tootsie roll caramels donut dragée bear claw. Chocolate powder candy canes.
    
- 
    
    Pie chocolate cake dessert pastry candy canes donut pie soufflé pie. Fruitcake caramels tart pudding macaroon chocolate jelly beans brownie.
    
- 
    
    Icing dessert chocolate cupcake dragée sesame snaps. Icing pastry donut cupcake marshmallow sweet macaroon gummies.
    
- 
    
    Jelly wafer biscuit. Dessert halvah cheesecake. Liquorice jelly sweet roll marzipan biscuit
    

Anchor links have had quite an evolution over the years. Have you checked if your implementation is as accessible as it can be? This demo starts with an accessible DOM structure as [researched by Amber Wilson](https://amberwilson.co.uk/blog/are-your-anchor-links-accessible/), and then uses CSS grid to position the anchor link element.

**Note**: When using grid or flexbox to change the visual order vs the DOM order, always be cautious of breaking expectations in visual focus order. In this case, we know the headline itself will not contain a link and so we are still able to maintain a visually logical focus order.

This demo also features an old pseudo class that is often forgotten which is `:target`. Go ahead - click the anchor in this demo or across this site. Thanks to `:target` coupled with `::before`, you'll be greeted with a friendly message to help identify the *target* of the hashed URL.

Finally, we've also included `scroll-margin-top` which adds margin *only* to an active page target. In other words, upon clicking an anchor link or visiting the site with a hashed URL, the scroll point will be above the target by the value of `scroll-margin-top` (*not yet available in Safari*).

**Bonus**: Notice the properties set on `:focus` to adjust the `outline` position with `outline-offset`. And check out `:hover` to see `text-underline-offset` used to adjust the position of the underline.

[Learn more about the `:target` pseudo class](https://moderncss.dev/guide-to-advanced-css-selectors-part-two/) in part two of my guide to advanced CSS selectors.

Support for `::marker` is now available across all modern browsers! This pseudo-selector allows customizing the "bullet" for unordered lists and the numeral for ordered lists without other pseudo element hacks.

**Note**: `::marker` only allows a select few properties to be modified including `animation-*`, `color`, `content`, `direction`, `font-*`, `transition-*`, `unicode-bidi`, and `white-space`.

The use of `::marker` is a great progressive enhancement that can be used safely without any special consideration since the default experience should always acceptable.

**Bonus**: Check out how the emoji are being inserted thanks to the `content` property's ability to access custom data attributes! (This appears not yet supported for `::marker` in Safari)

If you need more style control, you may still want to use an alternate method. Review my tutorial on creating [totally custom list styles](https://moderncss.dev/totally-custom-list-styles/).

In 55 smol lines of CSS, we've created a set of reasonable document styles that is *just enough* to produce a responsive, easily readable document given the use of semantic HTML. Thanks to `flexbox`, `viewport units`, and `clamp`, it's flexible for variable document lengths. The newly supported `:is()` deserves the most credit in terms of reducing lines of code.

While lines of code (short or long) certainly doesn't automatically mean "quality", this demo shows that for a simple project you may not need a framework when a little dash of carefully applied CSS will do!

In fact - it's a great starting point to expand from to use the other smol techniques 😉

> This particular snippet is for an entire webpage so consequently the demo is not available for direct preview. Select "Open in Codepen" to check out the following styles in context!
> 

**Little rusty on your selectors and combinators**? Check out my two-part guide to advanced CSS selectors, [starting with part one](https://moderncss.dev/guide-to-advanced-css-selectors-part-one/). These styles are used and very slightly expanded (~120 lines) in my [Smol 11ty Starter](https://smol-11ty-starter.netlify.app/).

The `:visited` pseudo class is very unique because of [the potential to be exploited in terms of user's privacy](https://developer.mozilla.org/en-US/docs/Web/CSS/Privacy_and_the_:visited_selector). To resolve this, browser makers have limited which CSS styles are allowed to be applied using `:visited`.

A key gotcha is that styles applied via `:visited` will always use the parent's alpha channel - meaning, you cannot use `rgba` to go from invisible to visible, you must change the whole color value. So, to hide the initial state, you need to be able to use a solid color, such as the page or elements's background color.

As usual - this demo has bonus techniques and properties! Note the way we're updating the *order* of the visited indicator using flexbox. And, we're using some newly supported properties to change the color, position, and style of the link underline.

Plus, we're using `fit-content` again but as a value of `width` this time and not as a function. This means it will expand to the equivalent of `max-width` but not *exceed* the available width, preventing overflow.

Una Kravets has a much more [in-depth reference on styling `:visited`](https://una.im/hacking-visited/). For another example, see how I've styled it for the [Style Stage directory](https://stylestage.dev/styles/).

[CSS is awesome](https://css-tricks.com/css-is-in-fact-awesome/), and using a mix of older and modern CSS we can quickly define flexible, unbreakable boxes!

This demo of a `blockquote` first reuses our [responsive padding](https://smolcss.dev/) idea to enable padding that *just feels right* as the box flexes to different sizes. The box size is controlled by setting width using the `min()` function. As the box grows and shrinks, `min()` will select the *minimum* of the provided values, resulting in a box that has a `max-width` for large viewports *and* a `max-width` on smaller viewports.

Then we add a few properties to ensure long text values cannot break the box, including `word-break` and `hyphens` (note that `[hyphens](https://developer.mozilla.org/en-US/docs/Web/CSS/hyphens#browser_compatibility)` may not work in all languages).

Finally, the `footer` sets its width with `fit-content` just as we also used in the previous [visited styles demo](https://smolcss.dev/). This makes for a great alternative to swapping to an `inline` display value in case you also need to set a `display`!

> Topping candy canes ice cream gummi bears gingerbread marshmallow. Chocolate cake powder sugar plum topping. Cake marshmallow carrot cake. Pie liquorice liquorice sweet tootsie roll caramels donut dragée bear claw. Chocolate powder candy canes.
> 

For more extensive info and another example for creating flexible, unbreakable boxes, check out this ModernCSS tutorial - [Developing For Imperfect: Future Proofing CSS Styles](https://moderncss.dev/developing-for-imperfect-future-proofing-css-styles/)

Focus styles are incredibly important for the accessibility of your application. But, it can be difficult to manage them across changing contexts.

The following solution takes advantage of custom properites and `:is()` to set reasonable defaults for interactive elements. Then, individual instances can override each setting by simply providing an alternate value for the custom property.

This solution sets `currentColor` as the `outline-color` which works in many contexts. One that it might not is for buttons, in which case you could update `--outline-color` to use the same color as the button background, for example.

Additionally, this demonstrates one of the newly available CSS pseudo-class selectors: `focus-visible`. This selector is intended to only display focus styles when the browser detects that they should be visible (you may encounter the term "heuristics"). For now, we've setup some fallbacks so that a focus style is presented even when a browser doesn't support `:focus-visible` quite yet.

**Note**: Due to using `:focus-visible`, you may not see focus styles on the links and buttons unless you tab to them.

> Make sure your focus styles have appropriate contrast! If you're working on buttons, generate an accessible color palette with ButtonBuddy
> 

Learn more about `:focus-visible` in my Smashing [article on newly supported CSS pseudo-class selectors](https://www.smashingmagazine.com/2021/04/guide-supported-modern-css-pseudo-class-selectors/). You can also find more [tips on how CSS impacts accessibility](https://moderncss.dev/modern-css-upgrades-to-improve-accessibility/) on ModernCSS.