# CSS Flip Animation

Source: Article
Status: Unprocessed
URL: https://davidwalsh.name/css-flip

![https://davidwalsh.name/demo/css-flip.png](https://davidwalsh.name/demo/css-flip.png)

---

You've all asked for it and now I've added it: Internet Explorer support! Annoyingly enough, the change involves rotate the `front` and `back` elements instead of just the container. [Skip to this section](https://davidwalsh.name/css-flip) if you'd like the Internet Explorer code. IE10+ is supported; IE9 does not support CSS animations.

![CSS%20Flip%20Animation%20f02a0d2818d247059ba213eb79e31d69/css-flip.png](CSS%20Flip%20Animation%20f02a0d2818d247059ba213eb79e31d69/css-flip.png)

CSS animations are a lot of fun; the beauty of them is that through many simple properties, you can create anything from an elegant fade in to a WTF-Pixar-would-be-proud effect. One CSS effect somewhere in between is the CSS flip effect, whereby there's content on both the front and back of a given container. This tutorial will show you show to create that effect in as simple a manner as possible.

![CSS%20Flip%20Animation%20f02a0d2818d247059ba213eb79e31d69/gofast-long.svg](CSS%20Flip%20Animation%20f02a0d2818d247059ba213eb79e31d69/gofast-long.svg)

*Quick note: this is not the first tutorial about this effect, but I've found the others over-complicated. Many other tutorials add additional styles to code samples which then require the reader to decipher which are needed and which aren't. This tutorial avoids that issue, providing you only the necessary styles; you can pretty up each side of the flip any way you'd like.*

## The HTML

The HTML structure to accomplish the two-sided effect is as you would expect it to be:

```
<div class="flip-container" ontouchstart="this.classList.toggle('hover');">
	<div class="flipper">
		<div class="front">
			<!-- front content -->
		</div>
		<div class="back">
			<!-- back content -->
		</div>
	</div>
</div>
```

There are two content panes, "front" and "back", as you would expect, but also two containing elements with very specific roles explained by their CSS. Also note the `ontouchstart` piece which allows the panes to swap on touch screens. Obviously you should break that code into a separate, unobtrusive JavaScript block if you wish.

## The CSS

I'm willing to bet that outside of the usual vendor prefix bloat, you'd be surprised at how little CSS is involved:

```
/* entire container, keeps perspective */
.flip-container {
	perspective: 1000px;
}
	/* flip the pane when hovered */
	.flip-container:hover .flipper, .flip-container.hover .flipper {
		transform: rotateY(180deg);
	}

.flip-container, .front, .back {
	width: 320px;
	height: 480px;
}

/* flip speed goes here */
.flipper {
	transition: 0.6s;
	transform-style: preserve-3d;

	position: relative;
}

/* hide back of pane during swap */
.front, .back {
	backface-visibility: hidden;

	position: absolute;
	top: 0;
	left: 0;
}

/* front pane, placed above back */
.front {
	z-index: 2;
	/* for firefox 31 */
	transform: rotateY(0deg);
}

/* back, initially hidden pane */
.back {
	transform: rotateY(180deg);
}
```

Here's a rough overview of the process:

- The outlying container sets the entire animation area's [perspective](https://developer.mozilla.org/en-US/docs/CSS/perspective)
- The inner container is the element that actually flips, spinning 180 degrees when the parent container is hovered over. This is also where you control the transition speed. Changing the rotation to -180deg spins the elements in the reverse direction.
- The front and back elements are positioned absolutely so they can "overlay" each other in the same position; their [backface-visibility](https://developer.mozilla.org/en-US/docs/CSS/backface-visibility) is hidden so the back of the flipped elements don't display during the animation
- The front element has a higher z-index than the back element so the front element may be coded first but it still displays on top
- The back element is rotate 180 degrees, so as to act as the back.

That's really all there is to it! Put this simple structure into place and then style each side as you'd like!

### A Note from CSS Animation Expert Ana Tudor

*[Applying certain properties with certain values](http://dev.w3.org/csswg/css-transforms/#transform-style-property) (like `overflow: hidden`) on the card element would disallow it to have 3D transformed children. I believe this is relevant because I got into trouble with `overflow: hidden` precisely in such cases, where all children of the 3D transformed element were in the same plane, but one or more had been rotated by `180deg`.*

## CSS Flip Toggle

If you'd prefer the element only flip on command via JavaScript, a simple CSS class toggle will do the trick:

```
.flip-container:hover .flipper, .flip-container.hover .flipper, .flip-container.flip .flipper {
	transform: rotateY(180deg);
}
```

Adding the flip class to the container element will flip the card using JavaScript -- no user hover required. A JavaScript comment like `document.querySelector("#myCard").classList.toggle("flip")` will do the flip!

## CSS Vertical Flip

Performing a vertical flip is as easy as flipping the axis and adding the `transform-origin` axis value. The origin of the flip must be updated and the card rotated the other way:

```
.vertical.flip-container {
	position: relative;
}

	.vertical .back {
		transform: rotateX(180deg);
	}

	.vertical.flip-container .flipper {
		transform-origin: 100% 213.5px; /* half of height */
	}

	.vertical.flip-container:hover .flipper {
		transform: rotateX(-180deg);
	}
```

You can see that the `X` access gets used, not the `Y`.

## Internet Explorer Support

Internet Explorer requires significant modifications to the standard flip code because it has not yet implemented all of the modern `transform` properties. Essentially both the front and back elements need to flipped at the same time:

```
/* entire container, keeps perspective */
.flip-container {
	perspective: 1000px;
	transform-style: preserve-3d;
}
	/*  UPDATED! flip the pane when hovered */
	.flip-container:hover .back {
		transform: rotateY(0deg);
	}
	.flip-container:hover .front {
	    transform: rotateY(180deg);
	}

.flip-container, .front, .back {
	width: 320px;
	height: 480px;
}

/* flip speed goes here */
.flipper {
	transition: 0.6s;
	transform-style: preserve-3d;

	position: relative;
}

/* hide back of pane during swap */
.front, .back {
	backface-visibility: hidden;
	transition: 0.6s;
	transform-style: preserve-3d;

	position: absolute;
	top: 0;
	left: 0;
}

/*  UPDATED! front pane, placed above back */
.front {
	z-index: 2;
	transform: rotateY(0deg);
}

/* back, initially hidden pane */
.back {
	transform: rotateY(-180deg);
}

/*
	Some vertical flip updates
*/
.vertical.flip-container {
	position: relative;
}

	.vertical .back {
		transform: rotateX(180deg);
	}

	.vertical.flip-container:hover .back {
	    transform: rotateX(0deg);
	}

	.vertical.flip-container:hover .front {
	    transform: rotateX(180deg);
	}
```

With the code above, IE10 will rotate flip the elements as expected!

The CSS flip animation has always been a classic, representative example of what's possible with CSS animations, and to a lessor extent, 3D CSS animations. What's better is that there's actually very little CSS involved. This effect would be really neat for HTML5 games, and as a standalone "card" effect, it's perfect. Can you think of anything else you'd use this for?