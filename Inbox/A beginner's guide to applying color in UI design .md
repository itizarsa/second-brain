# A beginner's guide to applying color in UI design - DEV Community

Source: Article
Status: Unprocessed
URL: https://dev.to/georgedoescode/a-beginner-s-guide-to-applying-color-in-ui-design-3904

![https://res.cloudinary.com/practicaldev/image/fetch/s--e13xmkyr--/c_imagga_scale,f_auto,fl_progressive,h_500,q_auto,w_1000/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/byvsm2g1tfsf7vr832zq.png](https://res.cloudinary.com/practicaldev/image/fetch/s--e13xmkyr--/c_imagga_scale,f_auto,fl_progressive,h_500,q_auto,w_1000/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/byvsm2g1tfsf7vr832zq.png)

---

![A%20beginner's%20guide%20to%20applying%20color%20in%20UI%20design%20%207d1cd3e133894fedbd0b12ac75e43e97/byvsm2g1tfsf7vr832zq.png](A%20beginner's%20guide%20to%20applying%20color%20in%20UI%20design%20%207d1cd3e133894fedbd0b12ac75e43e97/byvsm2g1tfsf7vr832zq.png)

Is color theory getting you down? Are you tired of the same old preset palettes? Sick of hitting “regenerate” on a magical color palette creator?

Don't worry, we've all been there...

This post hopes to be your virtual guide up the mystical mountain of color. By the time you reach the top, you will have all the skills you need to create beautiful, coherent palettes.

Sound OK? Let's set off for basecamp.

## Prerequisites

To make the most out of this tutorial, you should be comfortable working with both HTML and CSS.

## The format of this tutorial

This tutorial is all about learning by doing. We will be starting with the same base design and adding our own individual style.

The base design itself is a *“product card”*, the likes of which you will likely have come across on a variety of e-commerce sites. It is a simple example but provides an excellent blank canvas to experiment with color.

I have created a [CodePen](https://codepen.io/georgedoescode/pen/xxRrdJp) that you can [fork](https://blog.codepen.io/documentation/forks/#:~:text=To%20fork%20a%20Pen%20or,ready%20to%20save%20your%20changes.) to get started.

Here it is:

Right now, the colors are either black or white. There is no product image and the design has little personality. It's very basic, but that's OK. This is where you come in!

## **Choosing** ***your*** **product**

First things first, you should choose an image to replace the question mark. This could be anything — a chocolate bar, a pair of shoes, a tractor, a cool hat... It's up to you.

I encourage everyone to choose their *own* individual product image, though. Why?

Different products will suit different aesthetics and thus different color palettes. You may choose to add vibrant, bright colors for a candy bar or subdued, calming colors for a yoga mat. By choosing your own aesthetic and palette, you can better learn how to **apply** the techniques to your own work.

The starter CodePen comes with [Twemoji](https://twemoji.twitter.com/) built in to make choosing a product image as easy as possible. If you change the emoji in `card__img`, Twemoji will replace it with a high-res SVG version.

```
<div class="card__img" role="img">❓</div>

```

***Tip:** on macOS, you can open an emoji keyboard with `ctrl + cmd + space`. On Windows, you can open one with `windows/start + .`*

I'm going to choose the “herbs” emoji for my product card. I'm also going to change the card title and meta description to match my choice.

My product card now looks something like this:

You should have something similar, but with your own product image/emoji and text content. Nice work! Let's move on up the color mountain.

## **Working with HSL**

When working with color, I always reach for HSL. To me, it is the most intuitive way of representing colors in the browser. We will be using HSL throughout this tutorial, too, so here's a quick primer...

HSL stands for **hue, saturation, lightness**.

**Hue** is the angle of rotation *(in degrees)* on a color wheel for a particular color. In the browser, red sits at 0 degrees. Here's an example:

**Saturation** is how “intense” a color is. A lower saturation will appear more grey, a higher saturation more vibrant:

**Lightness** is how close to black or white the color is. A value of 0% lightness will always appear black, a value of 100% will always appear white:

We write HSL colors in CSS like this:

```
p {
  /* hue, saturation(%), lightness(%) */
  color: hsl(0, 100%, 50%);
}

```

If this is all new to you, don't worry! It can take a little while to get used to HSL, but I promise it is worth it.

If you feel like you need some practice, spend a little time experimenting. You can do this in a graphics editor such as Figma or Sketch, or right in the browser. Whatever fits with your workflow.

## Designing in grayscale

My personal preference when creating a design is to always start with shades of gray. By holding the color until the end, we can focus on our typography, spacing, and content.

You may notice in the starter CodePen that there are only two colors, black and white. This isn't quite enough to design with, so we need to add some more. Let's not start throwing colors in at random, though...

## **Defining the shades of gray**

A good practice when working with color is to define a system up-front. For very small projects like this one, 5 shades of each color should be enough. For larger projects, 9 - 10 shades are best.

If you check out the [Tailwind](https://tailwindcss.com/docs/customizing-colors) and [Material UI](https://material-ui.com/customization/color/#color) documentation you can observe this pattern in the wild.

To work out some initial shades, let's use a method based on [this article](https://refactoringui.com/previews/building-your-color-palette/) by the Refactoring UI folks.

**1. Choose a middle/base shade -** There are no set rules here, but try not to go too light or dark. For grays, a lightness of around **40 / 50** is a good start. I like to make sure this shade has enough contrast for use with text *(more on this a little later)*

**2. Choose the darkest and lightest shades -** Again, there are no right or wrong answers here. I'm using a lightness value of **10** for my darkest color and **96** for my lightest:

**3. Fill in the gaps -** Finally, choose two more shades that sit between the middle and darkest / lightest colors. The lightness values I have chosen for these two shades are **25** and **85**, respectively.

After following the steps above, you should have a rough grayscale palette all set up. This will change over time and likely need some tweaking as you work with it, but it's perfect for now.

Again, I encourage you to make these shades your own. You don't need to copy the above example exactly, but it should provide a good reference as you build your own palette.

## **Applying the shades of gray**

Let's apply our grayscale colors to our product card and mellow out those harsh visual vibes. I'm looking at you `#000`.

***Note:*** *I would usually define my shades of gray before starting any design work and apply them as I go. For the purposes of this tutorial, though, we are going to be adding them after-the-fact.*

First, let's add the pre-defined shades of gray as [CSS custom properties](https://developer.mozilla.org/en-US/docs/Web/CSS/--*) in our code. Storing our colors as custom properties will allow for simple tweaking later on.

```
:root {
  --gray-100: hsl(0, 0%, 10%);
  --gray-200: hsl(0, 0%, 25%);
  --gray-300: hsl(0, 0%, 46%);
  --gray-400: hsl(0, 0%, 83%);
  --gray-500: hsl(0, 0%, 96%);

  --white: hsl(0, 0%, 100%);
}

```

I like to label my shades `<color_name>-<increment_of_100>` This is a personal preference and it works great for me, but feel free to name them as you wish. I understand naming conventions are very personal!

Now we have our custom properties added to our CSS, we can apply them to various elements of our product card.

First, let's make the card's description our **second darkest** gray. This will leave enough room “either side” to create a visual hierarchy for our headers and meta text.

```
.card__description {
  color: var(--gray-200);
}

```

Next, we can now make our card title our **darkest** shade of gray. I often like to set headings a little darker in shade than other text elements to help them stand out.

```
.card__title {
  color: var(--gray-100);
}

```

To further build our hierarchy, let's push the card's “meta” text back a little by making it our **middle** gray shade. We can also make the little dot our **second-to-lightest** gray:

```
.card__meta {
  color: var(--gray-300);
}

.card__meta:before {
  background: var(--gray-200);
}

```

Looking good! From here, we can style up our “primary” and “secondary” buttons using an assortment of shades:

```
.card__btn {
  background: var(--gray-100);
  color: var(--white);
}

.card__btn--outline {
  background: var(--white);
  color: var(--gray-200);
  border: 1px solid var(--gray-400);
}

```

Finally, we can set our image background to our **lightest** shade of gray, and the little heart icon to the **middle**:

```
.card__img-wrapper {
  background: var(--gray-500);
}

```

```
.card__heart {
  color: var(--gray-300);
}

```

Phew! That's a lot of changes. Here's a CodePen showing everything we have done so far...

Through using *only shades of gray* we have established a clear visual hierarchy. Important elements such as the product title are darker and more prominent. Less important elements are lighter and less prominent.

Compared to the original black and white design, there is a lot more order to the card's layout. Before, every element was fighting for your eye's attention. Now, everything sits in its own space.

## **A note on accessibility - check your contrast**

When applying color, particularly to text elements, be wary of contrast. Contrast, or perceived “luminance”, is the difference in brightness between two colors.

This light gray text on a white background, for example, has a rather low contrast ratio of **1.48**:

This dark gray text has a far higher contrast ratio of **10.37**:

When working on the web, we must always hit *at least* [WCAG AA color contrast guidelines](https://www.w3.org/WAI/WCAG21/Understanding/contrast-minimum.html). This means:

- A ratio of at least **4.5:1** for regular text elements
- A ratio of at least **3:1** for large text elements *(usually around 18.5px and bold, or 24px with a regular weight)*
- A ratio of at least **3:1** for graphical objects and UI components *(the border on a text-input, for example)*

There are many methods available for checking color contrast in your designs. For testing a whole page, I like to use Chrome's [lighthouse](https://developers.google.com/web/tools/lighthouse) that runs straight from dev-tools. For checking individual colors, I like [this excellent tool](https://colourcontrast.cc/) from [Alex Clapperton](https://twitter.com/alexmclapperton).

In time, you will find your own way of checking contrast that best fits your workflow. For a start, though, these will work great.

## Choosing a personality

OK, so our product cards are looking good. By establishing a visual hierarchy, things are already looking a lot more “designed”. We have done a lot of work using *only grays*, but it's time to add a little touch of color.

First things first, spend a moment thinking about the personality you want to convey with your UI. The personality you land on will help decide your primary/base color.

If you have chosen a diamond ring for your product image, you may want to go for a regal/exclusive personality.

If you have chosen a beach umbrella, you may want to explore a happy, vibrant personality.

There are no right or wrong answers with this so go with your gut. For my herbs, I am going for calm and natural.

## **Choosing a primary color + shades**

When creating a color palette, I like to start with a single primary/base color. We will apply this color **the most** throughout our UI.

Keeping the personality you landed on earlier in mind, decide on a color to begin exploring. In my case, I have chosen **green**.

There are *tons* of resources online that explore the relationship of different colors/emotions. While these are a great reference, they aren't going to give you a definitive answer. Use them as a guide, but trust your eye. [This Wikipedia page on color psychology](https://en.wikipedia.org/wiki/Color_psychology#:~:text=Color%20psychology%20is%20the%20study,enhance%20the%20effectiveness%20of%20placebos.) is a good starting point.

Once you have chosen a rough color, how you experiment is completely up to you. Some like to work in a graphics editor such as Figma/Sketch, whilst others like to work in the browser.

If you aren't sure, fire up a new CodePen, create a square in the middle of the page, and start experimenting with `hsl()`.

...

Stuck? Don't worry!

I know, choosing a primary color can feel like an impossible task. Even after narrowing things down to an approximate hue, there are thousands of options. How on earth do you choose one?

If you find yourself getting a little lost at color sea, I recommend trying out the following:

- Research some brands/sites you like and use dev-tools or [an extension](https://www.colorzilla.com/) to inspect their palette. In particular - examine how they set the saturation and lightness for their primary/base color. This should help you get in the right ballpark for yours.
- Choose a painting or photograph you like. Use a browser extension to extract its colors in the same way as above. This can be a fantastic source of inspiration if you hit a wall!
- Try a color generator such as [coolors.co](https://coolors.co/), or check out a design resource such as [colors.cafe](https://twitter.com/colours__cafe). Whilst I don't recommend using a generator or preset palette for your *whole* color scheme... they could help you find a great primary/base color to start with.

For my primary color, I have landed on this shade of green:

Why?

First, it fits my desired natural/calm personality.

Second, it has enough contrast against a white background for text elements. This will make adding it to the UI far easier in the future. Again, there are no right or wrong answers here, but try and choose a color that hits these two criteria.

Once you have chosen your primary color, you will need to define some more shades. For this, you can follow the exact process we ran through to choose our grays. For my green color, that looks like this:

***Note:*** *darker shades often need more saturation, whilst lighter shades often need a little less.*

Say, in an alternate universe I had decided to use the beach umbrella emoji for my product image, I may have ended up with some colors like this:

If I had chosen the candy/sweets as my product, I may have ended up with something like this:

## Applying the primary/base color

Awesome. We now have each have a unique primary/base color + shades to apply to our product card. Although we have 5 exciting shades to choose from, we only need to apply *touches* of color. Remember, our grays can do most of the work.

To get started, place your primary/base color shades into your CSS in the same way as your grays:

```
:root {
  --green-100: hsl(152, 100%, 8%);
  --green-200: hsl(152, 100%, 16%);
  --green-300: hsl(152, 100%, 25%);
  --green-400: hsl(152, 50%, 50%);
  --green-500: hsl(152, 50%, 96%);
}

```

A great way to get started applying your primary/base color is to add it to a button. In our case, the “Buy now” button is perfect. It is the main action we want to highlight for the card, and adding a splash of color will help it stand out.

Let's set the buttons' background to our **middle** shade and its text color to the **lightest** shade. This is a handy little tip I use a lot. A lighter shade of a color sat on top of a darker shade will often look a lot more natural than pure white:

```
.card__btn {
  background: var(--green-300);
  color: var(--green-500);
}

```

Looking good! Next up let's set our product image background to our **lightest** shade:

```
.card__img-wrapper {
  background: var(--green-500);
}

```

Finally, let's set our little meta-info dot to our **second-to-lightest** shade:

```
.card__meta:before {
  background: var(--green-400);
}

```

Here's a Codepen showing my product card after making these changes:

Through using a few splashes of color, we have added a ton of personality to our product card.

Don't worry if you aren't 100% happy with your first try here. This stuff takes practice. If you get stuck, try a different product emoji and experiment with some different colors!

## Tinted grays

A great tip for making the colors in your UI feel more coherent, is to add a hint of your primary/base color to your grays. You will want to keep this subtle. Darker shades can take more of a tint than lighter shades.

For my color choices, that looks something like this:

My “gray” custom properties now look like this:

```
:root {
  --gray-100: hsl(152, 45%, 10%);
  --gray-200: hsl(152, 25%, 25%);
  --gray-300: hsl(152, 10%, 40%);
  --gray-400: hsl(152, 10%, 83%);
  --gray-500: hsl(152, 10%, 96%);
}

```

*Pssst... Remember to re-check your color contrast after adjusting your grays! You may need to tweak the lightness value of some of your colors after introducing a tint.*

Here is a CodePen showing my product card UI with these shades applied:

Not bad, eh! It's a small change, but it's worth making.

## Expanding your palette

At this point, our product card is almost complete. We have achieved a lot with only 5 shades of a primary/base color, and 5 shades of gray. For our small design, this is almost enough. For larger projects, you are likely going to need more.

Combining colors and building color palettes deserves an entire post all to itself. For our basic design, though, let's explore a simple way to add 1 more color to our UI...

Remember the color wheel from earlier? This is going to be our new best friend when it comes to finding colors that work together.

By starting at our base color hue, and rotating 180 degrees, we will reach our base's *complimentary* hue. You can pretty much guarantee that this hue and your primary/base hue will work great together!

Here's a visualization:

For me, the complementary hue is a maroon color. For you, it could be anything! To achieve this in CSS, just add 180 to your primary/base hue value.

*Note, in CSS hsl(), numbers above 360 will simply “wrap” back around to 0, so don't worry about doing any fancy calculation. Adding 180 to your base hue is all you need.*

Boom! That's it. From here, you can follow the same pattern we used before to create 5 shades. For me, that looks like this:

Once you have defined your shades, you can add them as custom properties and apply them how you wish. For me, I am going to use my new complementary shades to add some color to the “like” button:

```
.card__heart {
  color: var(--maroon-300);
  fill: var(--maroon-500);
}

```

That's it. We're done!

Your product card should look similar to mine, but with a totally different color scheme and product.

## Wrapping up

That's all folks. I hope you learned some useful new things about color from this tutorial. I hope you managed to make a cool product card, too. Whilst the example we created is simple, the techniques applied here will see you through much larger projects.

If you like, please share any CodePens / examples you make. I'd love to see them!

**Enjoyed this tutorial? Follow me on Twitter [@georgedoescode](https://twitter.com/georgedoescode) for more front-end/creative coding content 🎨**

*This tutorial took around 12 hours to put together, all in. If you would like to support my work you can [buy me a coffee](https://ko-fi.com/georgedoescode)*