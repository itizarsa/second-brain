# JavaScript Questions and Answers

Source: Article
Status: Unprocessed
URL: https://riyajain.hashnode.dev/most-frequent-javascript-questions-and-answers

[https://hashnode.com/utility/r?url=https%3A%2F%2Fcdn.hashnode.com%2Fres%2Fhashnode%2Fimage%2Fupload%2Fv1623501855631%2FHTt0EGj3U.png%3Fw%3D1200%26h%3D630%26fit%3Dcrop%26crop%3Dentropy%26auto%3Dcompress%2Cformat%26format%3Dwebp%26fm%3Dpng](https://hashnode.com/utility/r?url=https%3A%2F%2Fcdn.hashnode.com%2Fres%2Fhashnode%2Fimage%2Fupload%2Fv1623501855631%2FHTt0EGj3U.png%3Fw%3D1200%26h%3D630%26fit%3Dcrop%26crop%3Dentropy%26auto%3Dcompress%2Cformat%26format%3Dwebp%26fm%3Dpng)

---

[JavaScript%20Questions%20and%20Answers%2089841ee7c84d4f9c9da19f6b52c72c5a/image](JavaScript%20Questions%20and%20Answers%2089841ee7c84d4f9c9da19f6b52c72c5a/image)

Hi All, In this article we'll cover some common JavaScript interview questions and answers.

> "Small steps can lead to big changes."
> 

🚀**What is hoisting? Explain with example? Temporal Dead Zone?**

![JavaScript%20Questions%20and%20Answers%2089841ee7c84d4f9c9da19f6b52c72c5a/IqeFzralF.png](JavaScript%20Questions%20and%20Answers%2089841ee7c84d4f9c9da19f6b52c72c5a/IqeFzralF.png)

🎈Hoisting is the JavaScript interpreter’s action of moving all variable and function declarations to the top of the current scope.

🎈Basically, when JavaScript compiles all of your code, all variable declarations using var are lifted to the top of their functional/local scope (if declared inside a function) or to the top of their global scope (if declared outside of a function) regardless of where the actual declaration has been made. This is what we mean by “hoisting”.

🎈A key thing to note is that the only thing that gets moved to the top is the variable declarations, not the actual value given to the variable.

Variable declaration and initialization occur in the following sequence:

**Declaration –> Initialization/Assignment –> Usage**

```
// Variable lifecycle
let x;                 // Declaration
x = “hoisting”;        // Assignment
console.log(x);        // Usage

```

However, since JavaScript permits both declaration and initialization of variables simultaneously, this is the most used pattern:

Most importantly, you should always remember that the JavaScript declares the variable first in the background. Then, initializing them. Thus, it is also good to know that the processing of variable declarations takes place before the execution of any code. However, until the execution of code assigning them takes place the undeclared variables do not exist in JavaScript.

🎈Therefore, when the assignment is executed, a value assigned to an undeclared variable implicitly creates it as a global variable. This specifies that all undeclared variables are global variables.

```
// hoisting
function Hoisting(){
  x = 100;
  let y = 200;
}
Hoisting();
console.log(x); // 100
console.log(y); // Reference Error: y is not defined

```

🎈In the above code sample, there is a function called Hoisting(). Thus, we have a variable which we didn’t declare using let/var/const and a let variable y. The assigning of the undeclared variable to the global scope is done by JavaScript. But for variable y, we get a ReferenceError.

🎈**Hoisting in ES5**

```
console.log(car);    // undefined
var car = ‘BMW’;

```

But the interpreter sees this differently, which is as follows:

```
//how interpreter sees the above code
var car;
console.log(car); // undefined
car = ‘BMW’;

```

**Hoisting in ES6**

```
console.log(num);
let num = 003;         // ReferencError: num is not defined

```

🎈In the var keyword, we expect the output of the log to be undefined. However, since the let in es6 doesn’t take allow using undeclared variables, the interpreter throws a Reference error explicitly. This makes sure that we always declare our variable first.

> Variables and constants declared with let or const are not hoisted! JavaScript Initializations are Not Hoisted JavaScript only hoists declarations, not initializations.
> 

✍**Temporal Dead zone**

🎈The term to describe the state where variables are un-reachable. They are in scope, but they aren't declared.

🎈The let and const variables exist in the TDZ from the start of their enclosing scope until they are declared.

🎈You could also say that the variables exist in the TDZ from the place they get bound (when the variable gets bound to the scope it's inside) until it is declared (when a name is reserved in memory for that variable).

```
{
     // This is the temporal dead zone for the age variable!
    // This is the temporal dead zone for the age variable!
    // This is the temporal dead zone for the age variable!
     // This is the temporal dead zone for the age variable!
    let age = 2; // we got there! No more TDZ
    console.log(age);
}

```

🎈You can see above that if I accessed the age variable earlier than its declaration, it would throw a ReferenceError. Because of the TDZ.

🎈But var won't do that. var is just default initialized to undefined unlike the other declaration.

🚀**Difference between call, apply and bind. Give example**

They are some of the most important and often-used concepts in JavaScript and are very closely related to the this keyword.

![JavaScript%20Questions%20and%20Answers%2089841ee7c84d4f9c9da19f6b52c72c5a/WJyAXGb5N.png](JavaScript%20Questions%20and%20Answers%2089841ee7c84d4f9c9da19f6b52c72c5a/WJyAXGb5N.png)

✍**The** call() **method calls a function with a given this value and arguments provided individually.**

**Syntax: func.call([thisArg[, arg1, arg2, ...argN]])** thisArg — This is optional. It’s the value to use as this when calling func. arg1, arg2, ...argN— Optional arguments for the function.

```
'use strict'

let name = {
  firstName :'Riya',
  lastName :'Jain'
}
let name2 = {
  firstName :'Kashish',
  lastName :'Jain'
}
let printFullName = function(hometown, state){
 console.log(this.firstName+ " "+ this.lastName + " from "+ hometown + ", "+ state );
}

printFullName.call(name, "Mumbai", "Maharashtra");
// Riya Jain from Mumbai, Maharashtra

printFullName.call(name2, "Indore", "MadhyaPradesh");
// Kashish Jain from Indore, MadhyaPradesh

```

**Practical Applications** :📝

🎈 Using call to invoke a function and specifying the context for 'this' In the example below, when we call print, the value of this will be bound to object person.

```
const person = {
    name: 'Riya',
    age: 'X'
};
function print() {
  const reply = [this.name, 'is', this.age, 'years old.'].join(' ');
  console.log(reply);
}
print.call(person);
//Riya is X years old.

```

🎈 Using call to invoke a function and without specifying the first argument In the example below, we invoke the display function without passing the first argument. If the first argument is not passed, the value of this is bound to the global object.

```
var name = 'Riya';
function display() {
  console.log('Your name: ', this.name);
}
display.call();
// Your name:  Riya

Caution: In strict mode, the value of this will be undefined.

'use strict'

var name = 'Riya';
function display() {
  console.log('Your name: ', this.name);
}
display.call();
//Uncaught TypeError: Cannot read property 'name' of undefined

```

> Using a call method we can do function/method borrowing, we can borrow functions from other objects and use it with the data of some other objects
> 

✍**The** apply**() method calls a function with a given this value, and arguments provided as an array (or an array-like object).**

**Syntax** :func.apply(thisArg, [ argsArray])

> apply is very similar to call(), except for the type of arguments it supports.
> 

With apply, you can write a method once, and then inherit it in another object, without having to rewrite the method for the new object.

**Practical Applications** 📝

🎈Using apply and built-in functions

```
// Min/Max number in an array
const numbers = [9, 8, 1, 2, 3, 5, 6, 7];
// Using Math.min/Math.max apply
let max = Math.max.apply(null, numbers);
console.log(max); //9
// This about equal to Math.max(numbers[0], ...)
// or Math.max(5, 6, ...)
let min = Math.min.apply(null, numbers);
console.log(min); //1

```

✍**The** bind() **method returns a new function, when invoked, has its this sets to a specific value.**

func.bind(thisArg[, arg1[, arg2[, ...]]])

🎈The bind method looks exactly the same as the call method but the only difference is instead of directly calling this method here, the bind method binds this method with the object and returns a copy of that method. And will return a function.

🎈So there is a catch over here, it doesn’t directly call that method rather it will return a method that can be called later. This is basically used to just bind and keep the copy of that method and use it later.

**Practical Applications**📝

🎈Using bind() to borrow methods from a different object

```
let runner = {
    name: 'Runner',
    run: function(speed) {
        console.log(this.name + ' runs at ' + speed + ' mph.');
    }
};
let flyer = {
    name: 'Flyer',
    fly: function(speed) {
        console.log(this.name + ' flies at ' + speed + ' mph.');
    }
};
let run = runner.run.bind(flyer, 20);
run();
// Flyer runs at 20 mph.

```

🎈 Using JavaScript bind() for function binding (with setTimeout())🕥

For example:

```
let person = {
    firstName: 'John Doe',
    getName: function() {
        console.log(this.firstName);
    }
};
setTimeout(person.getName, 1000); //undefined
let f = person.getName;
setTimeout(f, 1000); //undefined

```

The this inside the setTimeout() function is set to the global object in non-strict mode and undefined in the strict mode.Therefore, when the callback person.getName is invoked, the name does not exist in the global object, it is set to undefined.

To fix the issue, you can wrap the call to the person.getName method in an anonymous function, like this:

```
setTimeout(function () {
    person.getName();
}, 1000);
// "John Doe

```

**Or you can use the bind() method:**

```
let f = person.getName.bind(person);
setTimeout(f, 1000);
// "John Doe"

```

🚀**What is closure and what are the advantages of using closure?**

✍A closure is a combination of a function bundled together (enclosed) with references to its surrounding state (the lexical environment). In other words, a closure gives you access to an outer function’s scope from an inner function. In JavaScript, closures are created every time a function is created, at function creation time.

![JavaScript%20Questions%20and%20Answers%2089841ee7c84d4f9c9da19f6b52c72c5a/b9SZ9HB2y.png](JavaScript%20Questions%20and%20Answers%2089841ee7c84d4f9c9da19f6b52c72c5a/b9SZ9HB2y.png)

✍Uses: module design, currying, functions like once, data hiding and encapsulation, settimeout, memoize, and many others.

```
function developer(){
          var name = 'riya';
           function displayName(){
              alert(name);
           }
          return displayName;
  }
var devName ='developer();
devName();

```

🚀**Event bubbling, event capturing/trickling, and event delegation**

✍**Event Bubbling**

![JavaScript%20Questions%20and%20Answers%2089841ee7c84d4f9c9da19f6b52c72c5a/X9qAia-YR.png](JavaScript%20Questions%20and%20Answers%2089841ee7c84d4f9c9da19f6b52c72c5a/X9qAia-YR.png)

🎈When you click on the button, the event passes from inner event target (Button whose id is the child) to Document. Click event pass in the following order: button-->div-->body-->html-->document

🎈If you want to stop the event bubbling, this can be achieved by the use of the event.stopPropagation() method.

✍**Event capturing/trickling**:

![JavaScript%20Questions%20and%20Answers%2089841ee7c84d4f9c9da19f6b52c72c5a/mUoom6JUt.png](JavaScript%20Questions%20and%20Answers%2089841ee7c84d4f9c9da19f6b52c72c5a/mUoom6JUt.png)

🎈When you click on the button, the event passes from parent (document) to event target(Button whose id is the child). Click event pass in the following order: document-->html-->body-->div-->button

🎈Event Capturing is the event starts from top element to target element. Modern browser doesn’t support event capturing by default but we can achieve that by code in JavaScript.We can use third optional argument of addEventListner to set true to enable event capturing in the parent div.

✍**Event Delegation**: a method of handling events for multiple elements via an event listener on one parent element. [dev.to/coderarchive/event-delegation-in-js-..](https://dev.to/coderarchive/event-delegation-in-js-1aff)

✍For more explanation: [dmitripavlutin.com/javascript-event-delegat..](https://dmitripavlutin.com/javascript-event-delegation/)

🚀**Explain with examples of a deep and shallow copy.**

![JavaScript%20Questions%20and%20Answers%2089841ee7c84d4f9c9da19f6b52c72c5a/W2UesJ0Yf.png](JavaScript%20Questions%20and%20Answers%2089841ee7c84d4f9c9da19f6b52c72c5a/W2UesJ0Yf.png)

✍**Shallow copy means copy only the reference.**

🎈**Example:**Here there are two objects originalObject and clonedObject, clonedObject has a reference of originalObject. If one of these objects is modified (from originalObject or clonedObject), we can observe the change in the value of the other.

![JavaScript%20Questions%20and%20Answers%2089841ee7c84d4f9c9da19f6b52c72c5a/MQPYMKjIZ.png](JavaScript%20Questions%20and%20Answers%2089841ee7c84d4f9c9da19f6b52c72c5a/MQPYMKjIZ.png)

🎈However, there is a workaround to copy objects wi thout reference. The Object.assign() method copies enumerable properties from a source object to a target object. Further, this can be used only if the object/array contains primitive type values.

```
let originalObject = {name: "apple"};
let clonedObject = Object.assign({}, originalObject);

```

![JavaScript%20Questions%20and%20Answers%2089841ee7c84d4f9c9da19f6b52c72c5a/Y1xO14ns0.png](JavaScript%20Questions%20and%20Answers%2089841ee7c84d4f9c9da19f6b52c72c5a/Y1xO14ns0.png)

🎈Here, if you modify the value of any property of variable originalObject or clonedObject, it won’t affect the other.

🎈So Object. assign() method will copy up to the first level. If the object contains any nested object or array then the internally copied reference type value will refer to its memory address.

✍**Deep Copy: It simply creates a duplicate of all the properties of the source object into the target object**

🎈 In other words, both the primitive type and reference type properties will be allocated to new memory locations.

## 

![JavaScript%20Questions%20and%20Answers%2089841ee7c84d4f9c9da19f6b52c72c5a/OqDkY0tPB.png](JavaScript%20Questions%20and%20Answers%2089841ee7c84d4f9c9da19f6b52c72c5a/OqDkY0tPB.png)

🚀**How Javascript code is executed?**

A perfect explanation: [youtube.com/watch?v=iLWTnMzWtj4](https://www.youtube.com/watch?v=iLWTnMzWtj4)

🚀**Explain features of ES6.**

✍**Template Literals in ES6**

In ES6, we can use a new syntax ${PARAMETER} inside of the back-ticked string.

```
var name = `Your name is ${firstName} ${lastName}.`

```

✍**Arrow Functions in ES6**

The fat arrows are amazing because they would make this behave properly, i.e., this will have the same value as in the context of the function— it won’t mutate.

```
$('.btn').click((event) => {
   this.doSomething()
});

```

✍ **Promises in ES6**

Promises are used for asynchronous execution. In ES6, we can use promise with the arrow function shown below.

```
var asyncCall =  new Promise((resolve, reject) => {
   // do something async
   resolve();
}).then(()=> {
   console.log('Yay!');
})

```

✍**Block-Scoped Constructs Let and Const**

```
function calculateAmount(boolVal) {
   let amount = 0;
   if(boolVal) {
      let amount = 1; // scope of this amount ends with next closing bracket
   }
   return amount;
}
console.log(calculateAmount(true)); // output: 0

```

✍**Enhanced Object Literals in ES6**

```
function getLaptop(make, model, year) {
   return {
      make,
      model,
      year
   }
}

getLaptop("Apple", "MacBook", "2015");

```

✍**Destructuring Assignment in ES6**

The destructuring assignment syntax is a JavaScript expression that makes it possible to unpack values from arrays, or properties from objects, into distinct variable.

```
var o = {p: 42, q: true};
var {p, q} = o;

console.log(p); // 42
console.log(q); // true

```

✍**Default Parameters in ES6** In ES6, we can put the default values right in the signature of the functions.

```
var calculateArea = function(height = 50, width = 80) {
    // write logic
    ...
}

```

🚀**JS engine archietecture.**

🚀**What is prototypal inheritance? Give example**

✍The core idea of Prototypal Inheritance is that an object can point to another object and inherit all its properties. The main purpose is to allow multiple instances of an object to share common properties

✍[dmitripavlutin.com/javascript-prototypal-in..](https://dmitripavlutin.com/javascript-prototypal-inheritance)

🚀**Write Polyfill for my bind method.**

✍A polyfill is a piece of code that implements the features that you expect the browser to support natively.

```
 let name = {
        firstName: "Riya",
        lastName: "Jain"
    }

    function printFullName (city, country) {
        console.log(this.firstName + ' ' + this.lastName + ' from ' + city + ', ' + country)
    }

    Function.prototype.polyfill_bind = function (...args) {
        let context = this;
        let params = args.slice(1)
        return function (...args2) {
            context.apply(args[0], [...params, ...args2] )
            // Or
            // context.call(args[0], ...params, ...args2)
        }
    }

    let showName = printFullName.polyfill_bind(name, 'JavaScript Family')
    showName('India');

    // Output: Riya Jain from JavaScript Family, India

```

🚀**What is an event loop?**

✍The **event loop(a gatekeeper**): it constantly checks whether or not the call stack is empty. If it is empty, new functions are added from the event queue. If it is not, then the current function call is processed.

![JavaScript%20Questions%20and%20Answers%2089841ee7c84d4f9c9da19f6b52c72c5a/TL6UhuQs0.png](JavaScript%20Questions%20and%20Answers%2089841ee7c84d4f9c9da19f6b52c72c5a/TL6UhuQs0.png)

🚀**splice vs slice method.**

✍The **slice****( )** method copies a given part of an array and returns that copied part as a new array. It doesn’t change the original array.

🎈array.slice(from, until);

🎈For example, I want to slice the first three elements from the array above. Since the first element of an array is always indexed at 0, I start slicing “from”0.

Now here is the tricky part. When I want to slice the first three elements, I must give the until parameter as 3. The slice( ) method doesn’t include the last given element.

🎈let array = [1, 2, 3, "hello world", 4.12, true]; array[0] --> 1 // included array[1] --> 2 // included array[2] --> 3 // included array[3] --> "hello world" // not included

🎈Finally, I assign the sliced Array to the newArray variable. Now let’s see the result:

> newArray variable is an array now, and the original one remains the same
> 

✍**Splice** array in JavaScript is a method that adds or removes items to or from the array. It’s a method that changes the content by adding the new elements or removing the old ones from an array.

> array.splice(index,howmany, item1,..............,item x)
> 

🎈Another way of declaring splice array is:

> var arrDeletedItems = array.splice(start, deleteCount,item1,item2, ...,item n)
> 

🎈Example: Remove 1 element from index 3

```
var myFish = ['pen', 'paper', 'drum', 'stone', 'pencil'];
var removed = myFish.splice(3, 1);
// removed is ["stone"]
// myFish is ["pen", "paper”, "stone", "pencil"]

```

> Output: Pen, paper, stone , pencil
> 

🚀**What is type of null,undefined,function ,NaN.**

```
typeof NaN // "number"
typeof null // "object"
typeof undefined // "undefined"
typeof function foo() {} // "function"

```

🚀**Difference between == and ===.**

The '==' operator performs a test based on abstract equality.

While the '===' operator tests for strict equality(two values are not of the same type when compared, the operator will return false).

```
36=='36' // true
36==='36' //  false

```

🚀**Implement a product method that will return the product of two numbers**

```
// Product
 const multiply = (num1, num2) => {
  return num1 * num2;
};
let result= multiply(4, 5);
console.log(result);
// 20

```

🚀**What is function currying? Give example**

🚀**What are promises in js? Difference between async-await vs promises.**

> A Promise is an object representing the eventual completion or failure of an asynchronous operation…Essentially, a promise is a returned object to which you attach callbacks, instead of passing callbacks into a function. — Mozilla Docs, Using promises
> 

✍A promise has two possible outcomes: it will either be kept when the time comes, or it won’t.

✍A promise is used to handle the asynchronous result of an operation.With Promises, we can defer the execution of a code block until an async request is completed.

✍First of all, a Promise is an object. There are 3 states of the Promise object:

🎈Pending: Initial State, before the Promise succeeds or fails.

🎈Resolved: Completed Promise

🎈Rejected: Failed Promise, throw an error

✍The promise has two parameters, one for success (resolve) and one for fail (reject):

```
const myPromise = new Promise((resolve, reject) => {
    // condition
});

```

✍

![JavaScript%20Questions%20and%20Answers%2089841ee7c84d4f9c9da19f6b52c72c5a/5_GH1WYKQ.png](JavaScript%20Questions%20and%20Answers%2089841ee7c84d4f9c9da19f6b52c72c5a/5_GH1WYKQ.png)

✍Await is basically syntactic sugar for Promises. It makes your asynchronous code look more like synchronous/procedural code, which is easier for humans to understand.

```
async function logFetch(url) {
  try {
    const response = await fetch(url);
    console.log(await response.text());
  }
  catch (err) {
    console.log('fetch failed', err);
  }
}

```

🎈**async** functions return a promise.**async** functions use an implicit Promise to return results.

🎈await blocks the code execution within the async function.When using async await, make sure you use try catch for error handling.

🎈await only blocks the code execution within the async function. It only makes sure that the next line is executed when the promise resolves. So, if an asynchronous activity has already started, await will not have any effect on it.

🚀**What are the advantages of using Axios over Fetch API?**

🚀**What is debouncing and create your own debouncing?**

✍ The debounce() function forces a function to wait a certain amount of time before running again. The function is built to limit the number of times a function is called.

🎈The function aims to reduce overhead by preventing a function from being called several times in succession.

![JavaScript%20Questions%20and%20Answers%2089841ee7c84d4f9c9da19f6b52c72c5a/sg7G9CJfY.png](JavaScript%20Questions%20and%20Answers%2089841ee7c84d4f9c9da19f6b52c72c5a/sg7G9CJfY.png)

🎈The Debounce technique allow us to “group” multiple sequential calls in a single one.

🎈Debounce function:

```
function debounce(fn, delay) {
  let timer;

  return function () {
    clearTimeout(timer);
    timer = setTimeout(() => fn(), delay);
  };
}

```

🎈Example:we type in the searchBar, the count of API called increases with each character. But that's not what we want to happen. What we want is to wait for the user to stop typing. As soon as the user stops typing then we want to make the API [call.So](http://call.so/) the above function will help us to achieve this:

🎈As soon as the user starts typing the function executes -:First it clears the timer if it's initialized. then it assigns the timer setTimeout function, which will run after 1 second if it is not cleared. If the user types any character within 1 second the function will be called again. But in the above step, we already assigned the setTimeout function to the timer variable. So the clearTimeout will clear the function from the timer variable and also assign a new setTimeout function to the timer variable. If the user didn't type and 1 second has passed, the function in setTimeout will execute and make the API call.

🚀**Difference between debouncing and throttling with examples.**

[telerik.com/blogs/debouncing-and-throttling..](https://www.telerik.com/blogs/debouncing-and-throttling-in-javascript)

🚀**Scope chain.**

![JavaScript%20Questions%20and%20Answers%2089841ee7c84d4f9c9da19f6b52c72c5a/AvXTOOd_D.png](JavaScript%20Questions%20and%20Answers%2089841ee7c84d4f9c9da19f6b52c72c5a/AvXTOOd_D.png)

✍The Scope Chain is the hierarchy of scopes that will be searched in order to find a function or variable.

✍Every scope is always connected to one or more scope in their back forming a chain or a hierarchy, except the global scope. The global scope does not have any parent, and that makes sense too since it is sitting at the top of the hierarchy.

🚀**Explain the CORS mechanism**

✍CORS is a mechanism that allows resources sharing between the origin, the provider, and requester servers. This determines the access permissions of the client origin by the source provider. As a result, the specified access permissions information is also sent to the browser.

🎈These resources are shared with HTTP Request, HTTP Response, and HTTP methods on a different inbound web browser.

🎈If you are a web developer, you must have seen the ‘CORS’ error appearing often on your screen when you try to call an API. But, Why does it happen?

![JavaScript%20Questions%20and%20Answers%2089841ee7c84d4f9c9da19f6b52c72c5a/6B9ow7dr3.png](JavaScript%20Questions%20and%20Answers%2089841ee7c84d4f9c9da19f6b52c72c5a/6B9ow7dr3.png)

🎈Well, For security reasons, browsers restrict cross-origin HTTP requests initiated from scripts. For example, if you want to access your API hosted at [api.github.com](https://api.github.com/) from your client-side frontend application which is hosted at [example.com](https://example.com/). The browser will not allow this request to complete.

🎈You only need to think about CORS when : API accessed by the browser. API is hosted on a separate domain.

🎈CORS allows the server to explicitly whitelist certain origin and help to bypass the same-origin policy.If your server is configured for CORS, it will return an extra header with “Access-Control-Allow-Origin” on each response.

🎈For example, if my API server hosted at [api.riya.com/users](https://api.riya.com/users) is CORS configured and I am making a request from my client application [github.com](https://github.com/) to fetch some data. The response will have this header.

```
Access-Control-Allow-Origin: https://github.com

```

🎈**CORS Preflight Request** :Preflighted requests first send an HTTP request by the OPTIONS method to the resource on the other domain, to determine if the actual request is safe to send or not.

![JavaScript%20Questions%20and%20Answers%2089841ee7c84d4f9c9da19f6b52c72c5a/UMhd0jZT7.png](JavaScript%20Questions%20and%20Answers%2089841ee7c84d4f9c9da19f6b52c72c5a/UMhd0jZT7.png)

✍ [developer.mozilla.org/en-US/docs/Web/HTTP/C..](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS) OR [youtube.com/watch?v=tcLW5d0KAYE](https://www.youtube.com/watch?v=tcLW5d0KAYE)

🚀**Difference between setTimeout vs setInterval.**

✍The difference between setTimeout() and setInterval() is that setTimeout() triggers the function call once. While, the setInterval() triggers the function repeatedly after the specified interval of time.

```
//Will output the text => The car is BMWon the console
function displayCar() {
    console.log('The car is BMW');
}

//The function 'displayCar' will be invoked repeatedly at a interval of 2 seconds
setInterval(displayCar, 2000);

```

🎈The displayCar function wil be called repeatedly at the specified time interval of 2000 milliseconds or 2 seconds.

✍**setTimeout example**

```
setTimeout(function() {
   console.log('Learn and explore!');
 }, 4000);

```

🎈"Learn and explore!" will be displayed on the console after 4 seconds. The first parameter passed to the setTimeOut is an anonymous function. The second parameter is the timeout value specified in milliseconds."Learn and explore!" will be displayed on the console after 4 seconds. The first parameter passed to the setTimeOut is an anonymous function. The second parameter is the timeout value specified in milliseconds.

🚀**What is optional chaining**?

✍ It allows accessing easily the properties from nested objects. It prevents writing boilerplate that verifies against nullish values on every property accessor from the accessor chain.

🎈The optional chaining operator ( ?. ) enables you to read the value of a property located deep within a chain of connected objects without having to check that each reference in the chain is valid

🎈Optional chaining in JavaScript is very useful because it can clean up our code with a single character: ?. Here's an example where we can check if an object person has a property called name.

```
// check to see if person exists before getting name
// if person doesn't exist, return undefined
const name = response.person?.name;

// -----------

// we can check if arrays exist before we grab an item also
const firstDog = animals.dogs?.[0]

```

🎈[developer.mozilla.org/en-US/docs/Web/JavaSc..](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Optional_chaining)

🚀**Map vs filter vs forEach**

✍Use **.map()** whenever you need to update data inside an array (by mapping over it!).

```
const numbers =[1 , 2 ,4];
const doubled =numbers.map(function(number){
 return number * 2;
});
console.log(doubled); // [2 , 4 , 8]

```

> map() will always return a new array of the same length as the original!
> 

✍**.filter()** loops through (or iterates) through data, and filters out data that doesn't match the criteria that we set.

🎈**Syntax**

```
var new_array = arr.filter(function callback(element, index, array) {
    // Return true or false
}[, thisArg])

```

🎈**Example**

```
const numbers = [1, 2, 3, 4];
const evens = numbers.filter(item => item % 2 === 0);
console.log(evens); // [2, 4]

```

✍**.forEach() is a very generic array method. We should try to only use it when we want to perform a specific action for each element of an array.**

```
const numbers =[1, 2,3,4,5];
numbers.forEach(function(number){
console.log(number);
});

```

> forEach() does not create a new array. In fact, it returns undefined!
> 

🚀**What is type coercion?**

✍Type Coercion refers to the automatic or implicit conversion of values from one type to another.

```
var val = '10' + 10;
console.log(val);

```

String ‘1010’ will get printed in the console. The number 10 is implicitly converted to string ‘10’ while executing the code. That’s what implicit type casting or type coercion.

🎈1 + true // 2 When we add numbers to booleans, the booleans are coerced into numbers, true becomes 1 and false becomes 0.

🎈"hello world" + true // "hello worldtrue" When strings are added to booleans, the booleans are coerced into strings and the strings then get concatenated.

> One operator that will not trigger implicit type coercion is the strict equality operator, ===. Strict equality will check if two pieces of data are the same and if they have the same type. The loose equality (==) operator will trigger implicit coercion.
> 

🎈Using the bang operator (!) we can coerce any value into a boolean and return its opposite

```
const name = 'Riya';
console.log(name); // Riya
console.log(!name); // false
console.log(!!name); // true

```

🚀**Remove falsy values from Array.**

✍Falsy values in javaScript are 'false' , 'NaN', '0', 'null', '' '' , 'undefined'

```
var a = [1, 2, 'b', 0, {}, '', NaN, 3, undefined, null, 5];

var b = a.filter(Boolean); // [1, 2, "b", {}, 3, 5];

```

🚀**Shuffle elements in an array.**

```
let list = [1, 2, 3, 4, 5, 6, 7, 8, 9]
list = list.sort(() => Math.random() - 0.5)

```

OR

```
function shuffle(arra1) {
    let ctr = arra1.length;
    let temp;
    let index;

    // While there are elements in the array
    while (ctr > 0) {
// Pick a random index
        index = Math.floor(Math.random() * ctr);
// Decrease ctr by 1
        ctr--;
// And swap the last element with it
        temp = arra1[ctr];
        arra1[ctr] = arra1[index];
        arra1[index] = temp;
    }
    return arra1;
}
const myArray = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9];
console.log(shuffle(myArray));

```

🚀**How to empty an array?**

🎈**Using length property:**

The length property returns the number of elements in that array. And if we equate this to 0, we will be able to empty the array elements.

```
names = ['Riya' , 'loves' , 'JavaScript'];
names.length = 0 // empties an array;
console.log(names); //[]

```

🎈**Assigning it to a new empty array** This is the fastest way of emptying an array.

```
names = ['Riya' , 'loves' , 'JavaScript'];
names = [];
console.log(names); //[]

```

🎈**Using splice() method** The splice() method takes the index (from which the splicing should start ) and the number of items to be removed as parameters and splices the elements.

```
names = ['Riya' , 'loves' , 'JavaScript'];
names.splice(0,names.length)// empties array;
console.log(names); // []

```

🚀**Different ways of creating an object.**

✍ [geeksforgeeks.org/creating-objects-in-javas..](https://www.geeksforgeeks.org/creating-objects-in-javascript-4-different-ways/)

🚀**Spread operator vs rest operator.**

✍**Spread operator**: allows iterables( arrays / objects / strings ) to be expanded into single arguments/elements.

🎈Splitting the strings:

```
 let name = "JavaScript";

 let arrayOfStrings = [...name];

console.log(arrayOfStrings);

 Ouptut -> ["J", "a", "v", "a", "S", "c", "r", "i", "p", "t"]

```

🎈Merging arrays:

```
const group1 = [1,2,3];
const group2 = [4,5,6];

const allGroups = [...group1,...group2];

console.log(allGroups)

//output -> [1, 2, 3, 4, 5, 6]

```

🎈Using spread operator in Function Calls:

```
function sum(a,b,c){
    return a+b+c;
}

const nums = [1,2,3];

//function calling

sum(...nums) // 6

```

✍**Rest parameter**: collects all remaining elements into an array

🎈If you see (…) dots on the function parameter then it is a rest parameter.

```
function sumAll(...args) {
    let sum = 0;
    for(let arg of args){
        sum = sum + arg;
    }
    return sum;
}

sumAll(1, 2, 3); //6
sumAll(1, 2, 3, 4); //10

```

🚀**What is a strict mode in js?**

✍Strict mode adds certain compulsions to JavaScript.Unde the strict mode,JavaScript shows error for a piece of codes,which do not show an error before,but might be problematic and potentially unsafe.Strict mode also solves some mistakes that hamper the JavaScript engines to work efficiently.

Strict mode can be enabled by adding the string literal "use strict" above the file.This can be illustrated by the given example:

```
function myfunction(){
"use strict";
var v ="This is a strict mode function";

```

🎈Benefits:Prevents unsafe actions to be performed.Prohibits some syntax likely that is probably going to be implemented as a part of future versions of the language.

🚀**What is eval()?**

✍The eval() function accepts a string value which holds JavaScript code. This function executes the given code and returns the result of the code.

> eval(string)
> 

```
var x = 2;
var y = 39;
var z = "42";
eval("x + y + 1"); // returns 42
eval(z);           // returns 42

```

🎈eval() is a dangerous function, which executes the code it's passed with the privileges of the caller. If you run eval() with a string that could be affected by a malicious party, you may end up running malicious code on the user's machine with the permissions of your webpage / extension. More importantly, third party code can see the scope in which eval() was invoked, which can lead to possible attacks in ways to which the similar Function is not susceptible.

🎈 [developer.mozilla.org/en-US/docs/Web/JavaSc..](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/eval)

🚀**Remove duplicate values from an array.**

✍**Using set operator** A set can only contain unique values

```
const array =[1,2,4,2,7,1];
const unique = [...new Set(array)];
console.log(unique); // [1, 2, 4, 7]

```

✍**Using Array.filter() and Array.indexOf()**

```
function usingFilterAndIndexOf(a) {
  return a.filter((element, index) => a.indexOf(element) === index);
}

const a = [1,1,2,3,3,4,4,5,5];
const b = [2,3,3,1,2,7,5,5,4,9,4,14];
const c = [5,2,3,2,5,5,1,7,2,1,5,8];

usingFilterAndIndexOf(a) //[1,2,3,4,5]
usingFilterAndIndexOf(b) //[2,3,1,7,5,4,9,14]
usingFilterAndIndexOf(c) //[5,2,3,1,7,8]

```

🚀**Difference between null and undefined**

✍In JavaScript ,undefined means the value of variable is not yet defined.And typeof undefined is also 'undefined'.We are getting undefined in JavaScript in some ways like :declaring a variable without assigning any value to it.

✍**null**  means empty or non-existent value which is used to indicate "no value" and typeof null returns object.

```
var a;
console.log(a);
// undefined

var b= null;
console.log(b);
// null

```

🚀**Check if a given object is empty or not.**

✍**Using Object.keys**

Object.keys will return an Array, which contains the property names of the object. If the length of the array is 0, then we know that the object is empty

```
const obj ={};
function isEmpty(obj) {
    return Object.keys(obj).length === 0;
}

```

✍Using JSON.stringfy If we stringify the object and the result is simply an opening and closing bracket, we know the object is empty.

```
function isEmptyObject(obj){
    return JSON.stringify(obj) === '{}';
}

```

🚀**Explain JWT in detail.**

✍JWT(JSON Web Token) is a method of transferring data between two parties in a compact manner.

🎈JWT contains three parts : header, payload,signature.

🎈The most common approach of authentication is to store the user in a session on the server. A session is a temporary file to make data accessible across pages on a website such as making sure the user can access a web resource.

🎈However, with JWT, we don’t need to manage sessions on the server anymore because the server only cares if the incoming request is valid, and comes from the right person.

🎈Here’s four steps showing how JWT works in practice without needing to use the sessions on the server.

🎈User logs in with username and password If credentials are correct, server creates a signed JWT which says who the user is. User wants to access home page Verify the JWT signature is valid, if true, grant access.

🎈 [float-middle.com/json-web-tokens-jwt-vs-ses..](https://float-middle.com/json-web-tokens-jwt-vs-sessions/) and also watch [youtube.com/watch?v=7Q17ubqLfaM](https://www.youtube.com/watch?v=7Q17ubqLfaM)

🚀**Difference between stop propagation and prevent default method.**

✍**prevent default method** is used to stop the browser’s default behavior when performing an action. Following are some examples of the default behavior:

🎈Clicking on a checkbox/radio input selects/deselects a checkbox.

🎈Clicking on an input/text-area field focuses the input and places the cursor in the input element

```
document.querySelector("#id-checkbox").addEventListener("click", function(event) {
         document.getElementById("output-box").innerHTML += "Sorry! <code>preventDefault()</code> won't let you check this!<br>";
         event.preventDefault();
}, false);

```

```
<p>Please click on the checkbox control.</p>

<form>
  <label for="id-checkbox">Checkbox:</label>
  <input type="checkbox" id="id-checkbox"/>
</form>

<div id="output-box"></div>

```

If you click on checkbox, then you will show something like this.

```
Sorry!  preventDefault()  won't let you check this!

```

✍The **stopPropagation()** method of the Event interface prevents further propagation of the current event in the capturing and bubbling phases.

🎈By default, all event handlers are registered in the bubbling phase. So if you click on a HTML element, the click event bubbles from the clicked element outwards to the element.

🎈So, we need to use stopPropagation which makes it so that first handler is run but the event doesn't bubble any further up the chain, so no more handlers will be run.

```
$("#but").click(function (event) {
    event.stopPropagation()
})
// since propagation was stopped by the #but id element's click, this alert will never be seen!
$("#foo").click(function () {
    alert("parent click event fired!")
})

```

```
<script src="https://ajax.googleapis.com/ajax/libs/jquery/2.1.1/jquery.min.js"></script>
<div id="foo">
    <button id="but">button</button>
</div>

```

🚀**What is array destructuring?**

✍Destructuring simply implies breaking down a complex structure into simpler parts.

Destructuring syntax can be used for variable declaration or variable assignment. You can also handle nested structures by using nested destructuring syntax.

**Basic Destructuring**

```
const numbers = [1,2,3];
const [one, two, three] = numbers;
console.log(one); // 1
console.log(two); // 2
console.log(three); // 3

```

**Nested Destructuring**

```
const numbers = [1,2,3,[11,22,33]];
const [one,two,three,[eleven, twelve, thirteen ]] = numbers
console.log(one) //1
console.log(eleven) //11

```

**Destructuring with Functions**

```
const numbers = [1,2,3,[11,22,33]];
const [one,two,three,[eleven, twelve, thirteen ]] = numbers
console.log(one) //1
console.log(eleven) //11

```

🚀**Difference between the arrow and normal function.**

[dmitripavlutin.com/differences-between-arro..](https://dmitripavlutin.com/differences-between-arrow-and-regular-functions/)

🚀**Increment and decrement operator.**

✍Increment and Decrement Operators: (are unary operators) are used to increment or decrement a variable value by 1.

🎈Two types of increment: Post Increment : variableName ++ Pre Increment : ++ variableName

```
var k = 5;
var j;
j = ++k; //result: j = 6, k = 5
j = k++; //result: j = 5, k = 6

```

> If the operator appears before the variable, the value is modified before the expression is evaluated. If the operator appears after the variable, the value is modified after the expression is evaluated. In other words, given j = ++k; , the value of j is the original value of k plus one; given j = k++; , the value of j is the original value of k , which is incremented after its value is assigned to j.
> 

🎈Two types of decrement: Post Decrement: variableName -- Pre Decrement : -- variableName

```
let b = 1;
console.log(b--);    // 1
console.log(b);      // 0

let c = 1;
console.log(--c);    // 0
console.log(c);      // 0

```

🚀**What is reference error and syntax error.**

✍A **reference error** is thrown when a code attempts to reference a non-existing variable

🎈Another important concept to understand, is that **scope** plays a big role in encountering ReferenceErrors. Scope determines the accessibility of variables. A variable needs to be available in the current context of execution, in order to be referenced. Every JavaScript function creates a new scope, thus variables defined inside of a function cannot be accessed from outside of that function, as the variable is defined from within the function.

```
function multiplyTwo() {
  let num1 = 2;
  return num1 * 2;
}
console.log(num1) // Uncaught ReferenceError: num1 is not defined

```

🎈Undefined variables

```
let firstName = "Riya"
let age = 99

console.log(lastName)
// Uncaught ReferenceError: lastName is not defined

```

✍**Syntax Error** The most popular one while development. It tells us that the syntax of code is somehow invalid.

🚀**Explain what the callback function is and provide a simple example.**

✍A callback is a function passed into another function as an argument to be executed later.

```
// function
function greet(name, callback) {
    console.log('Hi' + ' ' + name);
    callback();
}

// callback function
function callMe() {
    console.log('I am callback function');
}

// passing function as an argument
greet('Peter', callMe);

```

✍In the above program, there are two functions. While calling the greet() function, two arguments (a string value and a function) are passed.The callMe() function is a callback function

✍The benefit of using a callback function is that you can wait for the result of a previous function call and then execute another function call.

🎈**Program with setTimeout()**

```
// Callback Function Example
function greet(name, myFunction) {
    console.log('Hello world');

    // callback function
    // executed only after the greet() is executed
    myFunction(name);
}

// callback function
function sayName(name) {
    console.log('Hello' + ' ' + name);
}

// calling the function after 2 seconds
setTimeout(greet, 2000, 'John', sayName);

```

✍ [developer.mozilla.org/en-US/docs/Glossary/C..](https://developer.mozilla.org/en-US/docs/Glossary/Callback_function)

🚀**Given a string, reverse each word in the sentence.**

✍Using reverse

```
function reverseString(str) {
  return str
    .split('')
    .reverse()
    .join('');
}

```

✍Using reduce

```
function reverseString(str) {
  return [...str].reduce((accumulator, current) => {
    return current + accumulator;
  });

  // OR One-Liner
  // return [...str].reduce((accumulator, current) => current + accumulator)
}

```

🚀**Given two strings, return true if they are anagrams of one another.**

```
function isAnagram (str1, str2) {

    if (str1.length !== str2.length) {
        return false;
    }

    var sortStr1 = str1.split('').sort().join('');
    var sortStr2 = str2.split('').sort().join('');

    return (sortStr1 === sortStr2);
}

console.log(isAnagram('dog','god')); // true
console.log(isAnagram('foo','bar')); // false
console.log(isAnagram('foo','fooo')); // false

```

🚀**How does this keyword works. Provide some examples.**

✍Context is always the value of the this keyword which is a reference to the object that “owns” the currently executing code or the function where it’s looked at.

🎈

![JavaScript%20Questions%20and%20Answers%2089841ee7c84d4f9c9da19f6b52c72c5a/AmEn_fcCJ.png](JavaScript%20Questions%20and%20Answers%2089841ee7c84d4f9c9da19f6b52c72c5a/AmEn_fcCJ.png)

🎈We know that windowis a global object in the browser so if we type thisin the console and it should return window object, which it does.

🎈Context — when the function is defined globally and used under an object (Implicit Binding).

🎈

![JavaScript%20Questions%20and%20Answers%2089841ee7c84d4f9c9da19f6b52c72c5a/VFCISkn9H.png](JavaScript%20Questions%20and%20Answers%2089841ee7c84d4f9c9da19f6b52c72c5a/VFCISkn9H.png)

🎈Arrow functions work differently from regular functions in terms of context. thiswill always refer to the lexical scope (read here about scope), i.e thisretains the value of the enclosing lexical context's.

![JavaScript%20Questions%20and%20Answers%2089841ee7c84d4f9c9da19f6b52c72c5a/rEZ7U8XCs.png](JavaScript%20Questions%20and%20Answers%2089841ee7c84d4f9c9da19f6b52c72c5a/rEZ7U8XCs.png)

> In global code, it will be set to the global object, hence we get above true.
> 

🎈 [freecodecamp.org/news/javascript-this-keywo..](https://www.freecodecamp.org/news/javascript-this-keyword-binding-rules/)

🚀**What is the difference between var, let, and const.**

✍**var:**function-scoped and can be updated and redeclared.

🎈**let :** block-scoped, can be updated, but cannot be redeclared.

🎈**const :** block-scoped, cannot be updated and redeclared.

> For in depth understanding let and constant in temporal dead zone.Do watch this: youtube.com/watch?v=BNC6slYCj50
> 

🚀**Calculate the sum of all elements in a multidimensional array of infinite depth.**

```
function multi_array_sum(arr) {

    // see how many things are in the current array
    var currArrayLength = arr.length;
    // console.log( "currArrayLength: " + currArrayLength);

    // loop through the array and sum each element
    for( var i = 0; i < currArrayLength; i++ ) {

        // console.log( "arr["+ i +"]: " +  arr[i]);

        // is the current element a number? if so, add it to the sum
        if ( typeof arr[i] === "number") {
            arraySum += arr[i];
            // console.log( "arraySum: " + arraySum );
        }
        // is the current element an array? if so, recursively call this function
        else if ( Array.isArray( arr[i] ) === true ) {
            // console.log( "RECURSING");
            multi_array_sum( arr[i] );
        }

        // if the current element is some other thing then it will be ignored
    }

    return arraySum;
}

// set a variable outside of the function to hold the sum and set it to zero to start
// not sure how to put it in the function and make it work
var arraySum = 0;
var a = [1, [2, [3,4]], [5,6] ];
var result = multi_array_sum( a );
console.log( result );

```

🚀**Find a maximum consecutive repeating char in a given string.**

```
let str = 'bbbaaaaccadd'; //max repeating char is a with count 4
//sudo code
maxNow = if input string length is 1 or greater than 1 ? 1 : 0
maxOverall = if input string length is 1 or greater than 1 ? 1 : 0

for char in inputString starting from index 1
  if char equals prevChar
    maxNow++
    maxOverall = max(maxOverall, maxNow)
  else if char not equals prevChar
    maxNow = 1

```

🚀**Filter movie list by average rating, name.Sort filtered list by any field inside movie object.**

```
function getMovies() {
  return []; // [{id, name, year}]
}

// O(R)
function getRatings() {
  return []; // [{id, movie_id, rating}]   0 <= rating <= 10   // e.g 9.3
}

/**
 * minAvgRating ->
 *    avgRating >= minAvgRating
 *
 * sort ->
 *    name -> ascending order movies by name
 *   -name -> descending
 *
 *    avgRating
 *
 *
 * search ->
 *   'ave' -> 'Avengers'
 *   'avengers' -> 'Avengers'
 *   'AvengersInfinitywar' -> 'Avengers'
 */
const toLower = str => str.toLocaleLowerCase()

const getAvrgRating = (movie, movingWithRatings) => {
  let count = 0;
  return movingWithRatings.reduce((acc, value, index) => {
    const movieMatch = movie.id === value.movie_id
    if (movieMatch) {
      acc+=value.rating
      count++
    }
    if (index === movingWithRatings.length - 1) {
      acc = acc/count
    }
    return acc
  }, 0)
}

const isSubString = (str1, str2) => {
  str1 = toLower(str1.split(" ").join(""))
  str2 = toLower(str2.split(" ").join(""))
  if (str1.length > str2.length) {
    return str1.startWith(str2)
  } else {
    return str2.startWith(str1)
  }
}

const moviesList = getMovies()
const movingWithRatings = getRatings();
function queryMovies({ search, sort, minAvgRating }) {
  let filteredMovies = movingWithRatings.filter(movie => getAvrgRating(movie, movingWithRatings) >= minAvgRating);
  filteredMovies = filteredMovies.map(movie => moviesList.filter(listItem => listItem.id === movie.movie_id).pop())
  filteredMovies = filteredMovies.filter(movie => isSubString(toLower(movie.name), toLower(search)))
  filteredMovies = filteredMovies.sort((a, b) => {
    const isDescending = sort[0] === '-' ? true : false
    let sortCopy = isDescending ? sort.slice(1) : sort
    const value1 = a[sortCopy]
    const value2 = b[sortCopy]
    if (isDescending) {
      return value1 > value2 ? -1 : 1
    }else {
      return value1 < value2 ? -1 : 1
    }
  })
  filteredMovies = filteredMovies.map(movie => ({
    ...movie,
    avgRating: movingWithRatings.filter(ratedMovie => ratedMovie.movie_id === movie.id)[0].rating
  }))
  return filteredMovies
}

```

![JavaScript%20Questions%20and%20Answers%2089841ee7c84d4f9c9da19f6b52c72c5a/1Ujk-lU86.png](JavaScript%20Questions%20and%20Answers%2089841ee7c84d4f9c9da19f6b52c72c5a/1Ujk-lU86.png)

Well, this is it from my side. See you soon 😁

If you need any help feel free to ping me on LinkedIn [linkedin.com/in/riya-jain-6691b8127](https://www.linkedin.com/in/riya-jain-6691b8127)

### Interested in reading more such articles from Riya Jain?

Support the author by donating an amount of your choice.