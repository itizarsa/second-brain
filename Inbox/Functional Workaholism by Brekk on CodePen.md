# Functional Workaholism by Brekk on CodePen

Source: Article
Status: Unprocessed
URL: https://codepen.io/brekk/post/functional-workaholism

![https://assets.codepen.io/6512/internal/avatars/users/default.png?fit=crop&format=auto&height=80&version=2&width=80](https://assets.codepen.io/6512/internal/avatars/users/default.png?fit=crop&format=auto&height=80&version=2&width=80)

---

Over the last year or so I've been learning functional programming (FP) and trying to fold it into my basic approach to software. I'd like to frame it here the way I'd teach it to someone who knows JS but doesn't know FP. There are [far](https://drboolean.gitbooks.io/mostly-adequate-guide/content/) [better](https://github.com/getify/Functional-Light-JS) [resources](https://egghead.io/courses/professor-frisby-introduces-composable-functional-javascript) I can point you to, but here's my take, as I can't seem to stop thinking about this stuff and I wanted to put it all in one place.

So. Assuming decent knowledge of JS, you know that JS is a wild beast of dynamism and willful trickery. 🐲 With FP, we can keep using all the underlying awesomeness, but we can add clarity, decrease cognitive load and drastically improve maintenance and readability. 😍

(Edit: we'll be using `ramda` as our functional library of choice, but it is interchangeable with many other functional libraries.)

We'll use some definitions as our starting point for these ideas.

### Arity

`Arity` is the number of arguments a function expects. It is a simple thing, but with FP you start paying a lot of attention to the arity of a function, as each parameter can be thought of as a task / dependency:

```
const taskSolver = (taskOne) => {
  // we have to _do_ something with the `taskOne` parameter
}

```

Until we deal with the `taskOne` parameter above, our function doesn't make any sense. (Either we shouldn't have defined the parameter or we are practicing willful obtuseness, and really, what is the point of doing anything? 👻 )

### Nullary functions

A `nullary` function has an arity of zero, meaning it has zero parameters and returns one value. These are functions which take nothing and return something. They get their kicks for free.

*Examples*: `Math.random`; `Date.now`

### Pure functions

One thing you're always striving for in FP are `pure` functions. These are really nice variations on your standard JS insanity-closures. Instead of everything that JS offers and can do, all tricky-like, pure functions have two great qualities:

- they are `deterministic`, meaning given the same input, they will always return the same output
- (*Edit:* I previously mentioned pure functions being `idempotent` here instead of qualifying them as `deterministic`; please see [the comments](https://codepen.io/brekk/post/functional-workaholism#comment-id-6321) for a further definition of `idempotent`, it has greater meaning than I previously understood. Thanks Rick Medina and Scott Sauyet for the corrections!)
- they have no side-effects, meaning no part of the program external to the function will be manipulated, modified or otherwise maligned.
- (*Edit:* I neglected to mention one of the most helpful properties of pure functions, which is that *because* they are deterministic, they also exhibit `referential transparency`, which means that a function invoked with all of its parameters is interchangeable with its output, e.g. `const double = (x) => x * 2; double(5) * double(3) // 10 * double(3) // 10 * 6 // 60` Thanks [Eric Elliott](https://twitter.com/_ericelliott/status/842955941003776000)!)

The simplest pure function is ultimately far more useful than it appears:

```
const identity = (x) => x

```

Whatever it receives, it returns.

Which brings us to:

### Unary functions

`Unary` functions are functions with an arity of one. These are functions which take a thing and return a thing.

*Examples*: `Math.sqrt`; `parseFloat`

These are ideal in FP land, as they really lend themselves to composition, which we will get to a bit later, and higher-order functions.

One thing you start to strive for in FP-land is understanding the common patterns and generating generic versions of a function that solve all variations.

This would be impossible without:

### Higher-order functions

`Higher-order` functions take a function as an input and/or return a function as an output. These allow you to make simple functions far more powerful. By augmenting the input function and returning a wrapped function, we can both extricate the explicit task resolution (the function being passed in has privileged access and can be defined elsewhere) and we can automate common patterns and utilize them in the wrapped function.

The most common example here would probably be `map`, which is one of the coolest. 😎

### Binary functions

`Binary` functions are functions which take two inputs and return one output.

`map` is a binary function.

```
const {R} = window // Ramda used, but others possible
const {map} = R

```

`map` takes a unary function that knows how to operate on one value,

```
const double = (x) => 2 * x
const input = 5
const output = double(input)
console.log(output) // 10

```

And changes it so that it can operate on an array of values:

```
const input = [1,2,3,4,5]
const output = map(double, input)
console.log(output) // [2,4,6,8,10]

```

Maybe you already know about `map`, but know it as the native `Array.prototype.map` instead, which isn't as reusable, but follows the same pattern:

```
[1,2,3,4,5].map(double) // [2,4,6,8,10]

```

When I say not as reusable, it's because I didn't show you the full coolness of the `Ramda.map` we're using above. `Ramda.map` is a curried function. 😏

### Curry

When we `curry` a function, we make it so that until we provide all the parameters, we keep getting back a new function which expects the remaining parameters.

If we come back to our `double` definition above:

```
const double = (x) => 2 * x

```

We have hardcoded a `2` into the function. What if we wanted to make it so that we could pass in that value? We'd need to transform it into a binary function:

```
const multiply = (x, y) => y * x

```

But, if we use `curry`, we can make it so that we can re-use the same definition as `multiply`, but only provide the parameters we want (called `partial application`).

```
const {curry} = R
const multiply = curry((x, y) => y * x)
const double = multiply(2) // we're only providing one parameter, of the expected 2

```

😱 See what we did there?

I'll show it again, but with the `map` example from before:

```
const doubleList = map(double) // we're only providing one parameter, of the expected 2
console.log(doubleList([1,3,5,7,9])) // [2,6,10,14,18]

```

When `map` is curried this way, it's much more valuable, as it allows us to extricate the array from the function which manipulates the array.

### Function Composition

This is where everything becomes the most exciting.

So, let's say you want to do something simple, like take a value, make it JSON-safe, and print it.

```
const input = [{name: `Bark Obama`, type: `dog`}, {name: `Henry Hudson`, type: `cat`}, {name: `Slartibartfast`, type: `magrathean`}]
console.log(JSON.stringify(input))

```

Now, let's say for arguments sake that we want to be able to deal with *any* input, not just the great example I wrote above. In order to do that, we must wrap the expression with a function:

```
const prettyPrint = (rawArray) => console.log(JSON.stringify(rawArray))

```

Those parentheses at the end are the key here, we're essentially saying, all math-like:

```
g(f(x))

```

"The result of the function g invoked with the result of the function f invoked with the variable x"

So, suppose we're more than delighted with our contrived function for many months, but then our requirements change. Now we need to only look at a single property, instead of the full raw list, before we stringify it.

Using Ramda's handy `prop` function, we can just grab a value if we know the name.

```
const {prop} = R
const prettyPrint = (rawArray) => console.log(
  JSON.stringify(
    map((thing) => prop(`type`, thing), rawArray)
  )
)

```

So, right away this seems like it doesn't all need to be an arrow function without braces.

```
const prettyPrint = (rawArray) => {
  const types = map((thing) => {
    return prop(`type`, thing)
  }, rawArray)
  const stringified = JSON.stringify(types)
  console.log(stringified)
}

```

Here's a secret you maybe already knew / guessed: all of Ramda's functions are curried. This means that we can go way more terse while still being clear:

```
const prettyPrint = (rawArray) => {
  const getTypes = map(prop(`type`)) // terse but clear!
  const rawTypes = getTypes(rawArray)
  const stringified = JSON.stringify(rawTypes)
  console.log(stringified)
}

```

This is an example of the identity closure, which unfortunately you see all the time in JS. The identity function, as we've discussed, is this: `(x) => x`. The identity closure is this:

```
const idClosure = (x) => someFunction(x)

```

Unless `someFunction` above has an object binding we need to be aware of, we can simply replace `idClosure` above with:

```
const idClosure = someFunction

```

And the `map(prop('type'))` example above could be termed a curried identity closure. It partially applies parameters until it becomes a unary function.

So, coming back to our example, see how I named that `getTypes` function, but we could have also done (less clearly), by skipping the intermediate definition:

```
const rawTypes = map(prop(`type`))(rawArray)

```

Getting back to the now (slightly) more complicated math-style equation:

```
g(f(e(x)))

```

`e` in our case is the once named `getTypes`.

What we can do now is very exciting.

```
const prettyPrint = (a) => {
  const b = map(prop(`type`))(a)
  const c = JSON.stringify(b)
  console.log(c)
}

```

👆🏿 I've renamed the variables temporarily for clarity. See the way we're saying, take this one input `a`, invoke this function on it, save that as `b`, invoke a function on *it*, save that as `c`, and then finally, invoke another function on `c`?

```
const {pipe} = R
const prettyPrint = pipe(
  map(prop(`type`)), // a => b
  JSON.stringify, // b => c
  console.log
)

```

🤔

So, firstly, what does `pipe` do? Pipe composes together unary functions. It takes any number of unary functions and returns a new function: under the hood it joins them together so each new function receives the value from the last function's output. So whenever you see that kind of `g(f(e(x)))` invocation, you should know that you can reformat it as a pipe-style composition.

Secondly, that's very terse, how do we know other than faith how it works?

😁 Let's dive into `trace`, the first useful thing I ever learned in FP. Pretty much anytime you wanna debug JS, one of your go-to tools is the simple `console.log` to print state somewhere. `trace` uses `console.log` to magical curried effect.

```
const trace = curry((a, b) => {
  console.log(a, b)
  return b
})

```

Seems straightforward enough. Trace is defined as a curried binary function which prints both of its inputs and only returns the second one. Because it is curried, it lends itself to pipe composition in the most readable of ways:

```
const prettyPrint = pipe(
  trace(`input`),
  map(prop(`type`)),
  trace(`types`),
  JSON.stringify,
  console.log
)

```

Coooooool. So now we have this function, `prettyPrint`, and it prints out some stuff based on `type`. That's dope. (And if you think that's exciting, check out the more generic `xtrace` further below.) But two things. One. Right now we end our composition with `console.log`, and as you may know, that means we never get a real value here. If we omit it:

```
const stringifyTypes = pipe(
  // trace(`input`),
  map(prop(`type`)),
  // trace(`types`),
  JSON.stringify
)

```

Now we have a proper unary function! 🎉

But also, Two. What if down the line, your boss comes down and says that we now need a function which can deal with `name` instead of `type`, so I'd like you to just copy this and paste it and change that one string.

*Nuh uh.*

We keep it DRY in FP land, and for good reason: it aids our equational reasoning. Check it:

```
const stringifyProp = curry((property, input) => pipe(
  map(prop(property)),
  JSON.stringify
)(input))

```

"Wow Brekk, cool new function", you say. "Still seems like extra." And again, I say:

*NUH UH!*

```
const stringifyTypes = stringifyProp(`type`)
const stringifyNames = stringifyProp(`name`)

```

Seems like we have two brand new functions, but we know 100% about how they work, because they're different morphisms of the same generic function. 💥

### xtrace

Ok. So. Finally, here's a really cool way you can take `trace` and push it to be more generic, and then provide a way to inspect our data more granularly.

So, master-level excitement, we have the ability (using `Ramda.curry`, but arguably any equivalent function could do the same) to provide "placeholder" arguments to the function ([Read more about R.__ here.](http://ramdajs.com/docs/#__)), which takes the premise of currying and partial application to a whole new level.

```
// definition taken from Ramda (issues with destructuring `__` from `R` in the past)
const placeholder = {
  [`@@functional/placeholder`]: true
}
const $__ = placeholder
const xtrace = curry((log, a, lens, b) => {
  log(a, lens(b))
  return b
})
const trace = xtrace(console.log, $__, identity, $__)

```

👆🏿 Check it. We generated a generic function which is pure pure AF (`xtrace`) and then we used its definition to redefine our previous `trace` function. Also, see how useful `identity` can be? (`console.log` is a side-effect / side-cause, unless you pass it in to the function itself, as then it is a known-quantity / pure).

Now, if we define a new function, mebbe call it `thread`:

```
const thread = xtrace(console.log)
pipe(
  thread(`scope scopies`, (x) => x.someSpecificPropertyOrWhatever)
)

```

Now we have an amazingly helpful function which has the particularly advantageous morph above, but could ostensibly be used to generate any kind of side-effects during a pipe-composition.

✋🏾 It's over!

### Read more:

### Continued Reading!

**EDIT**: Hey, it used to be over *but now there's more!* Please read about how we might visualize these composed functions more easily and how we can add the Either Monad to our composed pipelines: [https://codepen.io/brekk/post/visual-function-composition](https://codepen.io/brekk/post/visual-function-composition)