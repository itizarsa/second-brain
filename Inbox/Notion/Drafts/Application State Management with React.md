# Application State Management with React

Source: Article
Status: Unprocessed
URL: https://kentcdodds.com/blog/application-state-management-with-react

![https://res.cloudinary.com/kentcdodds-com/image/upload/v1625032132/kentcdodds.com/content/blog/application-state-management-with-react/banner.jpg](https://res.cloudinary.com/kentcdodds-com/image/upload/v1625032132/kentcdodds.com/content/blog/application-state-management-with-react/banner.jpg)

---

![Application%20State%20Management%20with%20React%20772cc34784fe4b84b78158f36a0cb3c4/banner.jpg](Application%20State%20Management%20with%20React%20772cc34784fe4b84b78158f36a0cb3c4/banner.jpg)

*How React is all you need to manage your application state*

Current Available Translations:

Managing state is arguably the hardest part of any application. It's why there are so many state management libraries available and more coming around every day (and even some built on top of others... There are hundreds of "easier redux" abstractions on npm). Despite the fact that state management is a hard problem, I would suggest that one of the things that makes it so difficult is that we often over-engineer our solution to the problem.

There's one state management solution that I've personally tried to implement for as long as I've been using React, and with the release of React hooks (and massive improvements to React context) this method of state management has been drastically simplified.

We often talk about React components as lego building blocks to build our applications, and I think that when people hear this, they somehow think this excludes the state aspect. The "secret" behind my personal solution to the state management problem is to think of how your application's state maps to the application's tree structure.

One of the reasons redux was so successful was the fact that react-redux solved the [prop drilling](https://kentcdodds.com/blog/prop-drilling) problem. The fact that you could share data across different parts of your tree by simply passing your component into some magical `connect` function was wonderful. Its use of reducers/action creators/etc. is great too, but I'm convinced that the ubiquity of redux is because it solved the prop drilling pain point for developers.

This is the reason that I only ever used redux on one project: I consistently see developers putting *all* of their state into redux. Not just global application state, but local state as well. This leads to a lot of problems, not the least of which is that when you're maintaining any state interaction, it involves interacting with reducers, action creators/types, and dispatch calls, which ultimately results in having to open many files and trace through the code in your head to figure out what's happening and what impact it has on the rest of the codebase.

To be clear, this is fine for state that is truly global, but for simple state (like whether a modal is open or form input value state) this is a big problem. To make matters worse, it doesn't scale very well. The larger your application gets, the harder this problem becomes. Sure you can hook up different reducers to manage different parts of your application, but the indirection of going through all these action creators and reducers is not optimal.

Having all your application state in a single object can also lead to other problems, even if you're not using Redux. When a React `<Context.Provider>` gets a new value, all the components that consume that value are updated and have to render, even if it's a function component that only cares about part of the data. That might lead to potential performance issues. (React-Redux v6 also tried to use this approach until they realized it wouldn't work right with hooks, which forced them to use a different approach with v7 to solve these issues.) But my point is that you don't have this problem if you have your state more logically separated and located in the react tree closer to where it matters.

Here's the real kicker, if you're building an application with React, you already have a state management library installed in your application. You don't even need to `npm install` (or `yarn add`) it. It costs no extra bytes for your users, it integrates with all React packages on npm, and it's already well documented by the React team. It's React itself.

> React is a state management library
> 

When you build a React application, you're assembling a bunch of components to make a tree of components starting at your `<App />` and ending at your `<input />`s, `<div />`s and `<button />`s. You don't manage all of the low-level composite components that your application renders in one central location. Instead, you let each individual component manage that and it ends up being a really effective way to build your UI. You can do this with your state as well, and it's very likely that you do today:

```
1function Counter() {2  const [count, setCount] = React.useState(0)3  const increment = () => setCount(c => c + 1)4  return <button onClick={increment}>{count}</button>7function App() {8  return <Counter />
```

Note that everything I'm talking about here works with class components as well. Hooks just make things a bit easier (especially context which we'll get into in a minute).

```
1class Counter extends React.Component {2  state = {count: 0}3  increment = () => this.setState(({count}) => ({count: count + 1}))4  render() {5    return <button onClick={this.increment}>{this.state.count}</button>
```

"Ok, Kent, sure having a single element of state managed in a single component is easy, but what do you do when I need to share that state across components? For example, what if I wanted to do this:"

```
1function CountDisplay() {2  // where does `count` come from?3  return <div>The current counter count is {count}</div>6function App() {7  return (8    <div>9      <CountDisplay />10      <Counter />11    </div>
```

"The `count` is managed inside `<Counter />`, now I need a state management library to access that `count` value from the `<CountDisplay />` and update it in `<Counter />`!"

The answer to this problem is as old as React itself (older?) and has been in the docs for as long as I can remember: [Lifting State Up](https://reactjs.org/docs/lifting-state-up.html)

"Lifting State Up" is legitimately the answer to the state management problem in React and it's a rock solid one. Here's how you apply it to this situation:

We've just changed who's responsible for our state and it's really straightforward. And we could keep lifting state all the way to the top of our app.

"Sure Kent, ok, but what about the [prop drilling](https://kentcdodds.com/blog/prop-drilling) problem?"

Great question. Your first line of defense against this is to change the way you're structuring your components. Take advantage of [component composition](https://reactjs.org/docs/context.html#before-you-use-context). Maybe instead of:

You could do this instead:

If that's not super clear (because it's super contrived), [Michael Jackson](https://twitter.com/mjackson) has [a great video](https://www.youtube.com/watch?v=3XaXKiXtNjw) you can watch to help clarify what I mean.

Eventually though, even composition's not going to do it for you, so your next step is to jump into React's Context API. This has actually been a "solution" for a long time, but for a long time that solution was "unofficial." As I said, many people reached for `react-redux` because it solved this problem using the mechanism I'm referring to without them having to be worried about the warning that was in the React docs. But now that `context` is an officially supported part of the React API, we can use this directly without any problem:

> NOTE: That particular code example is VERY contrived and I would NOT recommend you reach for context to solve this specific scenario. Please read Prop Drilling to get a better sense for why prop drilling isn't necessarily a problem and is often desirable. Don't reach for context too soon!
> 

And what's cool about this approach is that we could put all the logic for common ways to update the state in our `useCount` hook:

And you could easily change this to `useReducer` rather than `useState` as well:

This gives you an immense amount of flexibility and reduces complexity by orders of magnitude. Here are a few important things to remember when doing things this way:

1. Not everything in your application needs to be in a single state object. Keep things logically separated (user settings does not necessarily have to be in the same context as notifications). You will have multiple providers with this approach.
2. Not all of your context needs to be globally accessible! **Keep state as close to where it's needed as possible.**

More on that second point. Your app tree could look something like this:

Notice that each page can have its own provider that has data necessary for the components underneath it. Code splitting "just works" for this stuff as well. How you get data *into* each provider is up to the hooks those providers use and how you retrieve data in your application, but you know just where to start looking to find out how that works (in the provider).

**For even more about why this colocation is beneficial, check out my ["State Colocation will make your React app faster"](https://kentcdodds.com/blog/state-colocation-will-make-your-react-app-faster) and ["Colocation"](https://kentcdodds.com/blog/colocation) blog posts. And for more about context, read [How to use React Context effectively](https://kentcdodds.com/blog/how-to-use-react-context-effectively)**

## Server Cache vs UI State

One last thing I want to add. There are various categories of state, but every type of state can fall into one of two buckets:

1. Server Cache - State that's actually stored on the server and we store in the client for quick-access (like user data).
2. UI State - State that's only useful in the UI for controlling the interactive parts of our app (like modal `isOpen` state).

We make a mistake when we combine the two. Server cache has inherently different problems from UI state and therefore needs to be managed differently. If you embrace the fact that what you have is not actually state at all but is instead a cache of state, then you can start thinking about it correctly and therefore managing it correctly.

You can definitely manage this yourself with your own `useState` or `useReducer` with the right `useContext` here and there. But allow me to help you cut to the chase and say that caching is a really hard problem (some say that it's one of the hardest in computer science) and it would be wise to stand on the shoulders of giants on this one.

This is why I use and recommend [react-query](https://github.com/tannerlinsley/react-query) for this kind of state. I know I know, I told you that you don't need a state management library, but I don't really consider react-query to be a state management library. I consider it to be a cache. And it's a darn good one. Give it a look! That [Tanner Linsley](https://twitter.com/tannerlinsley) is one smart cookie.

## What about performance?

When you follow the advice above, performance will rarely be an issue. Particularly when you're following [the recommendations around colocation](https://kentcdodds.com/blog/state-colocation-will-make-your-react-app-faster). However, there are definitely use cases where performance can be problematic. When you have state-related performance problems, the first thing to check is how many components are being re-rendered due to a state change and determine whether those components really need to be re-rendered due to that state change. If they do, then the perf issue isn't in your mechanism for managing state, but in the speed of your render in which case you need to [speed up your renders](https://kentcdodds.com/blog/fix-the-slow-render-before-you-fix-the-re-render).

However, if you notice that there are a lot of components that are rendering with no DOM updates or needed side-effects, then those components are rendering unnecessarily. This happens all the time with React and it's normally not a problem by itself (and you should [focus on making even unnecessary re-renders fast first](https://kentcdodds.com/blog/fix-the-slow-render-before-you-fix-the-re-render)), but if it really is the bottleneck, then here are a few approaches to solving performance issues with state in React context:

1. Separate your state into different logical pieces rather than in one big store, so a single update to any part of state does NOT trigger an update to every component in your app.
2. [Optimize your context provider](https://kentcdodds.com/blog/how-to-use-react-context-effectively)
3. Bring in [jotai](https://github.com/react-spring/jotai)

There it is again, another recommendation for a library. It's true, there are *some* use cases for which React's built-in state management abstractions are not well suited. Of all the available abstractions, jotai is the most promising for those use cases. If you're curious what those use cases are, the types of problems jotai solves well are actually really well described in [Recoil: State Management for Today's React - Dave McCabe aka @mcc_abe at @ReactEurope 2020](https://www.youtube.com/watch?v=_ISAA_Jt9kI). Recoil and jotai are very similar (and solve the same types of problems). But based on my (limited) experience with them, I prefer jotai.

In any case, *most* apps won't need an atomic state management tool like recoil or jotai.

## Conclusion

Again, this is something that you can do with class components (you don't have to use hooks). Hooks make this much easier, but you could implement this philosophy with React 15 no problem. Keep state as local as possible and use context only when prop drilling really becomes a problem. Doing things this way will make it easier for you to maintain state interactions.