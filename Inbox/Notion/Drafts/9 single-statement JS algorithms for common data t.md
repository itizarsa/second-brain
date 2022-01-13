# 9 single-statement JS algorithms for common data transformations | Ben Ilegbodu

Source: Notes
Status: Unprocessed
URL: https://www.benmvp.com/blog/9-single-statement-javascript-algorithms-common-data-transformations/

[https://res.cloudinary.com/benmvp/image/upload/w_1280,h_669,c_fill,q_auto,f_auto/w_666,c_fit,co_rgb:ffffff,g_north_west,x_550,y_64,l_text:roboto_70_bold:9%2520single-statement%2520JS%2520algorithms%2520for%2520common%2520data%2520transformations/w_666,c_fit,co_rgb:ffffff,g_south_west,x_550,y_64,l_text:roboto_40_light:Reducing%2520our%2520reliance%2520on%2520Lodash%2520by%2520leveraging%2520ESNext%2520APIs%2520to%2520transform%2520objects%2520and%2520arrays/w_350,c_fit,co_rgb:ffffff,g_south_west,x_64,y_64,l_text:roboto_40:April%252004%252C%25202021/v1619329795/benmvp/blog-post-template_gkpzgc](https://res.cloudinary.com/benmvp/image/upload/w_1280,h_669,c_fill,q_auto,f_auto/w_666,c_fit,co_rgb:ffffff,g_north_west,x_550,y_64,l_text:roboto_70_bold:9%2520single-statement%2520JS%2520algorithms%2520for%2520common%2520data%2520transformations/w_666,c_fit,co_rgb:ffffff,g_south_west,x_550,y_64,l_text:roboto_40_light:Reducing%2520our%2520reliance%2520on%2520Lodash%2520by%2520leveraging%2520ESNext%2520APIs%2520to%2520transform%2520objects%2520and%2520arrays/w_350,c_fit,co_rgb:ffffff,g_south_west,x_64,y_64,l_text:roboto_40:April%252004%252C%25202021/v1619329795/benmvp/blog-post-template_gkpzgc)

---

[blog-post-template_gkpzgc](9%20single-statement%20JS%20algorithms%20for%20common%20data%20t%20c1bc7606dbe1472d8877fcb8d23df902/blog-post-template_gkpzgc)

Last month I wrote a post on a [shorthand for converting a JavaScript array into an object lookup](https://www.benmvp.com/blog/create-object-lookup-array-javascript-objects/). I was able to write the code in a single statement:

```
const teamLookup = Object.fromEntries(teams.map((team) => [team.id, team]))
```

This exercise motivated me to investigate more single-statement data transformations we can use to limit our reliance on [Lodash](https://lodash.com/) (and `[.reduce()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce)`). And now I’m posting about it. 😄

So here are the “rules”:

1. No using Lodash (kinda the whole point)
2. No `.reduce()`. Pretty much any array or object can be transformed to another array or object within a `.reduce()` so that’s no fun 😅
3. Skipping the “obvious” new ES.next functionality (like `[.find()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/find)`, [object spread](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax#spread_in_object_literals), etc)
4. No data mutations; the transformation has to generate a new object (this is necessary for [React](https://reactjs.org/) and [reducers](https://reactjs.org/docs/hooks-reference.html#usereducer))

Now that we’ve gotten that out of the way let’s look at our transformations.

JavaScript provides `[.splice()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/splice)` for removing elements from an array, but it happens in place. It mutates the array, which breaks one of our rules. But we can use `[.filter()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)` instead!

```
const newPlayers = players.filter((player) => player.id !== ID_TO_DELETE)
```

By using `.filter()` to select all the players that **do not** have the `ID_TO_DELETE`, we delete the player with that `id` while simultaneously constructing a new array. This is probably one of my most favorite JavaScript “algorithms.” I use it all the time.

## 2. Replace an item at an array index

To replace an item at an index in an array, we would normally assign the value.

```
players[indexToReplace] = newPlayer
```

But that, of course, mutates the array. And so does `.splice()`. Instead we can use [array spread](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax#spread_in_array_literals) with `[.slice()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/slice)`.

```
const newPlayers = [
  ...players.slice(0, INDEX_TO_REPLACE),
  newPlayer,
  ...players.slice(INDEX_TO_REPLACE + 1),
]
```

We take slices of the array before and after the target `INDEX_TO_REPLACE`. Using array spread we concatenate these slices around the `newPlayer` we want to add. This results in a new array with just our target index replaced. This does create 2 intermediary array slices. So if your array is sufficiently large this *could* be a performance hit.

## 3. Create an empty array of X items

The `[_.times()](https://lodash.com/docs/4.17.15#times)` Lodash utility function is super helpful for quickly initializing an array of a specific length with values.

Since using Lodash of course breaks one of our rules, we can use `[Array.from](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/from)` to accomplish the same thing.

This looks like we’re breaking another one of our rules because we’re just using `Array.from` (added in ES2015). But I’m allowing it because of the `{ length: 5}` trick. `Array.from` accepts any *array-like* object, which is an object with a `length` property and indexed elements. Our `{length: 5}` object satisfies both requirements.

The second argument to `Array.from` is a `mapFn`. Since this `{length: 5}` trick creates an array with `undefined` values, the first argument in `mapFn` (the value) is useless. We only want the second argument (the `index`). We use the underscore (`_`) as a placeholder name for the function argument we do not need.

The `[_.mapValues](https://lodash.com/docs/4.17.15#mapValues)` helper is another useful function from Lodash. It creates a new object with the same keys as the original, but with new mapped values. By combining `[Object.entries()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/entries)`, `[.map()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map)`, and `[Object.fromEntries()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/fromEntries)`, we can build this ourselves.

Let’s break it down real quickly. First, `Object.entries` converts the object to an array of `[teamId, teamInfo]` pairs (called entries). Then we map over the array of pairs to return a new array of pairs. By the way, we also use [array destructuring](https://www.benmvp.com/blog/learning-es6-destructuring/) to create the `teamId` and `teamInfo` function arguments. The `teamId` remains the first item in the pair, but now the second item is the `teamInfo` with the `teamId` merged in. Lastly, `Object.fromEntries` transforms our array of `[key, value]` pairs into our resultant object.

This same algorithm can be used to replicate `[_.mapKeys](https://lodash.com/docs/4.17.15#mapKeys)` as well. Instead of changing the 2nd item in the `[key, value]` pair, we change the first (the `key`). In fact, there’s nothing stopping us from changing *both* items in the `[key, value]` pair!

Again, there are a number of intermediary arrays that get created in this transformation. But if your object isn’t huge, it should be fine.

## 6. Create an array of unique values

We can create a duplication-free version of an array using the combination of the `[Set](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Set)` object and array spread. No more need for `[_.uniq](https://lodash.com/docs/4.17.15#uniq)`!

Converting the `AGES` array into a `Set` object strips out all duplicates because a `Set` can only store unique values. We then convert the `Set` back into an array by spreading it (using `...`) into an array literal because it is a [built-in iterable](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Iteration_protocols).

A similar algorithm can be used to recreate `[_.union](https://lodash.com/docs/4.17.15#union)` which creates an array of unique values from multiple arrays.

The difference is that we spread `GROUP_A` & `GROUP_B` together to create a single, concatenated array before constructing a `Set` object from it.

The `[_.pick](https://lodash.com/docs/4.17.15#pick)` and `[_.omit](https://lodash.com/docs/4.17.15#omit)` Lodash helpers frequently come in handy. They are opposites of each other. The `_.pick` function creates an object with just the specified keys **picked** from the original. While the `_.omit` function creates an object **omitting** the specified keys. We basically use the same algorithm as [mapping values of an object](https://www.benmvp.com/blog/9-single-statement-javascript-algorithms-common-data-transformations/), except we use `.filter()` (plus `[.includes()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/includes)`) instead of `.map()`.

The difference between `pick` vs `omit` is the negation (`!`) of `IDS.includes(teamId)` within `.filter()`. By filtering down the entries to only the teams listed (or not listed) in `IDS`, the object created by `Object.fromEntries` has (or excludes) the selected teams.

What do you think of these? I’m sure there are many more single-statement data transformers, but these are the ones I use frequently and find the most helpful. I would love to see what other ones you use, so feel free to reach out to me on Twitter at [@benmvp](https://twitter.com/benmvp).

Keep learning my friends. 🤓