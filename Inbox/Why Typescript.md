# Why Typescript

Source: Notes
Status: Unprocessed

Types are foundational to JavaScript; they influence everything about the way you write your programs. But JavaScript’s dynamic type system often makes it easy to introduce bugs by mistakenly referencing variables with the wrong type. How many of us have experienced the dreaded Undefined is not an object error?
TypeScript was invented to stop these problems from happening before you even run your code. It uses JavaScript as a base, adds some extra syntax to define types, and provides a tool to transform your code back into JavaScript. The result is a hybrid of a compiler and a linter. TypeScript checks your code as you write it to make sure the types are correct, and then compiles it to whatever version of JavaScript you need to support.

TypeScript is superset of JavaScript, meaning that any JavaScript program is also a valid TypeScript program. This allows TypeScript programs to import and use JavaScript code, meaning you don’t have to rewrite your entire app right away when you start using TypeScript. Other developer tools, like Babel or Webpack, can be configured to process TypeScript files, and new JavaScript runtimes like Deno support TypeScript natively.

There’s a reason TypeScript is so popular. Developers who use it love the type safety it provides while still giving them the flexibility of JavaScript. Here are some reasons why you might find TypeScript useful.

## Type Validation

TypeScript is a static validation tool, like ESLint. The goal of any kind of validation tool is to increase your confidence that the program you are writing behaves the way it is supposed to and doesn’t have unexpected bugs. Since TypeScript understands the relationships between the types in your codebase, using it well can eliminate entire classes of errors and issues. As you write your code, TypeScript can give you hints to help you write your code correctly. TypeScript doesn’t replace ESLint or automated tests, but it can give you more confidence that your code is working correctly without having to run your code.
CompilerTypeScript is also a compiler. Like Babel, it can transform TypeScript and JavaScript code to support different features for older JavaScript engines. If you need to support an older browser like IE11, TypeScript can transform your code so it will work correctly. If you only need to support newer engines, the compiler will strip out the type data and leave you with valid JavaScript.
It’s important to remember that TypeScript is not a runtime language - all of the types are removed at compile time. It’s purpose is to encourage you, the developer, to use the types to add checks to your program so you have fewer errors and bugs.

### JavaScript Superset

TypeScript can be used as a progressive enhancement to JavaScript. It’s a superset of JavaScript, so any JavaScript program is valid TypeScript. This includes the massive amount of packages available on NPM. However, without proper type annotations, most JavaScript programs will have type errors. You can configure the compiler to ignore type errors on JavaScript programs as you transition your codebase from JavaScript to TypeScript.
Since TypeScript is a superset of JavaScript, many of the quirks of JavaScript are present in TypeScript programs. It might not always be possible to add the appropriate type annotations to something. TypeScript provides escape hatches, like the any type and // @ts-ignore which turn off the type checker for those parts of your code. This is just like writing regular JavaScript, so you can still enjoy the flexibility of dynamic types. However, it also means you can’t guarantee that your program will never have a type error. If you want a truly strongly typed language that compiles to JavaScript, you can use languages like ReScript or Elm.

### Communication and Documentation

Coming into a brand new codebase can be daunting, especially if you don’t know how all the pieces connect together or how something is supposed to behave. Adding type annotations to your code removes a lot of the guess work in figuring out how a program works and serves as guide for anyone trying to work in your codebase.
TypeScript can also help with refactoring. Without TypeScript, you have no way of knowing all of the different places that need to be updated when you change something. TypeScript checks your change against any other files that might be affected and warns you if anything is broken. All that’s left is to follow each warning and make the appropriate change without needing to run your code.

### The Bottom Line

In short, TypeScript will help you write code with less errors by checking your code before you run it. Adding the types might take a little bit of work, but it definitely pays off in the long run.