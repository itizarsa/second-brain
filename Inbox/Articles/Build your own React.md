# Build your own React

Source: Article
Status: Unprocessed
URL: https://pomb.us/build-your-own-react/

![https://pomb.us/static/b4694e6041953e3cb16f6a889f0cbc59/25036/card.png](https://pomb.us/static/b4694e6041953e3cb16f6a889f0cbc59/25036/card.png)

---

We are going to rewrite React from scratch. Step by step. Following the architecture from the real React code but without all the optimizations and non-essential features.

If you’ve read any of [my previous “build your own React” posts](https://engineering.hexacta.com/didact-learning-how-react-works-by-building-it-from-scratch-51007984e5c5), the difference is that this post is based on React 16.8, so we can now use hooks and drop all the code related to classes.

You can find the history with the old blog posts and the code on the [Didact repo](https://github.com/pomber/didact). There’s also a [talk covering the same content](https://youtu.be/8Kc2REHdwnQ). But this is a self-contained post.

Starting from scratch, these are all the things we’ll add to our version of React one by one:

- **Step I**: The `createElement` Function
- **Step II**: The `render` Function
- **Step III**: Concurrent Mode
- **Step V**: Render and Commit Phases
- **Step VI**: Reconciliation
- **Step VII**: Function Components
- **Step VIII**: Hooks

But first let’s review some basic concepts. You can skip this step if you already have a good idea of how React, JSX and DOM elements work.

We’ll use this React app, just three lines of code. The first one defines a React element. The next one gets a node from the DOM. The last one renders the React element into the container.

**Let’s remove all the React specific code and replace it with vanilla JavaScript**.

On the first line we have the element, defined with JSX. It isn’t even valid JavaScript, so in order to replace it with vanilla JS, first we need to replace it with valid JS.

JSX is transformed to JS by build tools like Babel. The transformation is usually simple: replace the code inside the tags with a call to `createElement`, passing the tag name, the props and the children as parameters.

`React.createElement` creates an object from its arguments. Besides some validations, that’s all it does. So we can safely replace the function call with its output.

And this is what an element is, an object with two properties: `type` and `props` (well, [it has more](https://github.com/facebook/react/blob/f4cc45ce962adc9f307690e1d5cfa28a288418eb/packages/react/src/ReactElement.js#L111), but we only care about these two).

The `type` is a string that specifies the type of the DOM node we want to create, it’s the `tagName` you pass to `document.createElement` when you want to create an HTML element. It can also be a function, but we’ll leave that for Step VII.

`props` is another object, it has all the keys and values from the JSX attributes. It also has a special property: `children`.

`children` in this case is a string, but it’s usually an array with more elements. That’s why elements are also trees.

The other piece of React code we need to replace is the call to `ReactDOM.render`.

`render` is where React changes the DOM, so let’s do the updates ourselves.

First we create a node* using the element `type`, in this case `h1`.

Then we assign all the element `props` to that node. Here it’s just the title.

- *To avoid confusion, I’ll use “element” to refer to React elements and “node” for DOM elements.*

Then we create the nodes for the children. We only have a string as a child so we create a text node.

Using `textNode` instead of setting `innerText` will allow us to treat all elements in the same way later. Note also how we set the `nodeValue` like we did it with the `h1` title, it’s almost as if the string had `props: {nodeValue: "hello"}`.

Finally, we append the `textNode` to the `h1` and the `h1` to the `container`.

Let’s start again with another app. This time we’ll replace React code with our own version of React.

We’ll start by writing our own `createElement`.

Let’s transform the JSX to JS so we can see the `createElement` calls.

As we saw in the previous step, an element is an object with `type` and `props`. The only thing that our function needs to do is create that object.

We use the *spread operator* for the `props` and the *rest parameter syntax* for the `children`, this way the `children` prop will always be an array.

For example, `createElement("div")` returns:

`createElement("div", null, a)` returns:

and `createElement("div", null, a, b)` returns:

The `children` array could also contain primitive values like strings or numbers. So we’ll wrap everything that isn’t an object inside its own element and create a special type for them: `TEXT_ELEMENT`.

*React doesn’t wrap primitive values or create empty arrays when there aren’t `children`, but we do it because it will simplify our code, and for our library we prefer simple code than performant code.*

In order to replace it, let’s give a name to our library. We need a name that sounds like React but also hints its *didactic* purpose.

If we have a comment like this one, when babel transpiles the JSX it will use the function we define.

For now, we only care about adding stuff to the DOM. We’ll handle updating and deleting later.

We start by creating the DOM node using the element type, and then append the new node to the container.

### Step III: Concurrent Mode

But… before we start adding more code we need a refactor.

There’s a problem with this recursive call.

Once we start rendering, we won’t stop until we have rendered the complete element tree. If the element tree is big, it may block the main thread for too long. And if the browser needs to do high priority stuff like handling user input or keeping an animation smooth, it will have to wait until the render finishes.

So we are going to break the work into small units, and after we finish each unit we’ll let the browser interrupt the rendering if there’s anything else that needs to be done.

We use `requestIdleCallback` to make a loop. You can think of `requestIdleCallback` as a `setTimeout`, but instead of us telling it when to run, the browser will run the callback when the main thread is idle.

*React [doesn’t use `requestIdleCallback` anymore](https://github.com/facebook/react/issues/11171#issuecomment-417349573). Now it uses the [scheduler package](https://github.com/facebook/react/tree/master/packages/scheduler). But for this use case it’s conceptually the same.*

`requestIdleCallback` also gives us a deadline parameter. We can use it to check how much time we have until the browser needs to take control again.

*As of November 2019, Concurrent Mode isn’t stable in React yet. The stable version of the loop looks more like this:*

To start using the loop we’ll need to set the first unit of work, and then write a `performUnitOfWork` function that not only performs the work but also returns the next unit of work.

### Step IV: Fibers

To organize the units of work we’ll need a data structure: a fiber tree.

We’ll have one fiber for each element and each fiber will be a unit of work.

Let me show you with an example.

![Build%20your%20own%20React%20a734f1f5b5a04ff1826a7d1324496f52/fiber0.png](Build%20your%20own%20React%20a734f1f5b5a04ff1826a7d1324496f52/fiber0.png)

Fiber Tree 0

Now let’s put it into code.

Try the version with reconciliation on [codesandbox](https://codesandbox.io/s/didact-6-96533).

Besides helping you understand how React works, one of the goals of this post is to make it easier for you to dive deeper in the React codebase. That’s why we used the same variable and function names almost everywhere.

For example, if you add a breakpoint in one of your function components in a real React app, the call stack should show you:

We didn’t include a lot of React features and optimizations. For example, these are a few things that React does differently:

- In Didact, we are walking the whole tree during the render phase. React instead follows some hints and heuristics to skip entire sub-trees where nothing changed.
- We are also walking the whole tree in the commit phase. React keeps a linked list with just the fibers that have effects and only visit those fibers.
- Every time we build a new work in progress tree, we create new objects for each fiber. React recycles the fibers from the previous trees.
- When Didact receives a new update during the render phase, it throws away the work in progress tree and starts again from the root. React tags each update with an expiration timestamp and uses it to decide which update has a higher priority.
- And many more…

There are also a few features that you can add easily:

If you add any of these or other features to Didact send a pull request to the [GitHub repo](https://github.com/pomber/didact), so others can see it.

Thanks for reading!

And if you want to comment, like or share this post you can use this tweet: