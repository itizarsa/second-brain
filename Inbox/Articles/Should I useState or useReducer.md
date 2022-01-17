# Should I useState or useReducer?

Source: Article
Status: Unprocessed
URL: https://kentcdodds.com/blog/should-i-usestate-or-usereducer

![https://res.cloudinary.com/kentcdodds-com/image/upload/v1625033326/kentcdodds.com/content/blog/should-i-usestate-or-usereducer/banner.png](https://res.cloudinary.com/kentcdodds-com/image/upload/v1625033326/kentcdodds.com/content/blog/should-i-usestate-or-usereducer/banner.png)

---

![Should%20I%20useState%20or%20useReducer%20c923233ce32a48209980856caf8ab4cd/banner.png](Should%20I%20useState%20or%20useReducer%20c923233ce32a48209980856caf8ab4cd/banner.png)

*Two built-in React hooks that handle state, which one should you use?*

Whenever there are two things to do the same thing, people inevitably ask: "When do I use one over the other?" There are two possible reasons for having multiple ways of doing the same thing:

1. One is the "old way" and the other is the "new (and improved) way". Typically the old way is kept around for backward compatibility reasons and the new way is the path forward for new code. For example: class components (old way) vs function components (new way).
2. They come with different trade-offs that should be considered and therefore should be applied in situations that suit them better (sometimes meaning you'll use more than one in a given application). For example: `[useEffect` vs `useLayoutEffect`](https://kentcdodds.com/blog/useeffect-vs-uselayouteffect) or [Static vs Unit vs Integration vs E2E tests](https://kentcdodds.com/blog/unit-vs-integration-vs-e2e-tests) or ["Control Props" vs "State Reducers"](https://kentcdodds.com/blog/control-props-vs-state-reducers)

`useState` and `useReducer` fall into the second category here. So let's talk about the trade-offs.

(and no, it's not a [trick question](https://twitter.com/ryanflorence/status/1234534306707456000) 😂).

## Examples

I think the best way to discuss these trade-offs is through the lens of examples. We'll look at two examples. One which suits `useState` better, and one which suits `useReducer` better. This won't be enough to cover all of the trade-offs, but hopefully can be a good starting point for us.

### Custom `useDarkMode` hook

I recently wrote this for my workshop projects ([for example](https://react-fundamentals.netlify.com/)). It's pretty interesting, so let's compare `useState` and `useReducer` implementations for that:

### `useState` implementation

I'll highlight the areas where we're interacting with the state:

```
1function useDarkMode() {2  const preferDarkQuery = '(prefers-color-scheme: dark)'3  const [mode, setMode] = React.useState(4    () =>5      window.localStorage.getItem('colorMode') ||6      (window.matchMedia(preferDarkQuery).matches ? 'dark' : 'light'),9  React.useEffect(() => {10    const mediaQuery = window.matchMedia(preferDarkQuery)11    const handleChange = () => setMode(mediaQuery.matches ? 'dark' : 'light')12    mediaQuery.addListener(handleChange)13    return () => mediaQuery.removeListener(handleChange)14  }, [])16  React.useEffect(() => {17    window.localStorage.setItem('colorMode', mode)18  }, [mode])20  return [mode, setMode]
```

Hopefully that makes sense. Basically we're saying, if the user's set their preferences to dark mode, then we'll initialize our mode to `dark`, otherwise we'll initialize to `light` and then return the `mode` and `setMode` and as the mode changes (whether by calling `setMode` directly or as the user changes their system preferences) we'll keep that value set in `localStorage` for future use.

### `useReducer` implementation:

There are several ways you could write this with `useReducer`. I'll start out with the typical way most people write reducers:

Wow, I think we can both agree that the `useState` version was WAY simpler! But wait! We can drastically simplify the `useReducer` version by going against the "grain" and not writing your typical redux-style reducer. Let's try that:

That's a lot better than our other try with `useReducer`. But we basically [implemented `useState` with `useReducer`](https://kentcdodds.com/blog/how-to-implement-usestate-with-usereducer). And even then, it's still less clear than our `useState` version. So at the end of the day, `useState` was a much better solution in this case.

### Custom `useUndo` hook

There's a great `[useUndo` hook on GitHub](https://github.com/xxhomey19/use-undo). I took inspiration from that for this example. Thank you [Homer Chen](https://twitter.com/xxhomey19)!

(For these, almost everything is interacting with state, so... no highlights...)

### `useState` implementation

Looks pretty ok right? It probably is, but there's actually a situation where this could be pretty buggy. But first, I want to address a common misconception people have about calling multiple state updaters in sequence (like we're doing in each of those functions).

Often people think this means that you'll trigger a re-render for each call (so, they're suggesting that calling `reset` would trigger three rerenders). First, remember to focus on [Fixing the slow render before you fix the re-render](https://kentcdodds.com/blog/fix-the-slow-render-before-you-fix-the-re-render), but secondly, remember that React has a batch system so if you were to call `reset` from an event handler or in a `useEffect` callback, it would trigger only one re-render.

That said, if we were to call `reset` in an async function (like after making an HTTP request), then that *would* result in three re-renders. However, in the future with concurrent mode those will be batched as well. So my main concern isn't the re-renders.

My concern is with the insidious stale closure bugs in our code! Can you spot them? There are three! I'll give you a hint, there's one in each of `undo`, `redo`, and `set`, but there's not one in `reset`.

Here's a contrived example that would reveal this bug:

The printed result here would be:

It should be:

So what happened to `"second"` in our situation? Ah! Turns out we're missing our dependency on `set` in the effect dependency array. Silly goose. Let's add those:

Great, save, reload... Wait wut? Oh no! Here's what happened when I added those:

But wait! Aren't we memoizing the `set` function? It shouldn't change unless its dependencies change... Wait... That includes the `past` and `present` values... And whoops! When we call `set` those values are changed, which leads to our infinite loop!

Now, this may seem contrived, but a similar bug could come up if you were updating the state based on network events and they came back in a different order from when they were sent out. Either way, you just don't want to have to think about this kind of thing right? Right.

So we can fix this problem with `useReducer`, but we can actually change our `useState` implementation and side-step this issue and I thought you'd enjoy that, so here it is:

There are a few things I did to fix this issue:

1. I used state updater callbacks in when calling the state updater functions so I could receive the `currentState` as an argument. This meant that I didn't need to list the state as a dependency.
2. I combined all the state into a single object. I had to do this because there are situations where you need one value to determine another. For example, in `redo`, I need the value of `present` to update `past` and the value of `future` to update `present`.
3. I did the calculations for `canUndo` and `canRedo` within the state updater callbacks based on the `currentState` I receive from the arguments so I didn't need to list those in the dependency array.

That solves the issue we were having and it does so pretty well, but let's try this same thing with `useReducer` to compare.

### `useReducer` implementation

Wow, the `useUndo` thing itself is actually very simple now. If we had started with `useReducer` from the get-go, we wouldn't have even considered adding anything to our dependency array because those functions are so simple they don't need anything. All the logic lives in our reducer. That helps us avoid the issue naturally.

You may find it interesting that the switch cases in our reducer are basically exactly what the contents of our functions were before we made the change.

> When one element of your state relies on the value of another element of your state in order to update: useReducer
> 

## Conclusion

So if you want some "rules" (NOT ESLINT RULES), here they are:

- **When it's just an independent element of state you're managing: `useState`**
- **When one element of your state relies on the value of another element of your state in order to update: `useReducer`**

Outside of these "rules," everything else is really subjective. Honestly, even the "rules" are subjective because as I demonstrated, you can do everything you want with either one.

Also, please note that this applies on a case-by-case basis. You can absolutely use `useState` in the same component or hook that's using `useReducer`. And you can have multiple `useState`s and multiple `useReducer`s in a single hook or component. That's no problem. Separate state logically by domain. If it changes together, it's likely better to keep together in a reducer. If something is pretty independent from other elements of state in that hook/component, then putting it with other elements of state is just adding unnecessary complexity and noise to that reducer and you'd be better off leaving it out on its own.

So it's not just "when I have more than X number of `useState`s I switch to `useReducer`." It's more nuanced than that. But hopefully this post helps you understand those nuances and reach for the tool that has the trade-offs that work best for your situation. In general, I suggest starting with `useState`, and moving to `useReducer` when you notice elements of state need to change together.

Good luck!