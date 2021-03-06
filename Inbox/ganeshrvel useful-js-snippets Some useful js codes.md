# ganeshrvel/useful-js-snippets: Some useful js codes

Source: Notes
Status: Unprocessed
URL: https://github.com/ganeshrvel/useful-js-snippets

[https://opengraph.githubassets.com/52d025c076122018b871a01a7c503f62a4cc5d812492f326de4bd40c8b4b6f52/ganeshrvel/useful-js-snippets](https://opengraph.githubassets.com/52d025c076122018b871a01a7c503f62a4cc5d812492f326de4bd40c8b4b6f52/ganeshrvel/useful-js-snippets)

---

[useful-js-snippets](ganeshrvel%20useful-js-snippets%20Some%20useful%20js%20codes%20799218327ed742cd82536416975d9071/useful-js-snippets)

# Handy Javascript methods

License: MIT

Author: Ganesh Rathinavel

Requirements: es6, javascript enabled browser or node.js

Version: 1.2

URL: [https://github.com/ganeshrvel/useful-js-snippets](https://github.com/ganeshrvel/useful-js-snippets)

Navigate through 'tools.js' for the codes.

### Installation:

```
const {
 move,
 imageLoaded,
 getNetElementWidth,
 rand,
 stripTags,
 replaceAll,
 urlSanitizer,
 chainValidator,
 onlyNumber,
 toObject,
 rtrim,
 urls,
 htmlSanitize,
 isTouchDevice,
 isiOS,
 isFunction,
 isArray,
 isObject,
 isString,
 isJSON,
 changeURLHash,
 waitForElementLoad,
} = require('./tools')
```

### Overview:

### Move an array key-value pair to another index.

```
//Example:
let value = ['animals', 'plants'];
value.move(0, 3);

//Output: ["plants",undefined,undefined,"animals"]
```

### Wait for an image to load.

```
//Example: <img src='https://assets-cdn.github.com/images/modules/logos_page/GitHub-Logo.png'>

imageLoaded(
 'https://assets-cdn.github.com/images/modules/logos_page/GitHub-Logo.png').
then(res => {
 console.log(`Success`);
}).
catch(e => {
 console.error(`Error`);
});
```

### Find the actual width of an element.

> Total width: (width + margin - padding + border). It takes the styles of its children into consideration;
> 

```
//Example:
getNetElementWidth('#logo');
```

### Generate a lengthy random number.

```
//Example:
rand();
```

### Strip HTML Tags from an input string.

```
//Example:
stripTags(
 `<img src='https://assets-cdn.github.com/images/modules/logos_page/GitHub-Logo.png'>`,
 `<img><span>`);
```

### Replace all occurrences of a sub-string.

```
//Example:
replaceAll('this is a test but this is another test too', 'this', 'that');

//Output: that is a test but that is another test too
```

### URL Sanitizer.

> Encodes and decodes url parameters
> 

```
//Example:
urlSanitizer(`https://www.google.co.in/search?ei=abc&q=test+test`);
```

### Chained object validator.

```
//Example:

let obj1 = {
 key2: {
 key3: 'qwerty',
 },
 key4: [ //array
 {key5: 'abc'},
 [
 {key6: 'xyz'},
 [
 [
 {
 key7: 12345,
 key8: [
 {
 key9: '0000000',
 },
 ],
 },
 ],
 ],
 ],
 ],
 };

chainValidator(obj1, 'unknownKey'); //Output=> undefined
chainValidator(obj1, 'key2'); //Output=> {key3: "qwerty"}
chainValidator(obj1, 'key2.key3'); //Output=> qwerty
chainValidator(obj1, 'key4[0]'); //Output=> {key5: "abc"}
chainValidator(obj1, 'key4[1][0].key6'); //Output=> xyz
chainValidator(obj1, 'key4[1][1][0][0].key7'); //Output=> 12345
chainValidator(obj1, 'key4[1][1][0][0].key8[0].key9'); //Output=> 0000000
```

### Return numeric value from the input string.

```
//Example:
onlyNumber(`test abc 124#$' xyz`);

//Output: 124
```

### Array to Object.

```
//Example:
toObject([3, 5, 6]);
```

### Strip a character from the beginning and end of the string

```
//Example:
let animal = ' cat ';
rtrim(animal);
//Output: cat

let planet = 'sunearthsun';
rtrim(planet, 'sun');
//Output: earth

let alphabets = 'aaaaabaaaaa';
rtrim(alphabets, 'a');
//Output: b
```

### Get/Manipulate URL, URI parameters or hashes.

> get: returns parameter(s) in a url as an object; if url is empty current url is considered; if param is empty all url parameters are returned as an object getUrlWithoutHash: strips hash and return url; if url is empty current url is considered; getHash: returns the hash value of an url as an object; if url is empty current url is considered; parseHash: parses and returns multiple hash values of an url as an object; if url is empty current url is considered; if param is empty all url parameters are returned as an object removeHash: remove hash from the address bar url getUrlPath: get url location pathname
> 

```
//Example:
urls.get({});
//Output: {param: "value1", q: "hey"}

urls.get({url: 'http://www.example.com?t=a&p=s'});
//Output: {t: "a", p: "s"}

urls.getUrlWithoutHash({});
urls.getUrlWithoutHash({url: http://www.example.com?t=a&p=s#test'});
//Output: http://www.example.com?t=a&p=s

urls.getHash({});
urls.getHash({url: 'http://www.example.com?t=a&p=s#test'});
//Output: test

urls.parseHash({});
urls.parseHash({url: 'http://www.example.com#test1=var1&test2=var2'});
//Output: {test1: "var1", test2: "var2"}

urls.getUrlPath();
//Output: '/path1/path2'
```

### Sanitize html tags.

> Escapes and unescapes html tags
> 

```
htmlSanitize('<html>').escape;
//Output: &lt;html&gt;

htmlSanitize('&lt;html&gt;').unescape;
//Output: <html>
```

### Check whether the device is touch enabled.

```
//Example:
isTouchDevice();
```

### Detecting iOS.

```
//Example:
isiOS();
```

### Check whether the given variable is a function.

```
//Example:
let testFunction = function() {
 console.log('I am a function..');
};
isFunction(testFunction);
```

### Check whether the input variable is an Array.

```
//Example:
let testArray = ['earth', 'mars', 'venus'];
isArray(testArray);
```

### Check whether the input variable is an Object.

```
//Example:
let testObj = {
 'window': {
 'name': 'main_window',
 'width': 500,
 'height': 500,
 },
};
isObject(testObj);
```

### Check whether the input variable is an String.

```
//Example:
isString('qwerty');
```

### Check whether the variable is a JSON Object.

```
//Example:
let testJson = {
 'menuitem': [
 {'value': 'New', 'onclick': 'CreateNewDoc()'},
 ],
};
isJSON(testJson);
```

### Change the url hash in the address bar and push the same into the browser history.

```
//Example:
changeURLHash('test_param');

//Output: http://www.example.com#test_param
```

### Wait for DOM element load.

```
//Example:
waitForElementLoad({
 selector: '#div-id',
 time: 200,
}).
then(response => {
 console.log(`Element was successfully loaded into the DOM`);
}).
catch(e => {
 console.error(e);
});
```

### Changelogs:

### v1.2

- Added: ES5 Module import compatible
- Optimization: Cleaned some codes, Fixed few bugs

### v1.1

- Updated the README
- Added: Chained Object Validator
- Optimization: Cleaned some codes

### v1.0:

Initial Push