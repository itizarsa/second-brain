# Page Visibility API

Source: Article
Status: Unprocessed
URL: https://davidwalsh.name/page-visibility

![https://davidwalsh.name/wp-content/themes/punky/images/logo.png](https://davidwalsh.name/wp-content/themes/punky/images/logo.png)

---

One event that's always been lacking within the document is a signal for when the user is looking at a given tab, or another tab. When does the user switch off our site to look at something else? When do they come back? The Page Visibility API allows developers to react to changes in page visibility via the `visibilitychange document` event. New `document.hidden` and `document.visibilityChange` properties are also available.

![Page%20Visibility%20API%20526e8165be20441aa914de2199eff503/gofast-long.svg](Page%20Visibility%20API%20526e8165be20441aa914de2199eff503/gofast-long.svg)

## document.hidden

This new document property, `document.hidden`, returns true the page is currently not visible.

## document.visibilityState

The `visibilityState` will either be `visible` (the page is the foreground tab of a non-minimized window), `hidden` (document is either a background tab or part of a minimized window), or `prerender` (the page content is being prerendered and is not visible to the user).

## visibilitychange Event

Listening for changes in window visibility is as easy as:

```
// Adapted slightly from Sam Dutton
// Set name of hidden property and visibility change event
// since some browsers only offer vendor-prefixed support
var hidden, state, visibilityChange;
if (typeof document.hidden !== "undefined") {
	hidden = "hidden";
	visibilityChange = "visibilitychange";
	state = "visibilityState";
} else if (typeof document.mozHidden !== "undefined") {
	hidden = "mozHidden";
	visibilityChange = "mozvisibilitychange";
	state = "mozVisibilityState";
} else if (typeof document.msHidden !== "undefined") {
	hidden = "msHidden";
	visibilityChange = "msvisibilitychange";
	state = "msVisibilityState";
} else if (typeof document.webkitHidden !== "undefined") {
	hidden = "webkitHidden";
	visibilityChange = "webkitvisibilitychange";
	state = "webkitVisibilityState";
}

// Add a listener that constantly changes the title
document.addEventListener(visibilityChange, function() {
	document.title = document[state];
}, false);

// Set the initial value
document.title = document[state];
```

The example above changes the `document.title` property during every visibility change!

## Supporting `visibilityChange` in MooTools

MooTools doesn't support `visibilityChange` out of the box, so you'll need to add this bit of JavaScript:

```
// Set it up!
Element.NativeEvents[visibilityChange] = 2;
Element.Events[visibilityChange] = {
	base: visibilityChange,
	condition: function(event) {
		event[state] = document[state];
		event.visibilityState = document[state];
		return true;
	}
};

// Now use it!
document.addEvent(visibilityChange, function(e) {
	document.title = document[state];
});
```

Don't you love it when it's that easy?! This mirror the code needed to add `onMessage` events to the list of supported events.

So what could `visibilitychange` be used for? You could stop periodically refreshing content when the page is no longer visible, then pull new content when the page becomes visible again. You could [pause and resume a video during visibility changes](http://www.samdutton.com/pageVisibility/). Audio too. You could adjust your site statistics to count only time spent on site while the page is visible. There's loads you can do! So...the question is...what would you do with this?