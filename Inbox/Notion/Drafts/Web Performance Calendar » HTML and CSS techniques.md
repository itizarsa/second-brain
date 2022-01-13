# Web Performance Calendar » HTML and CSS techniques to reduce your JavaScript

Source: Article
Status: Unprocessed
URL: https://calendar.perfplanet.com/2020/html-and-css-techniques-to-reduce-your-javascript/

![https://calendar.perfplanet.com/wp-content/uploads/2020/12/catz.png](https://calendar.perfplanet.com/wp-content/uploads/2020/12/catz.png)

---

![Web%20Performance%20Calendar%20%C2%BB%20HTML%20and%20CSS%20techniques%2046af358280df45369c2fc0b5efb59899/anthonyr.jpg](Web%20Performance%20Calendar%20%C2%BB%20HTML%20and%20CSS%20techniques%2046af358280df45369c2fc0b5efb59899/anthonyr.jpg)

[Anthony Ricaud](https://ricaud.me/)

([@anthony_ricaud](https://twitter.com/anthony_ricaud)) is a web engineer helping teams ship efficient products at a sustainable pace. With a broad understanding of web protocols and browsers, he likes to design simple but fast web architectures.

More and more websites are relying on JavaScript for the interactions they provide. It enables pleasant experiences but also comes with undesirable effects:

- Longer page load times
- Page is unusable until the JavaScript loads and if it does so without any errors
- Usability, reactivity and accessibility can be lacking without a team with the means and resources to pay attention to those.

Given these drawbacks, relying on solutions provided natively by browsers enables you to benefit at low cost from the expertise of the community creating web standards. These solutions generally have the advantage of using less code, thus reducing maintenance efforts for a development team (for example, no need to update the libraries used).

In this article, we will explore some of these native solutions that are available to the majority of your users. We will see some examples but we won’t go into all the subtleties, because other resources do so very well. Rather, the goal is to inform you of the existence of these techniques.

## Rendering blocked by JavaScript

Before going through each technique, a quick reminder about a big drawback of using JavaScript: a browser only has one thread to control the rendering of your page. When JavaScript runs, the browser delays user interaction events and interface updates. This can be very annoying because you get the impression that the page does not respond to your actions or that the animations are janky. Philip Walton [details this problem and includes a demo](https://philipwalton.com/articles/why-web-developers-need-to-care-about-interactivity/).

Development teams tend to work with powerful devices on a daily basis. This often hides the negative effects of our JavaScript. Don’t forget to test regularly on more limited devices.

(It is possible to run JavaScript in another thread through Web Workers but it is rarely useful for interface code.)

## Clamping the number of lines displayed

### JavaScript version

Here are two ways to do this in JavaScript :

1. Limit the number of characters displayed. This is very fragile because, except for monospace fonts, the width of the characters is variable. You may end up with more lines than you want or with text truncated too early.
2. Truncate the content of the element by trial and error until the element occupies the desired number of lines. This is very expensive because each time you try, you have to ask the browser to render to see if you get the desired size. And this technique can only be accurate if it is used after rendering with the desired fonts, which can result in large layout shifts.

In a page containing a lot of text to truncate, this delays the correct display. In addition, these two solutions completely truncate the text, which can have consequences on search engines or the restitution by assistive technologies. The font size or the width of the element can also change during the lifetime of the page (voluntarily by the user, involuntarily by changing the orientation of the device). Taking all these cases into account is quite annoying.

### Native version

- `[webkit-line-clamp](https://developer.mozilla.org/en/docs/Web/CSS/-webkit-line-clamp)` is a CSS property to do this natively. Introduced ten years ago in Safari, this property has been used so widely that other browsers have also adopted it for compatibility reasons and [it has become standard](https://www.w3.org/TR/css-overflow-3/#webkit-line-clamp). (Yes, with the prefix.) You need a few other prefixed properties to achieve the desired behaviour. It is a bit irritating to have to use prefixed properties but the prefix has been detailed in standards so we’re not taking any risk.

Except Internet Explorer and Firefox before version 68, all browsers support this property. The following example illustrates it with as a fallback solution.

This solution has no performance or annoying content shifts issues and does not impact search engines or assistive technologies. However, [it does not work for items with multiple children](https://codepen.io/jimratliff/pen/BaBzzbq).

## Keep an element on screen when it matters

You may want to keep a header, a toolbar or a shopping cart visible for a section of the page. I often encounter this kind of behaviour but it rarely has the correct implementation.

### JavaScript version

Historically, to do this, it was necessary to listen to scrolling events that fire very often. So often that most solutions discarded most of the events with throttling or debouncing techniques. Nowadays, we can use `[IntersectionObserver](https://developer.mozilla.org/en/docs/Web/API/Intersection_Observer_API)` to only receive events when the element enters or leaves the viewport. That’s way more efficient.

Once we’ve detected the element entering or leaving the viewport, we need to switch from `position: relative` to `position: fixed`. This requires the browser to recompute the size and position of a lot of elements (what we refer to as layout or reflow) which is expensive. And it is important to make sure that the surrounding elements do not move around and cause a jump in content. “Le Monde suffers from such an imperfect implementation.

If the rendering is blocked when the element enters or exits the viewport (which is very likely with the current trend of having animations coordinated with scrolling), the switchover will take place much later.

### Native version

CSS now has `[position: sticky](https://developer.mozilla.org/en/docs/Web/CSS/position)` to achieve this behaviour. No performance, responsiveness or content jump issues: as long as the browser can scroll, it will keep the item positioned exactly where you declared it. To choose its positioning, use `top`, `bottom`, `left` or `right`.

All browsers except Internet Explorer and older versions of Chrome or Firefox support sticky. For these older browsers, the elements are in `position: static`, which is the default value and will not take into account the values of `top`, `bottom`, `left` and `right`. Keep this in mind if you need to support these browsers. Older versions of Safari require the `-webkit-sticky` prefix.

However, there is one limitation: it is impossible to change the appearance of an element whether it is stuck or not, say with a pseudo-class `:stuck`. [This is a general limitation of CSS](https://wiki.csswg.org/faq#selectors-that-depend-on-layout). In this case, I recommend combining the benefits of `position: sticky` to keep the element sticking with `IntersectionObserver`to change its appearance (while taking care not to change its dimensions, to prevent content jumps).

## Smooth scrolling

### JavaScript version

To implement this in JavaScript, you need to regularly execute JavaScript that will change the scroll position. For the animation to run smoothly, no other JavaScript should block the rendering during the whole animation.

You will also need to choose a timing function. To look natural, it may need to be different for each operating system to suit its conventions.

### Native version

Thanks to `[scroll-behavior: smooth](https://developer.mozilla.org/en/docs/Web/CSS/scroll-behavior)` in CSS and `{behavior: 'smooth'}` as an option to `[scroll](https://developer.mozilla.org/en/docs/Web/API/Element/scroll)`, `[scrollTo](https://developer.mozilla.org/en/docs/Web/API/Element/scrollTo)` and `[scrollIntoView](https://developer.mozilla.org/en/docs/Web/API/Element/scrollIntoView)` in JavaScript, you delegate all the timing functions decisions. This gives you a behaviour more in line with the device used.

Safari doesn’t support this yet (unless you enable a hidden preference) but most of the time, it’s not a big deal: it’s a classic example of [progressive enhancement](https://developer.mozilla.org/en-US/docs/Glossary/Progressive_Enhancement).

With both the JavaScript version and the native version, there are two accessibility aspects to pay attention to: respect [the preference to minise animations and movements](https://developer.mozilla.org/en/docs/Web/CSS/@media/prefers-reduced-motion) and [make sure the focus is moved appropriately](https://css-tricks.com/smooth-scrolling-accessibility/).

## Scrolling with snap points

This lets you create slide shows, horizontal lists that snap to each item or sections that take up the all viewport.

### JavaScript version

To create a slide show, we listen to:

- pressure events (`mousedown`, `mouseup`, `touchstart`, `touchend`, `pointerdown` or `pointerup`) ;
- movement events (`mousemove`, `touchmove` or `pointermove`).

Handling this well for all types of pointers (mouse or finger) and when the pointer leaves the area is quite tricky. Once these events are properly handled, we move the elements according to the movement. Each move may trigger a costly reflow, creating jank and breaking the illusion for the user.

For sections taking up all the viewport or horizontal lists, we must listen to all scrolling events, cancel them and replace them with the scroll moves we want. Getting a pleasant behaviour is very difficult: we’ve all screamed at our screens when we come across a site that hijacks native scrolling.

For both those use cases, you will need to decide when to move on to the next item based on the speed and distance of the original move. If your choices do not match the system behaviour, you will confuse your users.

### Native version

CSS has [scroll snap](https://developer.mozilla.org/en/docs/Web/CSS/CSS_Scroll_Snap) to handle this. On the scrolling container, we define `[scroll-snap-type](https://developer.mozilla.org/en/docs/Web/CSS/scroll-snap-type)` to indicate the direction we want snaps to happen and whether they are mandatory or only when in proximity of a snap point. Then on the container’s children, we will define `[scroll-snap-align](https://developer.mozilla.org/en/docs/Web/CSS/scroll-snap-align)` to indicate snap points.

The following demo works entirely without JavaScript. It also uses `scroll-behavior` to hint that the user can use the regular scrolling mechanisms.

By ticking the checkbox, you’ll activate a tiny bit of `IntersectionObserver` to highlight the thumbnail of the currently visible image.

All modern browsers support this behaviour. There was [an alternate syntax](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Scroll_Snap/Browser_compat) but I advise against using it. It will only increase the testing scenarios and you can rely on graceful degradation. In browsers without support, it will be a regular scroll.

As this feature uses the browser’s scrolling, we get incredible fluidity compared to JavaScript solutions, regardless of the type of pointer used. And if you are trying to improve your [First Input Delay](https://web.dev/fid/), scrolling does not count as an input so this interaction will not be the first input.

## Lazy-loading images

### JavaScript version

To achieve this with JavaScript, we generally use a syntax such as `<img data-src="…" data-srcset="…" alt="…">`. When the images get close to the viewport, the JavaScript will change the attributes to fetch and display them.

The main drawback of this technique is that those images are not visible until the associated JavaScript kicks in. [And it happens more than you think](https://kryogenix.org/code/browser/everyonehasjs.html). Search engines will also have more difficulty finding your images since they don’t really exist and the bots can’t scroll.

Choosing when to trigger the download is quite subtle. How far away from the viewport should you trigger it based on the available bandwidth? Should you take the scrolling speed into account?

### Native version

In the last year, all browsers but Safari have implemented the attribute `[loading="lazy"](https://developer.mozilla.org/en/docs/Web/HTML/Element/img#attr-loading)` on `<img>` elements. If your website currently loads all images, you can add this attribute. You’ll get a lighter website for most of the visits with little effort on your part.

If you already use a lazy-loading solution, until Safari supports this attribute, you’ll have to make a decision based on your specifics. Is it worth loading all images in Safari for a streamlined code?

Right now, the rules to trigger a download are specific to each browser and may not be ideal. One thing is certain though, the heuristics will get better over time and you won’t have to change a line of code!

I did not prepare a demo for this as it’s a bit invisible but you can go read [Google’s explanation about it](https://web.dev/browser-level-image-lazy-loading/).

## Production examples

If you’d like to see those examples in the wild, I’ve used all those techniques in my previous project (the website is in French though):

- on [search results](https://i-make.com/fr/search/?q=kit+cr%C3%A9atif) (truncated titles and lazy loaded images)
- on [product detail pages](https://i-make.com/fr/catalogue/p/beautymix-le-robot-de-cosmetique-maison-26/) (lazy loaded images, smooth scrolling and scroll snap for the image gallery)
- and on the [basket](https://i-make.com/fr/basket/) (if you have products in your basket the order button is sticky). I invite you to successively test with a narrow and wide viewport.

## Conclusion

I hope this little overview inspires you to update the websites you maintain. Next time you’re looking for a JavaScript library for a certain behaviour, remember these few techniques. Also ask yourself if there might be other HTML or CSS techniques I have not covered (maybe `<details>` with `<summary>` or `<datalist>`). Browsers are constantly improving, you might be pleasantly surprised. And your users will rejoice!