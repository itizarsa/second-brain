# How to use React Context effectively

Source: Article
Status: Unprocessed
URL: https://kentcdodds.com/blog/how-to-use-react-context-effectively

![https://res.cloudinary.com/kentcdodds-com/image/upload/v1625032892/kentcdodds.com/content/blog/how-to-use-react-context-effectively/banner.jpg](https://res.cloudinary.com/kentcdodds-com/image/upload/v1625032892/kentcdodds.com/content/blog/how-to-use-react-context-effectively/banner.jpg)

---

![How%20to%20use%20React%20Context%20effectively%20462ddc4612e04502b6254609facabe18/banner.jpg](How%20to%20use%20React%20Context%20effectively%20462ddc4612e04502b6254609facabe18/banner.jpg)

Photo by [Pathum Danthanarayana](https://unsplash.com/photos/KLbUohEjb04)

*How to create and expose React Context providers and consumers*

Current Available Translations:

In [Application State Management with React](https://kentcdodds.com/blog/application-state-management-with-react), I talk about how using a mix of local state and React Context can help you manage state well in any React application. I showed some examples and I want to call out a few things about those examples and how you can create React context consumers effectively so you avoid some problems and improve the developer experience and maintainability of the context objects you create for your application and/or libraries.

> Note, please do read Application State Management with React and follow the advice that you shouldn't be reaching for context to solve every state sharing problem that crosses your desk. But when you do need to reach for context, hopefully this blog post will help you know how to do so effectively. Also, remember that context does NOT have to be global to the whole app, but can be applied to one part of your tree and you can (and probably should) have multiple logically separated contexts in your app.
> 

First, let's create a file at `src/count-context.js` and we'll create our context there:

```
2import * as React from 'react'4const CountContext = React.createContext()
```

First off, I don't have an initial value for the `CountContext`. If I wanted an initial value, I would call `React.createContext({count: 0})`. But I don't include a default value and that's intentional. The `defaultValue` is only useful in a situation like this:

```
1function CountDisplay() {2  const {count} = React.useContext(CountContext)3  return <div>{count}</div>6ReactDOM.render(<CountDisplay />, document.getElementById('⚛️'))
```

Because we don't have a default value for our `CountContext`, we'll get an error on the highlighted line where we're destructuring the return value of `useContext`. This is because our default value is `undefined` and you cannot destructure `undefined`.

None of us likes runtime errors, so your knee-jerk reaction may be to add a default value to avoid the runtime error. However, what use would the context be if it didn't have an actual value? If it's just using the default value that's been provided, then it can't really do much good. 99% of the time that you're going to be creating and using context in your application, you want your context consumers (those using `useContext`) to be rendered within a provider which can provide a useful value.

> Note, there are situations where default values are useful, but most of the time they're not necessary or useful.
> 

[The React docs](https://reactjs.org/docs/context.html#reactcreatecontext) suggest that providing a default value "can be helpful in testing components in isolation without wrapping them." While it's true that it allows you to do this, I disagree that it's better than wrapping your components with the necessary context. Remember that every time you do something in your test that you don't do in your application, you reduce the amount of confidence that test can give you. [There are reasons to do this](https://kentcdodds.com/blog/the-merits-of-mocking), but that's not one of them.

> Note: If you're using TypeScript, not providing a default value can be really annoying for people who are using React.useContext, but I'll show you how to avoid that problem altogether below. Keep reading!
> 

## The Custom Provider Component

Ok, let's continue. For this context module to be useful *at all* we need to use the Provider and expose a component that provides a value. Our component will be used like this:

```
1function App() {2  return (4      <CountDisplay />5      <Counter />6    </CountProvider>10ReactDOM.render(<App />, document.getElementById('⚛️'))
```

So let's make a component that can be used like that:

> NOTE: this is a contrived example that I'm intentionally over-engineering to show you what a more real-world scenario would be like. This does not mean it has to be this complicated every time! Feel free to use useState if that suits your scenario. In addition, some providers are going to be short and simple like this, and others are going to be MUCH more involved with many hooks.
> 

## The Custom Consumer Hook

Most of the APIs for context usages I've seen in the wild look something like this:

But I think that's a missed opportunity at providing a better user experience. Instead, I think it should be like this:

This has the benefit of you being able to do a few things which I'll show you in the implementation now:

First, the `useCount` custom hook uses `React.useContext` to get the provided context value from the nearest `CountProvider`. However, if there is no value, then we throw a helpful error message indicating that the hook is not being called within a function component that is rendered within a `CountProvider`. This is most certainly a mistake, so providing the error message is valuable. ***#FailFast***

## The Custom Consumer Component

If you're able to use hooks at all, then skip this section. However if you need to support React `<` 16.8.0, or you think the Context needs to be consumed by class components, then here's how you could do something similar with the render-prop based API for context consumers:

And here's how class components would use it:

This is what I used to do before we had hooks and it worked ok. I would not recommend bothering with this if you can use hooks though. Hooks are much better.

## TypeScript

I promised I'd show you how to avoid issues with skipping the `defaultValue` when using TypeScript. Guess what! By doing what I'm suggesting, you avoid the problem by default! It's actually not a problem at all. Check it out:

With that, anyone can use `useCount` without having to do any undefined-checks, because we're doing it for them!

## What about dispatch `type` typos?

At this point, you reduxers are yelling: "Hey, where are the action creators?!" If you want to implement action creators that is fine by me, but I never liked action creators. I have always felt like they were an unnecessary abstraction. Also, if you are using TypeScript and have your actions well typed, then you should not need them. You can get autocomplete and inline type errors!

![How%20to%20use%20React%20Context%20effectively%20462ddc4612e04502b6254609facabe18/auto-complete.png](How%20to%20use%20React%20Context%20effectively%20462ddc4612e04502b6254609facabe18/auto-complete.png)

![How%20to%20use%20React%20Context%20effectively%20462ddc4612e04502b6254609facabe18/type-error.png](How%20to%20use%20React%20Context%20effectively%20462ddc4612e04502b6254609facabe18/type-error.png)

I really like passing `dispatch` this way and as a side benefit, `dispatch` is stable for the lifetime of the component that created it, so you don't need to worry about passing it to `useEffect` dependencies lists (it makes no difference whether it is included or not).

If you are not typing your JavaScript (you probably should consider it if you have not), then the error we throw for missed action types is a failsafe. Also, read on to the next section because this can help you too.

## What about async actions?

This is a great question. What happens if you have a situation where you need to make some asynchronous request and you need to dispatch multiple things over the course of that request? Sure you could do it at the calling component, but manually wiring all of that together for every component that needs to do something like that would be pretty annoying.

What I suggest is you make a helper function within your context module which accepts `dispatch` along with any other data you need, and make that helper be responsible for dealing with all of that. Here's an example from [my Advanced React Patterns workshop](https://kentcdodds.com/workshops/advanced-react-patterns):

Then you can use that like this:

I'm really happy with this pattern and if you'd like me to teach this at your company [let me know](https://kentcdodds.com/contact) (or [add yourself to the waitlist](https://kentcdodds.com/workshops/advanced-react-patterns) for the next time I host the workshop)!

## Conclusion

So here's the final version of the code:

Note that I'm *NOT* exporting `CountContext`. This is intentional. I expose only one way to provide the context value and only one way to consume it. This allows me to ensure that people are using the context value the way it should be and it allows me to provide useful utilities for my consumers.

I hope this is useful to you! Remember:

1. You shouldn't be reaching for context to solve every state sharing problem that crosses your desk.
2. Context does NOT have to be global to the whole app, but can be applied to one part of your tree
3. You can (and probably should) have multiple logically separated contexts in your app.

Good luck!