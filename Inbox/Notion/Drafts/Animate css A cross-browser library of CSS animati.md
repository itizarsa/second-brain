# Animate.css | A cross-browser library of CSS animations.

Source: Website
Status: Unprocessed
URL: https://animate.style/

![https://animate.style/img/animatecss-opengraph.jpg](https://animate.style/img/animatecss-opengraph.jpg)

---

> Animate.css v4 brought some breaking changes, please refer to the migration guide before updating from v3.x and under.
> 

**Animate.css** is a library of ready-to-use, cross-browser animations for use in your web projects. Great for emphasis, home pages, sliders, and attention-guiding hints.

## Installation and usage

### Installing

Install with npm:

```
$ npm install animate.css --save

```

Or install with Yarn (this will only work with appropriate tooling like Webpack, Parcel, etc. If you are not using any tool for packing or bundling your code, you can simply use the CDN method below):

```
$ yarn add animate.css

```

Import it into your file:

Or add it directly to your webpage using a CDN:

```
<head>
  <link
    rel="stylesheet"
    href="https://cdnjs.cloudflare.com/ajax/libs/animate.css/4.1.1/animate.min.css"
  />
</head>

```

### Basic usage

After installing Animate.css, add the class `animate__animated` to an element, along with any of the [animation names](https://animate.style/) (don't forget the `animate__` prefix!):

```
<h1 class="animate__animated animate__bounce">An animated element</h1>

```

That's it! You've got a CSS animated element. Super!

> Animations can improve the UX of an interface, but keep in mind that they can also get in the way of your users! Please read the best practices and gotchas sections to bring your web-things to life in the best way possible.
> 

### Using `@keyframes`

Even though the library provides you a few helper classes like the `animated` class to get you up running quickly, you can directly use the provided animations `keyframes`. This provides a flexible way to use Animate.css with your current projects without having to refactor your HTML code.

Example:

```
.my-element {
  display: inline-block;
  margin: 0 0.5rem;

  animation: bounce; /* referring directly to the animation's @keyframe declaration */
  animation-duration: 2s; /* don't forget to set a duration! */
}

```

Be aware that some animations are dependent on the `animation-timing` property set on the animation's class. Changing or not declaring it might lead to unexpected results.

### CSS Custom Properties (CSS Variables)

Since version 4, Animate.css uses custom properties (also known as CSS variables) to define the animation's duration, delay, and iterations. This makes Animate.css very flexible and customizable. Need to change an animation duration? Just set a new value globally or locally.

Example:

```
/* This only changes this particular animation duration */
.animate__animated.animate__bounce {
  --animate-duration: 2s;
}

/* This changes all the animations globally */
:root {
  --animate-duration: 800ms;
  --animate-delay: 0.9s;
}

```

Custom properties also make it easy to change all your animation's time-constrained properties on the fly. It means that you can have a slow-motion or time-lapse effect with a javascript one-liner:

```
// All animations will take twice the time to accomplish
document.documentElement.style.setProperty('--animate-duration', '2s');

// All animations will take half the time to accomplish
document.documentElement.style.setProperty('--animate-duration', '.5s');

```

Even though some aging browsers do not support custom properties, Animate.css provides a proper fallback, widening its support for any browser that supports CSS animations.

## Utility classes

Animate.css comes packed with a few utility classes to simplify its use.

### Delay classes

You can add delays directly on the element's class attribute, just like this:

```
<div class="animate__animated animate__bounce animate__delay-2s">Example</div>

```

Animate.css provides the following delays:

[Untitled](Animate%20css%20A%20cross-browser%20library%20of%20CSS%20animati%20ec8c8e57b00e4ef6b8a8efd644a2051f/Untitled%20Database%2013384ccbddb249f189c61182268c8488.csv)

The provided delays are from 1 to 5 seconds. You can customize them setting the `--animate-delay` property to a longer or a shorter duration:

```
/* All delay classes will take 2x longer to start */
:root {
  --animate-delay: 2s;
}

/* All delay classes will take half the time to start */
:root {
  --animate-delay: 0.5s;
}

```

### Slow, slower, fast, and Faster classes

You can control the speed of the animation by adding these classes, as below:

```
<div class="animate__animated animate__bounce animate__faster">Example</div>

```

The `animate__animated` class has a default speed of `1s`. You can also customize the animations duration through the `--animate-duration` property, globally or locally. This will affect both the animations and the utility classes. Example:

```
/* All animations will take twice as long to finish */
:root {
  --animate-duration: 2s;
}

/* Only this element will take half the time to finish */
.my-element {
  --animate-duration: 0.5s;
}

```

Notice that some animations have a duration of less than 1 second. As we used the CSS `calc()` function, setting the duration through the `--animation-duration` property will respect these ratios. So, when you change the global duration, all the animations will respond to that change!

### Repeating classes

You can control the iteration count of the animation by adding these classes, like below:

```
<div class="animate__animated animate__bounce animate__repeat-2">Example</div>

```

[Untitled](Animate%20css%20A%20cross-browser%20library%20of%20CSS%20animati%20ec8c8e57b00e4ef6b8a8efd644a2051f/Untitled%20Database%20c2ba036b8b894ed9abdbe6aefd7932d8.csv)

As with the delay and speed classes, the `animate__repeat` class is based on the `--animate-repeat` property and has a default iteration count of `1`. You can customize them by setting the `--animate-repeat` property to a longer or a shorter value:

```
/* The element will repeat the animation 2x
   It's better to set this property locally and not globally or
   you might end up with a messy situation */
.my-element {
  --animate-repeat: 2;
}

```

Notice that `animate__infinite` doesn't use any custom property, and changes to `--animate-repeat` will have no effect. Don't forget to read the [best practices](https://animate.style/) section to make the best use of repeating animations.

## Best practices

Animations can greatly improve an interface's UX, but it's important to follow some guidelines to not overdo it and deteriorate the user experience on your web-things. Following the following rules should provide a good start.

### Meaningful animations

You should avoid animating an element just for the sake of it. Keep in mind that animations should make an intention clear. Animations like attention seekers (bounce, flash, pulse, etc) should be used to bring the user's attention to something special in your interface and not only as a way to bring "flashiness" to it.

Entrances and exit animations should be used to orientate what is happening in the interface, clearly signaling that it's transitioning into a new state.

It doesn't mean that you should avoid adding playfulness to the interface, just be sure that the animations are not getting in the way of your user and that the page's performance is not affected by an exaggerated use of animations.

### Don't animate large elements

Avoid it as it won't bring much value to the user and will probably only cause confusion. Besides that, there is a good chance that the animations will be junky, culminating in bad UX.

### Don't animate root elements

Animating the `<html/>` or `<body/>` tags is possible, but you should avoid it. There were some reports pointing out that this could trigger some weird browser bugs. Besides, making the whole page bounce would hardly provide good value to your UX. If you indeed need this sort of effect, wrap your page in an element and animate it, like this:

```
<body>
  <main class="animate__animated animate__fadeInLeft">
    <!-- Your code -->
  </main>
</body>

```

### Infinite animations should be avoided

Even though Animate.css provides utility classes for repeating animations, including an infinite one, you should avoid endless animations. It will just distract your users and might annoy a good slice of them. So, use it wisely!

### Mind the initial and final state of your elements

All the Animate.css animations include a CSS property called `animation-fill-mode`, which controls the states of an element before and after animation. You can read more about it [here](https://developer.mozilla.org/en-US/docs/Web/CSS/animation-fill-mode). Animate.css defaults to `animation-fill-mode: both`, but you can change it to suit your needs.

### Don't disable the `prefers-reduced-motion` media query

Since version 3.7.0 Animate.css supports the `prefers-reduced-motion` media query which disables animations based on the OS system's preference on supporting browsers (most current browsers support it). This is a **critical accessibility feature** and should never be disabled! This is built into browsers to help people with vestibular and seizure disorders. You can read more about it [here](https://css-tricks.com/revisiting-prefers-reduced-motion-the-reduced-motion-media-query/). If your web-thing needs the animations to function, warn users, but don't disable the feature. You can do it easily with CSS only. Here's a simple example:

## Gotchas

### You can't animate inline elements

Even though some browsers can animate inline elements, this goes against the CSS animation specs and will break on some browsers or eventually cease to work. Always animate block or inline-block level elements (grid and flex containers and children are block-level elements too). You can set an element to `display: inline-block` when animating an inline-level element.

### Overflow

Most of the Animate.css animations will move elements across the screen and might create scrollbars on your web-thing. This is manageable using the `overflow: hidden` property. There's no recipe to when and where to use it, but the basic idea is to use it in the parent holding the animated element. It's up to you to figure out when and how to use it, [this guide](https://developer.mozilla.org/en-US/docs/Web/CSS/overflow) can help you understand it.

### Intervals between repeats

Unfortunately, this isn't possible with pure CSS right now. You have to use Javascript to achieve this result.

## Usage with Javascript

You can do a whole bunch of other stuff with animate.css when you combine it with Javascript. A simple example:

```
const element = document.querySelector('.my-element');
element.classList.add('animate__animated', 'animate__bounceOutLeft');

```

You can detect when an animation ends:

```
const element = document.querySelector('.my-element');
element.classList.add('animate__animated', 'animate__bounceOutLeft');

element.addEventListener('animationend', () => {
  // do something
});

```

or change its duration:

```
const element = document.querySelector('.my-element');
element.style.setProperty('--animate-duration', '0.5s');

```

You can also use a simple function to add the animations classes and remove them automatically:

```
const animateCSS = (element, animation, prefix = 'animate__') =>
  // We create a Promise and return it
  new Promise((resolve, reject) => {
    const animationName = `${prefix}${animation}`;
    const node = document.querySelector(element);

    node.classList.add(`${prefix}animated`, animationName);

    // When the animation ends, we clean the classes and resolve the Promise
    function handleAnimationEnd(event) {
      event.stopPropagation();
      node.classList.remove(`${prefix}animated`, animationName);
      resolve('Animation ended');
    }

    node.addEventListener('animationend', handleAnimationEnd, {once: true});
  });

```

And use it like this:

```
animateCSS('.my-element', 'bounce');

// or
animateCSS('.my-element', 'bounce').then((message) => {
  // Do something after the animation
});

```

If you had a hard time understanding the previous function, have a look at [const](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/const), [classList](https://developer.mozilla.org/en-US/docs/Web/API/Element/classList), [arrow functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions), and [Promises](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise).

## Migration from v3.x and under

Animate.css v4 brought some improvements, improved animations, and new animations, which makes it worth upgrading. However, it also comes with a breaking change: we have added a prefix for all of the Animate.css classes - defaulting to `animate__` - so a direct migration is impossible.

But fear not! Although the default build, `animate.min.css`, brings the `animate__` prefix we also provide the `animate.compat.css` file which brings no prefix at all, like the previous versions (3.x and under).

If you're using a bundler, update your import:

from:

```
import 'animate.min.css';

```

to

```
import 'animate.compat.css';

```

Notice that depending on your project's configuration, this might change a bit.

In case of using a CDN, update the link in your HTML:

from:

```
<head>
  <link
    rel="stylesheet"
    href="https://cdnjs.cloudflare.com/ajax/libs/animate.css/3.7.2/animate.min.css"
  />
</head>

```

to

```
<head>
  <link
    rel="stylesheet"
    href="https://cdnjs.cloudflare.com/ajax/libs/animate.css/4.0.0/animate.compat.css"
  />
</head>

```

In the case of a new project, it's highly recommended to use the default prefixed version as it'll make sure that you'll hardly have classes conflicting with your project. Besides, in later versions, we might decide to discontinue the `animate.compat.css` file.

## Custom Builds

Animate.css is powered by npm, postcss + postcss-preset-env, which means you can create custom builds pretty easily, using future CSS today.

First of all, you’ll need Node and all other dependencies:

```
$ cd path/to/animate.css/
$ npm install

```

Next, run `npm start` to compile your custom build. Three files will be generated:

- `animate.css`: raw build, easy to read and without any optimization
- `animate.min.css`: minified build ready for production
- `animate.compat.css`: minified build ready for production **without class prefix**. This should only be used as an easy path for migrations.

For example, if you'll only use some of the “attention seekers” animations, simply edit the `./source/animate.css` file, delete every `@import` and the ones you want to use.

```
@import 'attention_seekers/bounce.css';
@import 'attention_seekers/flash.css';
@import 'attention_seekers/pulse.css';
@import 'attention_seekers/rubberBand.css';
@import 'attention_seekers/shake.css';
@import 'attention_seekers/headShake.css';
@import 'attention_seekers/swing.css';
@import 'attention_seekers/tada.css';
@import 'attention_seekers/wobble.css';
@import 'attention_seekers/jello.css';
@import 'attention_seekers/heartBeat.css';

```

Now, just run `npm start` and your highly optimized build will be generated at the root of the project.

### Changing the default prefix

It's pretty straight forward to change animate's prefix on your custom build. Change the `animateConfig`'s `prefix` property in the `package.json` file and rebuild the library with `npm start`:

```
/* on Animate.css package.json */
"animateConfig": {
  "prefix": "myCustomPrefix__"
},

```

then:

```
$ npm start

```

Easy peasy!

## Accessibility

Animate.css supports the `[prefers-reduced-motion` media query](https://webkit.org/blog/7551/responsive-design-for-motion/) so that users with motion sensitivity can opt out of animations. On supported platforms (currently all the major browsers and OS, including mobile), users can select "reduce motion" on their operating system preferences, and it will turn off CSS transitions for them without any further work required.

## Core team

[Animate%20css%20A%20cross-browser%20library%20of%20CSS%20animati%20ec8c8e57b00e4ef6b8a8efd644a2051f/15052701](Animate%20css%20A%20cross-browser%20library%20of%20CSS%20animati%20ec8c8e57b00e4ef6b8a8efd644a2051f/15052701)

## License and Contributing

Animate.css is licensed under the MIT license. ([https://opensource.org/licenses/MIT](https://opensource.org/licenses/MIT))

### Contributing

Pull requests are the way to go here. We only have two rules for submitting a pull request: match the naming convention (camelCase, categorized [fades, bounces, etc.]) and let us see a demo of submitted animations in a [pen](https://codepen.io/). That **last one is important**.

### Code of Conduct

This project and everyone participating in it is governed by the [Contributor Covenant Code of Conduct](https://github.com/animate-css/animate.css/blob/main/CODE_OF_CONDUCT.md). By participating, you are expected to uphold this code. Please report unacceptable behavior to [animate@eltonmesquita.com](mailto:animate@eltonmesquita.com).