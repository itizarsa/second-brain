# The complete guide to working with strings in modern JavaScript

Source: Article
Status: Unprocessed
URL: https://www.baseclass.io/guides/string-handling-modern-js

![https://www.baseclass.io/guides/string-handling-modern-js/og_image_large.png](https://www.baseclass.io/guides/string-handling-modern-js/og_image_large.png)

---

![og_image_large.png](The%20complete%20guide%20to%20working%20with%20strings%20in%20mode%20df0985c11474450795dcc9f86a69e8c4/og_image_large.png)

The complete guide to

This guide is intended to cover everything you need to know about creating, manipulating and comparing strings in JavaScript.

extra tips

and

common issues

sections along the way will hopefully teach you something new, and help you to avoid common mistakes.

If I've missed anything, please [let me know](https://twitter.com/DaveJSaunders) and I'll add it!

Remember to bookmark this page to refer to later!

## Contents

- [Splitting a string](https://www.baseclass.io/guides/string-handling-modern-js)
- [Comparing strings](https://www.baseclass.io/guides/string-handling-modern-js)
- [Multi-line strings](https://www.baseclass.io/guides/string-handling-modern-js)
- [Padding strings](https://www.baseclass.io/guides/string-handling-modern-js)
- [Changing the case of a string](https://www.baseclass.io/guides/string-handling-modern-js)
- [Removing whitespace](https://www.baseclass.io/guides/string-handling-modern-js)
- [Replacing characters in a string](https://www.baseclass.io/guides/string-handling-modern-js)
- [🔥 Get more like this](https://www.baseclass.io/guides/string-handling-modern-js)

## Creating strings

There are fundamentally two categories of strings in JavaScript; string primitives and String objects.

### Primitives

String primitives are created like this:

```
let example1 = "BaseClass"// or let example2 = String("BaseClass")
```

In almost all cases, you should use one of these methods to create a new string.

You can use either single quotes (`' '`) or double-quotes (`" "`) when defining a string literal.

### Objects

You can create a String *object* using the `new` keyword.

The only real advantage that an object has over a string primitive is that you can attach additional properties to it:

```
let website = new String("BaseClass")
website.rating = "great!"
```

There are very few cases where this is useful though. In almost all cases, you should create a string *primitive*.

## Template Literals

### Basic Template Literals

Template Literals allow you to combine variables and text into a new string using a more readable syntax.

Instead of double or single-quotes, enclose the string in back-ticks and reference variables using the syntax `${variableName}`:

You can also include expressions in a Template Literal:

Brower support for Template Literals is now very good:

### Tagged Templates

Tagged Templates allow you to create a function that parses a Template Literal.

This can be really powerful, and is most clearly demonstrated by an example:

Imagine we have a function called `censor()` that removes any offensive words in a string entered by a user.

When we want to censor a string, we could manually call `censor()` on every user entered value:

Or, we could use Tagged Templates.

This allows us to write a function that accepts the string values from the Template Literal, and all of the expressions used in the template:

Note that in the last line we 'tag' the string with our function by adding it before the Template Literal, rather than explicitly calling the `censorStrings()` function.

This means we can now manipulate the template literal and the values inside it.

Now we have access to the Template Literal and the individual arguments, we can sensor every variable used in the string:

Finally, our tagging function has to return the finished string.

To do this, we simply interleave the original string array and the array of (modified) inputs in to a *new* array.

Here we do that using `.reduce()`:

Our tagging function is now complete, and can be used anywhere we need to censor user inputs:

### Raw Strings

`String.raw` is a pre-defined [tag function](https://www.baseclass.io/guides/string-handling-modern-js).

It allows you to access the string without interpreting any backslash escape sequences.

For example, when using a string containing `\n` with `String.raw`, instead of getting a new line in the string you would get the actual `\` and `n` characters:

This makes it useful for (among other things) writing strings in which you'd usually have to escape lots of backslash characters, such as file paths:

## Combining strings

### Concatenating strings

You can combine (or 'concatenate') multiple strings to create a new one using the `+` symbol:

This can also be used to split string creation over multiple lines for readability:

You can also concatenate strings with variables (non-string variables will be converted to strings):

To create a new string by adding to the end of an existing one, use `+=`:

### Repeating a string

The `repeat()` method returns a new string, which contains the original string repeated a number of times:

You can use this in the following browsers:

### Joining strings

You can combine an array of strings into one using the `.join()` method on the array.

The default is to separate the items with a comma:

You can also specify the string used to separate the elements:

Passing an empty string to `string.join` will join elements with nothing between them:

When `toString()` is used on an array, it also returns a comma-separated list of the strings.

## Splitting a string

You can split a string in to an array using the `split()` method.

Common use cases for this are:

Turning a sentence into an array of words, by splitting it on spaces:

.. or splitting a multi-line string into individual lines:

You can also limit the number of items you would like back from `split()`, by passing an optional second parameter:

## Comparing strings

### Equality

When you know you are comparing two string primitives, you can use either the `==` or `===` operators:

If you are comparing a string primitive to something that is *not* a string, `==` and `===` behave differently.

When using the `==` operator, the non-string will be coerced to a string. That means that JavaScript will try and make it a string before comparing the values.

For a strict comparison, where non-strings are not coerced to strings, use `===`:

The same is true of the not-equal operators, `!=` and `!==`:

If you're not sure what to use, prefer strict equality using `===`.

### Case sensitivity

When a case-insensitive comparison is required, it is common to convert both strings to upper or lowercase and compare the result.

Sometimes you need more control over the comparison, though. See the next section for that..

### Handling diacritics

Diacritics are modifications to a letter, such as é or ž.

You may wish to specify how these are handled when comparing two strings.

For example, in some languages it is common practice to exclude accents from letters when writing in uppercase.

If you need a case-insensitive comparison, simply converting two strings to the same case first using `toUpperCase()` or `toLowerCase()` would not account for this addition/removal of accents, and might not give you the result you are expecting.

When you need more fine-grained control of the comparison, use  [localeCompare](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/localeCompare) instead:

The `localeCompare` method allows you to specify the 'sensitivity' of the comparison.

Here we used a 'sensitivity' of `base` to compare the strings using their 'base' characters (meaning it will ignore case and accents).

This is supported in the following browsers:

### Greater/less than

When comparing strings using the `<` and `>` operators, JavaScript will compare each character in 'lexicographical order'.

That means that they are compared letter by letter, in the order they would appear in a dictionary:

### True or false strings

Empty strings in JavaScript are considered false when compared with the `==` operator (but not when using `===`)

Strings with a value are 'true', so you can do things like this:

## Sorting strings

### Simple Array.sort()

The simplest way to sort an array of strings is to use the `Array.sort()` method:

### localeCompare

Using `localeCompare` as the sorting function allows you to compare strings in a case-insensitive way:

You can also use `localeCompare` to ignore diacritics (like accents) while sorting strings. See the [Handling Diacritics](https://www.baseclass.io/guides/string-handling-modern-js) section for more information.

## Multi-line strings

You can add new lines in a string using `\n`:

In a Template Literal, new lines are respected within the backticks:

## Padding strings

You can add whitespace to the start or end of a string until it reaches a specified length using `padStart()` or `padEnd()`:

Instead of whitespace, you can pad the target string with another string, by passing it as the second parameter.

That string will be repeated until the target length is reached (the string will be truncated if it does not fit evenly into the required padding):

This is supported by all modern browsers:

## Extracting part of a String

### Substrings

These methods take the index of the first character you wish to extract from the string.

They return everything from that character to the end of the string:

The second (optional) argument is the character at which you'd like to stop.

This final character is *not included* in the output:

So, which one should you use?

They are very similar, but with some subtle differences:

- If the end value is higher than the start value, `substring()` will 'correct' them by swapping them, but `slice()` will just return an empty string.
- `substring()` treats a negative index as `0`. With `slice()`, you can use a negative number to count backwards from the *end* of the string. For example, `.slice(-3)` will return the last 3 characters of the string.

### Single characters

The `charAt()` method returns a specific character from the string (remember, indexes are 0-based):

You can also treat a string as an array, and access it directly like this:

## Changing the case of a string

You can make a string all-caps like this:

Or all lowercase like this:

## Removing whitespace

The following methods will remove all spaces, tabs, non-breaking spaces and line ending characters (e.g. `\n`) from relevant part the string:

## Searching for text in a string

### Find the position of a substring

You can search for a string within another string using `indexOf()`.

This will return the position of *first occurrence* of the search term within the string, or `-1` if the string is not found:

You can also use the regular expression method `search()` to do the same thing:

To search for the *last occurrence* of a search term, use `lastIndexOf()`:

All of these methods will return `-1` if the search term is not found in the target string.

### Starts/Ends with

You can use the `indexOf()` methods above to check whether a string begins with, or ends with, a search term.

However, ES6 added specific methods for this:

### Includes

If you don't care about the specific position of the substring, and only care whether it is in the target string *at all*, you can use `includes()`:

### Regular Expressions

To find the first occurrence of a regular expression match, use `.search()`.

To return an array containing all matches of a regular expression, use `match()`, with the `/g` (global) modifier:

(using `match()` without the `/g` modifier will return only the first match, and some additional properties such as the index of the result in the original string, and any named capturing groups)

If you need more details about each match, including their index in the original string, you can use `matchAll`.

This method returns an iterator, so you can use a `for...of` loop over the results. You must use a regular expression with the `/g/` modifier with `matchAll()`:

## Replacing characters in a string

You can use `replace()` to replace certain text in a string.

The first argument to `replace()` is the text to find and replace, the second is the text to replace it with.

Passing a string as the first argument replaces *only the first instance of the term*:

If you want to replace *all* instances of the text, you can pass a regular expression with the 'greedy' modifier (`/g`) as the first argument:

ES2021 added `replaceAll()`, to make replacing all instances of a term easier:

You can use this if you only need to support very recent browsers: