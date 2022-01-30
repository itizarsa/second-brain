# A Guide to CSS Animation - Part 1 - DEV Community

Source: Article
Status: Unprocessed
URL: https://dev.to/jh3y/a-guide-to-css-animation-part-1-36o9

![https://res.cloudinary.com/practicaldev/image/fetch/s--COtAjcKM--/c_imagga_scale,f_auto,fl_progressive,h_500,q_auto,w_1000/https://thepracticaldev.s3.amazonaws.com/i/dxbsihqs2oylyygdxtbw.png](https://res.cloudinary.com/practicaldev/image/fetch/s--COtAjcKM--/c_imagga_scale,f_auto,fl_progressive,h_500,q_auto,w_1000/https://thepracticaldev.s3.amazonaws.com/i/dxbsihqs2oylyygdxtbw.png)

---

![A%20Guide%20to%20CSS%20Animation%20-%20Part%201%20-%20DEV%20Community%206d1a763dcdf949ddbc73e31d20cfc4f1/dxbsihqs2oylyygdxtbw.png](A%20Guide%20to%20CSS%20Animation%20-%20Part%201%20-%20DEV%20Community%206d1a763dcdf949ddbc73e31d20cfc4f1/dxbsihqs2oylyygdxtbw.png)

> Let's get things moving! 🎞
> 

Hey! 👋 So you’re interested in making things move on your websites and in your apps? This guide should help 👍

This post assumes you’ve never created a `CSS` animation before. But even if you have, there may be things you were not aware of. It does assume you have some familiarity with `HTML` and `CSS`. We’ll explore creating your first animation through to things like chaining animations.

![A%20Guide%20to%20CSS%20Animation%20-%20Part%201%20-%20DEV%20Community%206d1a763dcdf949ddbc73e31d20cfc4f1/ib20yjm5dzcvd8nkzqvt.gif](A%20Guide%20to%20CSS%20Animation%20-%20Part%201%20-%20DEV%20Community%206d1a763dcdf949ddbc73e31d20cfc4f1/ib20yjm5dzcvd8nkzqvt.gif)

CSS animation can be a quick concept to grasp but a big topic to cover once we really dig in. Therefore, this post is split over parts.

- Part 1: Introduces CSS animation looking at things like performance and how to inspect animations. We will also create a basic animation and look at `@keyframes` composition.
- [Part 2](https://dev.to/jh3y/a-guide-to-css-animation-part-2-2hjo): With the basics grasped, we dig into the different things we can do with the `animation` properties. This includes tips on things like using `fill-mode` and chaining animations.

![A%20Guide%20to%20CSS%20Animation%20-%20Part%201%20-%20DEV%20Community%206d1a763dcdf949ddbc73e31d20cfc4f1/5x1glkjlwud45768m1b4.png](A%20Guide%20to%20CSS%20Animation%20-%20Part%201%20-%20DEV%20Community%206d1a763dcdf949ddbc73e31d20cfc4f1/5x1glkjlwud45768m1b4.png)

- [Part 3](https://dev.to/jh3y/a-guide-to-css-animation-part-3-3g20): We wrap things up with some bonus topics like using CSS variables and hooking in from `JavaScript`. We also discuss whether we should even use CSS animation at all. That’s right, it’s not always the best option. But there’s a benefit to understanding the foundations and alternatives.

![A%20Guide%20to%20CSS%20Animation%20-%20Part%201%20-%20DEV%20Community%206d1a763dcdf949ddbc73e31d20cfc4f1/yhn46zgwfzm4z7ma9qy1.png](A%20Guide%20to%20CSS%20Animation%20-%20Part%201%20-%20DEV%20Community%206d1a763dcdf949ddbc73e31d20cfc4f1/yhn46zgwfzm4z7ma9qy1.png)

All the code is available in this CodePen collection 🤓

![A%20Guide%20to%20CSS%20Animation%20-%20Part%201%20-%20DEV%20Community%206d1a763dcdf949ddbc73e31d20cfc4f1/jqssaberzcdexpoqwzce.png](A%20Guide%20to%20CSS%20Animation%20-%20Part%201%20-%20DEV%20Community%206d1a763dcdf949ddbc73e31d20cfc4f1/jqssaberzcdexpoqwzce.png)

This means all the examples can be forked, downloaded, edited, etc. 👍

The code is also available on Github

![A%20Guide%20to%20CSS%20Animation%20-%20Part%201%20-%20DEV%20Community%206d1a763dcdf949ddbc73e31d20cfc4f1/g2szs1hogdfmgghl3dxo.png](A%20Guide%20to%20CSS%20Animation%20-%20Part%201%20-%20DEV%20Community%206d1a763dcdf949ddbc73e31d20cfc4f1/g2szs1hogdfmgghl3dxo.png)

For all animations, we are using a single `div` element unless stated otherwise. The basic markup comprises of something like the following;

```
<html>
  <head>
    <title>Our first animation</title>
    <style>
     * {
       box-sizing: border-box;
     }
     html, body {
       align-items: center;
       background-color: rebeccapurple;
       display: flex;
       justify-content: center;
       margin: 0;
       padding: 0;
     }
     div {
       background-color: #2EEC71;
       height: 100px;
       width: 100px;
     }
    </style>
    <link rel="stylesheet" href="./index.css" />
  </head>
  <body>
    <div />
  </body>
</html>

```

The goal of this guide is to make you comfortable with creating your own CSS animations from scratch! 💪

To improve usability and general user experience. But that does not mean animation should be everywhere in your sites. There are times and places.

![A%20Guide%20to%20CSS%20Animation%20-%20Part%201%20-%20DEV%20Community%206d1a763dcdf949ddbc73e31d20cfc4f1/6x6ame7kiwthajqayrk7.gif](A%20Guide%20to%20CSS%20Animation%20-%20Part%201%20-%20DEV%20Community%206d1a763dcdf949ddbc73e31d20cfc4f1/6x6ame7kiwthajqayrk7.gif)

With animation, we can do things such as draw a users' attention to something or direct them through a flow. Consider loading animations or page transition effects for example.

Before we start creating animations, we need to know which properties we can animate. We can’t animate every property. The following MDN article lists properties that we can animate.

Lea Verou also has a great demo page for animatable properties.

![A%20Guide%20to%20CSS%20Animation%20-%20Part%201%20-%20DEV%20Community%206d1a763dcdf949ddbc73e31d20cfc4f1/mcypemz6h5y6u3cdop8a.png](A%20Guide%20to%20CSS%20Animation%20-%20Part%201%20-%20DEV%20Community%206d1a763dcdf949ddbc73e31d20cfc4f1/mcypemz6h5y6u3cdop8a.png)

![A%20Guide%20to%20CSS%20Animation%20-%20Part%201%20-%20DEV%20Community%206d1a763dcdf949ddbc73e31d20cfc4f1/40hhcn6pjh48a1otyxcn.png](A%20Guide%20to%20CSS%20Animation%20-%20Part%201%20-%20DEV%20Community%206d1a763dcdf949ddbc73e31d20cfc4f1/40hhcn6pjh48a1otyxcn.png)

## Property performance

Out of the animatable properties, we may choose to animate some over others due to performance.

For example, animating an element's position will be better handled using `transform`. This is because the GPU can handle the heavy lifting when animating that property. Animating some properties will trigger layouts to take place 👎

The following article is great for understanding animation performance 👍

With all that out of the way, let’s get started 💪

Let’s dig right in and create our first animation ⛏

For this animation, we will make an element spin 360 degrees. Riveting stuff I know 😅 But we need to start somewhere!

First, we create our animation using the `@keyframes` rule. The `@keyframes` rule takes the following structure.

```
@keyframes [NAME] {
  [ KEYFRAME SELECTOR ] { CSS STYLES }
}

```

`animation-name` is the name we give to our animation. You can have one or many keyframe selectors 👍

We will name our animation `spin`. To spin our element we can use the `transform` property and `rotate` from `0deg` to `360deg`. We use two keyframe selectors. One to define the start of our animation(`from`) and one for the end of our animation(`to`). `from` and `to` keywords are equivalent to `0%` and `100%`.

```
@keyframes spin {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}

```

We can take this a little further. The styles under the `from` keyframe selector match the initial `transform` of our element. Therefore, the keyframe selector is redundant. We can remove it.

```
@keyframes spin {
  to {
    transform: rotate(360deg);
  }
}

```

Now, we need to apply that animation to our element. We use the `animation-name` and `animation-duration` properties 👍

Here we are telling our element to use the animation `spin` with a duration of 2 seconds. The duration can be set in either millisecond(`ms`) or seconds(`s`).

Loading that up in a browser should give us something like

Our first animation 🎉

From that first animation, we have enough to go off and start creating cool animations 😎 But stick around to get a full grasp of what else we can achieve 💪

We have created our first animation. Now seems like a great time to introduce the `Animations` inspector in `Google Chrome`.

Open up the animation in `Google Chrome` and open up the `Developer Tools`. Open up the `Animations` panel by going into `More Tools`. If the `Animations` panel says “Listening for animations…”, refresh the page.

After refreshing, we should see something in the `Animations` panel, that’s our animation!

Click the animation and we are able to inspect it. Now as our animation isn’t particularly complex, there isn’t much to inspect. But with the Animations Inspector, we can do various things. We can experiment with durations and delays as well as altering playback speed. Most importantly, we can replay our animations without having to refresh the entire page 😅

This becomes particularly useful when we have many animations. Whether it be for different elements or on one element.

Read more about the `Animations` inspector in the following article.

Throughout this guide, I recommend using the inspector when checking out the [demos](https://codepen.io/collection/nMpBQm/) 👍

We put together our first `@keyframes` rule in our `spin` animation.

There isn’t much to `@keyframes`. After specifying an animation name, we structure our animation within keyframe selectors. The keyframe selector specifies a percentage of the animation duration. Or, as mentioned before, we can use the `from` and `to` keywords that are equal to `0%` and `100%`.

Each selector defines styles that should apply at that point of the animation. If we have selectors that specify the same CSS styles, we can group them together.

Let’s start with a basic example. Consider the animation of an element moving around the path of a square.

We will call our animation `squarePath`, very creative I know 😅

For this example, there will be four positions for our element. For every side of the square, we use a quarter of the animation. Because our start and finish position will be the same, we can group those keyframe selectors 👍

Apply the `animation-name` and `animation-duration` to our element 🎉

And that’s it! We have an element moving along the path of a square 🎉

We’ve taken a look at the basics of creating and applying animations to our elements. We can also inspect our animations and tweak them in the browser 💪

Although that will be enough to get up and running with CSS animation, there’s a lot more to it! I hope you’ll join me in [Part 2](https://medium.com/@jh3y/a-guide-to-css-animation-part-2-2cd422f78567) where we dig deeper into applying animations and the associated tips and tricks.

Remember, all the code is available in the following CodePen collection 👍

As always, any questions or suggestions, please feel free to leave a response or [tweet me 🐦](https://twitter.com/@jh3yy)! Be sure to connect with me on the socials! 😎