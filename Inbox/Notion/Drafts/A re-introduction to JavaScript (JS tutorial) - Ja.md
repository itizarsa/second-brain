# A re-introduction to JavaScript (JS tutorial) - JavaScript | MDN

Status: Unprocessed
URL: https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript

![https://developer.mozilla.org/mdn-social-share.0ca9dbda.png](https://developer.mozilla.org/mdn-social-share.0ca9dbda.png)

---

![mdn-social-share.0ca9dbda.png](A%20re-introduction%20to%20JavaScript%20(JS%20tutorial)%20-%20Ja%20fcee19c14d1343f8a97fc4a489a8d1b4/mdn-social-share.0ca9dbda.png)

Why a re-introduction? Because [JavaScript](https://developer.mozilla.org/en-US/docs/Glossary/JavaScript) is notorious for being misunderstood. It is often derided as being a toy, but beneath its layer of deceptive simplicity, powerful language features await. JavaScript is now used by an incredible number of high-profile applications, showing that deeper knowledge of this technology is an important skill for any web or mobile developer.

It's useful to start with an overview of the language's history. JavaScript was created in 1995 by Brendan Eich while he was an engineer at Netscape. JavaScript was first released with Netscape 2 early in 1996. It was originally going to be called LiveScript, but it was renamed in an ill-fated marketing decision that attempted to capitalize on the popularity of Sun Microsystem's Java language — despite the two having very little in common. This has been a source of confusion ever since.

Several months later, Microsoft released JScript with Internet Explorer 3. It was a mostly-compatible JavaScript work-alike. Several months after that, Netscape submitted JavaScript to [Ecma International](https://www.ecma-international.org/), a European standards organization, which resulted in the first edition of the [ECMAScript](https://developer.mozilla.org/en-US/docs/Glossary/ECMAScript) standard that year. The standard received a significant update as [ECMAScript edition 3](https://www.ecma-international.org/publications/standards/Ecma-262.htm) in 1999, and it has stayed pretty much stable ever since. The fourth edition was abandoned, due to political differences concerning language complexity. Many parts of the fourth edition formed the basis for ECMAScript edition 5, published in December of 2009, and for the 6th major edition of the standard, published in June of 2015.

**Note:** Because it is more familiar, we will refer to ECMAScript as "JavaScript" from this point on.

Unlike most programming languages, the JavaScript language has no concept of input or output. It is designed to run as a scripting language in a host environment, and it is up to the host environment to provide mechanisms for communicating with the outside world. The most common host environment is the browser, but JavaScript interpreters can also be found in a huge list of other places, including Adobe Acrobat, Adobe Photoshop, SVG images, Yahoo's Widget engine, server-side environments such as [Node.js](https://nodejs.org/), NoSQL databases like the open source [Apache CouchDB](https://couchdb.apache.org/), embedded computers, complete desktop environments like [GNOME](https://www.gnome.org/) (one of the most popular GUIs for GNU/Linux operating systems), and others.

JavaScript is a multi-paradigm, dynamic language with types and operators, standard built-in objects, and methods. Its syntax is based on the Java and C languages — many structures from those languages apply to JavaScript as well. JavaScript supports object-oriented programming with object prototypes, instead of classes (see more about [prototypical inheritance](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Inheritance_and_the_prototype_chain) and ES2015 [classes](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes)). JavaScript also supports functional programming — because they are objects, functions may be stored in variables and passed around like any other object.

Let's start off by looking at the building blocks of any language: the types. JavaScript programs manipulate values, and those values all belong to a type. JavaScript's types are:

- [Number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures)
- [BigInt](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures)
- [String](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures)
- [Boolean](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures)
- `[Function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function)`
- [Object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures)
- [Symbol](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures) (new in ES2015)

... oh, and [undefined](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures) and [null](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures), which are ... slightly odd. And `[Array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)`, which is a special kind of object. And `[Date](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date)` and `[RegExp](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp)`, which are objects that you get for free. And to be technically accurate, functions are just a special type of object. So the type diagram looks more like this:

- [Number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures)
- [BigInt](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures)
- [String](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures)
- [Boolean](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures)
- [Symbol](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures) (new in ES2015)
- [undefined](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures)

And there are some built-in `[Error](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Error)` types as well. Things are a lot easier if we stick with the first diagram, however, so we'll discuss the types listed there for now.

ECMAScript has two built-in numeric types: **Number** and **BigInt**.

The Number type is a [double-precision 64-bit binary format IEEE 754 value](https://en.wikipedia.org/wiki/Double_precision_floating-point_format) (numbers between -(2^53 − 1) and 2^53 − 1). And where this article and other MDN articles refer to “integers”, what’s usually meant is a *representation* of an integer using a Number value. But because such Number values aren’t real integers, you have to be a little careful. For example:

```
console.log(3 / 2);             // 1.5, not 1
console.log(Math.floor(3 / 2)); // 1

```

So an *apparent integer* is in fact *implicitly a float*.

Also, watch out for stuff like:

```
0.1 + 0.2 == 0.30000000000000004;

```

In practice, integer values are treated as 32-bit ints, and some implementations even store it that way until they are asked to perform an instruction that's valid on a Number but not on a 32-bit integer. This can be important for bit-wise operations.

The standard [arithmetic operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators) are supported, including addition, subtraction, modulus (or remainder) arithmetic, and so forth. There's also a built-in object that we did not mention earlier called `[Math](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math)` that provides advanced mathematical functions and constants:

```
Math.sin(3.5);
var circumference = 2 * Math.PI * r;

```

You can convert a string to an integer using the built-in `[parseInt()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/parseInt)` function. This takes the base for the conversion as an optional second argument, which you should always provide:

```
parseInt('123', 10); // 123
parseInt('010', 10); // 10

```

In older browsers, strings beginning with a "0" are assumed to be in octal (radix 8), but this hasn't been the case since 2013 or so. Unless you're certain of your string format, you can get surprising results on those older browsers:

```
parseInt('010');  //  8
parseInt('0x10'); // 16

```

Here, we see the `[parseInt()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/parseInt)` function treat the first string as octal due to the leading 0, and the second string as hexadecimal due to the leading "0x". The *hexadecimal notation is still in place*; only octal has been removed.

If you want to convert a binary number to an integer, just change the base:

```
parseInt('11', 2); // 3

```

Similarly, you can parse floating point numbers using the built-in `[parseFloat()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/parseFloat)` function. Unlike its `[parseInt()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/parseInt)` cousin, `parseFloat()` always uses base 10.

You can also use the unary `+` operator to convert values to numbers:

```
+ '42';   // 42
+ '010';  // 10
+ '0x10'; // 16

```

A special value called `[NaN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/NaN)` (short for "Not a Number") is returned if the string is non-numeric:

```
parseInt('hello', 10); // NaN

```

`NaN` is toxic: if you provide it as an operand to any mathematical operation, the result will also be `NaN`:

```
NaN + 5; // NaN

```

You can reliably test for `NaN` using the built-in `[Number.isNaN()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/isNaN)` function, [which behaves just as its name implies](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/isNaN):

```
Number.isNaN(NaN); // true
Number.isNaN('hello'); // false
Number.isNaN('1'); // false
Number.isNaN(undefined); // false
Number.isNaN({}); // false
Number.isNaN([1]) // false
Number.isNaN([1,2]) // false

```

But don’t test for `NaN` using the global `[isNaN()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/isNaN)` function, [which has unintuitive behavior](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/isNaN):

```
isNaN('hello'); // true
isNaN('1'); // false
isNaN(undefined); // true
isNaN({}); // true
isNaN([1]) // false
isNaN([1,2]) // true

```

JavaScript also has the special values `[Infinity](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Infinity)` and `-Infinity`:

```
 1 / 0; //  Infinity
-1 / 0; // -Infinity

```

You can test for `Infinity`, `-Infinity` and `NaN` values using the built-in `[isFinite()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/isFinite)` function:

```
isFinite(1 / 0); // false
isFinite(-Infinity); // false
isFinite(NaN); // false

```

**Note:** The `[parseInt()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/parseInt)` and `[parseFloat()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/parseFloat)` functions parse a string until they reach a character that isn't valid for the specified number format, then return the number parsed up to that point. However the "+" operator converts the string to `NaN` if there is an invalid character contained within it. Just try parsing the string "10.2abc" with each method by yourself in the console and you'll understand the differences better.