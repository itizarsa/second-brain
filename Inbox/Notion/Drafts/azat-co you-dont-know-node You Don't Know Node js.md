# azat-co/you-dont-know-node: You Don't Know Node.js

Source: Article
Status: Unprocessed
URL: https://github.com/azat-co/you-dont-know-node

[https://opengraph.githubassets.com/06208d638e35fac17230df4abe96dc4059d58e1e06bb48501a331c9f459b9cf3/azat-co/you-dont-know-node](https://opengraph.githubassets.com/06208d638e35fac17230df4abe96dc4059d58e1e06bb48501a331c9f459b9cf3/azat-co/you-dont-know-node)

---

footer: © Node.University, 2018 theme: Simple slidenumbers: true build-lists: true [.hide-footer] [.slidenumbers: false]

# You Don't Know Node, v2

## Quick Intro to Core Node

# Turn OFF laptops, phones, distractors and LISTEN

# Who am I? `¯\_(ツ)_/¯`

# Not Kyle Simpson

(Hint: He wrote "You Don't Know JS" series)

![azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/kylesimpson.jpg](azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/kylesimpson.jpg)

^You are looking for Kyle Simpson, you're in a wrong room

# My name is Azat Mardan and I am the creator of Node University

Azat Mardan and numbers

- 14 books (not counting Korean, Chinese, Polish and Russian translations)
    
    ![azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/1f4da.png](azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/1f4da.png)
    
- 20+ conferences talks in 2016-17
    
    ![azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/1f3a4.png](azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/1f3a4.png)
    
- 200+ blog posts on Webapplog: [https://webapplog.com](https://webapplog.com/)
    
    ![azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/1f468-1f4bb.png](azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/1f468-1f4bb.png)
    
- 239 top most active GitHub contributor, higher Paul Irish, Todd Motto, TJ Holowaychuk, John Papa, etc. ([source](https://github.com/azat-co/practicalnode))
    
    ![azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/2328.png](azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/2328.png)
    
- 19 online courses on Node University [https://node.university](https://node.university/)
    
    ![azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/1f393.png](azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/1f393.png)
    

^Macy's, Intuit, Northwestern Mutual, Apple, DocuSign, UC Davis, Salesforce, The University of Arizona, The Orchard, M3, Twilio, Fox Studios, Michael Kors

![azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/companies.png](azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/companies.png)

![azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/azats-books-covers.png](azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/azats-books-covers.png)

## Fun Facts

- Read ~270 books in last 4 years
- Check social media only once per week
- Prefer coffee with butter instead of milk
- Live in San Francisco Bay Area

# I know Node

- Storify - startup which we sold
- DocuSign - 50M users
- Capital One - Fortune 500

# I dislike compiled languages

## Actually, just one. Java!

![azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/java-compile-funny.jpg](azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/java-compile-funny.jpg)

# My Mission is to Make a World a Better Place

# My Plan

Software helps people

`+`

Node is a good tool to build good software

`=`

I need to teach as many people Node as possible

# My Goal (for this talk)

Spike your interest in core Node features

# Starting with basics: Why Use Node?

# Input/output is one of the most expensive type tasks (>CPU)

![azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/1f4b0.png](azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/1f4b0.png)

# Node has non-blocking I/O

![azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/non-blocking-docs.png](azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/non-blocking-docs.png)

^Docs are not very ilustrative

![azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/event-loop-node-interactive.jpg](azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/event-loop-node-interactive.jpg)

^Good but too much tech details

^This allows processing other tasks while IO calls are unfinished like this ^Nginx vs. Apache ^Blocking I/O is expensive!

![azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/non-blocking.png](azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/non-blocking.png)

^This allows processing other tasks while IO calls are unfinished like this ^Nginx vs. Apache ^Blocking I/O is expensive!

### Java Sleep

```
System.out.println("Step: 1");
System.out.println("Step: 2");
Thread.sleep(1000);
System.out.println("Step: 3");
```

## Node "Sleep"

```
console.log('Step: 1')
setTimeout(function () {
 console.log('Step: 3')
}, 1000)
console.log('Step: 2')
```

## Process Multiple Tasks

```
console.log('Step: 1')
setTimeout(function () {
 console.log('Step: 3')
 // console.log('Step 5')
}, 1000);
console.log('Step: 2')
// console.log('Step 4')
```

# Blocking Web Server

![azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/threading_java.png](azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/threading_java.png)

![azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/coffeeshop-blocking.jpg](azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/coffeeshop-blocking.jpg)

# Non-Blocking Web Server

![azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/threading_node.png](azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/threading_node.png)

^This is in contrast to today's more common concurrency model where OS threads are employed. Thread-based networking is relatively inefficient and very difficult to use. Furthermore, users of Node are free from worries of dead-locking the process --- there are no locks

![azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/coffeeshop-non-blocking.jpg](azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/coffeeshop-non-blocking.jpg)

# [Multi-threading] is the software equivalent of a nuclear device because if it is used incorrectly, it can blow up in your face.

[http://blog.codinghorror.com/threading-concurrency-and-the-most-powerful-psychokinetic-explosive-in-the-univ](http://blog.codinghorror.com/threading-concurrency-and-the-most-powerful-psychokinetic-explosive-in-the-univ)

# Blocking systems have to be multi-threaded

# Node is single threaded... and that's good!

![azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/1f604.png](azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/1f604.png)

## It's still possible to write blocking code in Node.js.

![azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/1f633.png](azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/1f633.png)

# Blocking Node.js Code

```
// blocking.js
console.log('Step: 1')
for (var i = 1; i<1000000000; i++) {
 // This will take 100-1000ms
}
console.log('Step: 2')
```

# Blocking Node.js Code

```
var fs = require('fs')

var contents = fs.readFileSync('accounts.txt','utf8')
console.log(contents)
console.log('Hello Ruby\n')

var contents = fs.readFileSync('ips.txt','utf8')
console.log(contents)
console.log('Hello Node!')
//accounts.txt->Hello Ruby->ips.txt->Hello Node!
```

# Non-Blocking Node.js Code

```
var fs = require('fs')

fs.readFile('accounts.txt','utf8', function(error, contents){
 console.log(contents)
})
console.log('Hello Ruby\n')

fs.readFile('ips.txt','utf8', function(error, contents){
 console.log(contents)
})
console.log('Hello Node!')
//Hello Ruby->Hello Node->... accounts.txt->ips.txt or ips.txt->accounts.txt
```

# Node *typically* is much faster than other platforms

# How many of you reach the performance limitations of apps built with blocking I/O systems?

# Probably not many

# My Fav Node Benefit

# JavaScript everywhere. One language to rule 'em all!

# When one language is used everywhere

- Think faster
- Reuse code
- Learn quicker

# Most of Node is JavaScript

- Array
- String
- Primitives
- Functions
- Objects

# Node !== Browser JavaScript

# Node Core Modules

![azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/node-core-modules.gif](azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/node-core-modules.gif)

# How to create global variables (no `window` in Node), work with modules, get path to my script?

# `global`

Now available everywhere in your code

# It has properties!

# `global.__filename`

# `global.__dirname`

# `global.module`

# `global.require()`

# How do I...?

- Access CLI input?
- Get system info: OS, platform, memory usage, versions, etc.?
- Read env vars (passwords!)?

# `global.process` or `process`

# `process.pid`

# `process.versions`

# `process.arch`

# `process.argv`

# `process.env`

# `process.uptime()`

# `process.memoryUsage()`

# `process.cwd()`

# `process.exit()`

# `process.kill()`

# Who likes and understands callbacks?

![azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/1f64b.png](azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/1f64b.png)

[http://callbackhell.com](http://callbackhell.com/)

```
fs.readdir(source, function (err, files) {
 if (err) {
 console.log('Error finding files: ' + err)
 } else {
 files.forEach(function (filename, fileIndex) {
 console.log(filename)
 gm(source + filename).size(function (err, values) {
 if (err) {
 console.log('Error identifying file size: ' + err)
 } else {
 console.log(filename + ' : ' + values)
 aspect = (values.width / values.height)
 widths.forEach(function (width, widthIndex) {
 height = Math.round(width / aspect)
 console.log('resizing ' + filename + 'to ' + height + 'x' + height)
 this.resize(width, height).write(dest + 'w' + width + '_' + filename, function(err) {
 if (err) console.log('Error writing file: ' + err)
 })
 }.bind(this))
 }
 })
 })
 }
})
```

## Callbacks are not very developmental scalable

![azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/1f61e.png](azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/1f61e.png)

# Me When Working With Deeply Nested Callbacks

![azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/tree_slam.gif](azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/tree_slam.gif)

# Events

Events are part of core and supported by most of the core modules while more advanced patterns such as promises, generators, async/await are not.

### Events == Node Observer Pattern

- Subject
- Observers (event listeners) on a subject
- Event triggers

### Events

```
var events = require('events')
var emitter = new events.EventEmitter()
```

### Events

In node.js an event can be described simply as a string with a corresponding callback.

```
emitter.on('done', function(results) {
 console.log('Done: ', results)
})
```

### Using Event Emitters

```
var events = require('events')
var emitter = new events.EventEmitter()

emitter.on('knock', function() {
 console.log('Who\'s there?')
})

emitter.on('knock', function() {
 console.log('Go away!')
})

emitter.emit('knock')
```

### Inheriting from EventEmitter

```
// job.js
var util = require('util')
var Job = function Job() {
 // ...
 this.process = function() {
 // ...
 job.emit('done', { completedOn: new Date() })
 }
}

util.inherits(Job, require('events').EventEmitter)
module.exports = Job
```

### Inheriting from EventEmitter

```
// weekly.js
var Job = require('./job.js')
var job = new Job()

job.on('done', function(details){
 console.log('Job was completed at', details.completedOn)
 job.removeAllListeners()
})

job.process()
```

### Listeners

```
emitter.listeners(eventName)
emitter.on(eventName, listener)
emitter.once(eventName, listener)
emitter.removeListener(eventName, listener)
```

# Resources to Learn Node Patterns

- Node Patterns: From Callbacks to Observer: [http://webapplog.com/node-patterns-from-callbacks-to-observer](http://webapplog.com/node-patterns-from-callbacks-to-observer)
- [https://github.com/azat-co/node-patterns](https://github.com/azat-co/node-patterns)
- [Node.js Design Patterns, Second Edition by Mario Casciaro, Luciano Mammino](https://www.packtpub.com/web-development/nodejs-design-patterns-second-edition)

# Problems with Large Data

- Speed: Too slow because has to load all
- Buffer limit: ~1Gb
- Overhyped (JK)

# Streams

## Abstractions for continuous chunking of data

# No need to wait for the entire resource to load

# Types of Streams

- Readable
- Writable
- Duplex
- Transform

## Streams Inherit from Event Emitter

# Streams are Everywhere!

- HTTP requests and responses
- Standard input/output (stdin&stdout)
- File reads and writes

# Readable Stream Example

`process.stdin`

Standard input streams contain data going into applications.

# This is achieved via a read operation.

# Input typically comes from the keyboard used to start the process.

To listen in on data from stdin, use the `data` and `end` events:

```
// stdin.js
process.stdin.resume()
process.stdin.setEncoding('utf8')

process.stdin.on('data', function (chunk) {
 console.log('chunk: ', chunk)
})

process.stdin.on('end', function () {
 console.log('--- END ---')
})
```

# Demo

`$ node stdin.js`

# New Interface `read()`

```
var readable = getReadableStreamSomehow()
readable.on('readable', () => {
 var chunk
 while (null !== (chunk = readable.read())) {
 console.log('got %d bytes of data', chunk.length)
 }
})
```

^readable.read is sync but the chunks are small

# Writable Stream Example

`process.stdout`

Standard output streams contain data going out of the applications.

# This is done via a write operation.

# Data written to standard output is visible on the command line.

# Writable Stream

To write to `stdout`, use the `write` function:

```
process.stdout.write('A simple message\n')
```

# What about HTTP?

```
const http = require('http')
var server = http.createServer( (req, res) => {
 req.setEncoding('utf8')
 req.on('data', (chunk) => {
 transform(chunk) // This functions is defined somewhere else
 })
 req.on('end', () => {
 var data = JSON.parse(body)
 res.end()
 })
})

server.listen(1337)
```

# Pipe

```
var r = fs.createReadStream('file.txt')
var z = zlib.createGzip()
var w = fs.createWriteStream('file.txt.gz')
r.pipe(z).pipe(w)
```

^Readable.pipe takes writable and returns destination

## What data type to use for binary data?

### Buffers

Binary data type, to create:

- `Buffer.alloc(size)`
- `Buffer.from(array)`
- `Buffer.from(buffer)`
- `Buffer.from(str[, encoding])`

Docs: [http://bit.ly/1IeAcZ1](http://bit.ly/1IeAcZ1)

# Working with Buffer

```
// buf.js
var buf = Buffer.alloc(26)
for (var i = 0 ; i < 26 ; i++) {
 buf[i] = i + 97 // 97 is ASCII a
}
console.log(buf) // <Buffer 61 62 63 64 65 66 67 68 69 6a 6b 6c 6d 6e 6f 70 71 72 73 74 75 76 77 78 79 7a>
console.log(buf.toString('utf8')) // abcdefghijklmnopqrstuvwxyz
```

# Buffer Convertion

```
buf.toString('ascii') // outputs: abcdefghijklmnopqrstuvwxyz
buf.toString('ascii', 0, 5) // outputs: abcde
buf.toString('utf8', 0, 5) // outputs: abcde
buf.toString(undefined, 0, 5) // encoding defaults to 'utf8', outputs abcde
```

### Remember fs?

```
fs.readFile('/etc/passwd', function (err, data) {
 if (err) return console.error(err)
 console.log(data)
});
```

`data` is buffer!

# Demo

```
$ node server-stream

```

# Streams and Buffer Demo

```
// server-stream.js
app.get('/stream', function(req, res) {
 var stream = fs.createReadStream(largeImagePath)
 stream.pipe(res)
})
```

```
$ node server-stream

```

[http://localhost:3000/stream](http://localhost:3000/stream) [http://localhost:3000/non-stream](http://localhost:3000/non-stream)

# Results in DevTools

`/stream` responds faster!

```
X-Response-Time
~300ms vs. 3-5s

```

# Stream Resources

Stream automated workshop: [https://github.com/substack/stream-adventure](https://github.com/substack/stream-adventure)

```
$ sudo npm install -g stream-adventure
$ stream-adventure

```

[https://github.com/substack/stream-handbook](https://github.com/substack/stream-handbook)

![azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/nodeconfcamp.jpg](azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/nodeconfcamp.jpg)

# How to scale a single threaded system?

# Cluster Usage

- Master: starts workers
- Worker: do the job, e.g., HTTP server

Number of processes = number of CPUs

# Clusters

```
var cluster = require('cluster')
var numCPUs = require('os').cpus().length
if (cluster.isMaster) {
 for (var i = 0; i < numCPUs; i++) {
 cluster.fork()
 }
} else if (cluster.isWorker) {
 // your server code
})
```

# Cluster Demo

1. Run `code/cluster.js` with node (`$ node cluster.js`).
2. Install `loadtest` with npm: `$ npm install -g loadtest`
3. Run load testing with: `$ loadtest http://localhost:3000 -t 20 —c 10`

Press control+c on the server terminal

# Cluster Libraries

- Core cluster: lean and mean
- strong-cluster-control ([https://github.com/strongloop/strong-cluster-control](https://github.com/strongloop/strong-cluster-control)), or `$ slc run`: good choice
- pm2 ([https://github.com/Unitech/pm2](https://github.com/Unitech/pm2)): good choice

### pm2

[https://github.com/Unitech/pm2](https://github.com/Unitech/pm2)

[http://pm2.keymetrics.io](http://pm2.keymetrics.io/)

Advantages:

- Load-balancer and other features
- 0s reload down-time, i.e., forever alive
- Good test coverage

### pm2 Demo: Typical Express Server

```
var express = require('express')
var port = 3000
global.stats = {}
console.log('worker (%s) is now listening to http://localhost:%s',
 process.pid, port)
var app = express()
app.get('*', function(req, res) {
 if (!global.stats[process.pid]) global.stats[process.pid] = 1
 else global.stats[process.pid] += 1;
 var l ='cluser '
 + process.pid
 + ' responded \n';
 console.log(l, global.stats)
 res.status(200).send(l)
})
app.listen(port)
```

### pm2 Demo

Using `server.js`:

```
$ pm2 start server.js -i 0

```

In a new window:

```
$ loadtest http://localhost:3000 -t 20 -c 10
$ pm2 list

```

# Spawn vs Fork vs Exec

- `require('child_process').spawn()` - large data, stream, no new V8 instance
- `require('child_process').fork()` - new V8 instance, multiple workers
- `require('child_process').exec()` - buffer, async, all the data at once

### Spawn Example

```
fs = require('fs')
process = require('child_process')
var p = process.spawn('node', 'program.js')
p.stdout.on('data', function(data)) {
 console.log('stdout: ' + data)
})
```

### Fork Example

```
fs = require('fs')
process = require('child_process')
var p = process.fork('program.js')
p.stdout.on('data', function(data)) {
 console.log('stdout: ' + data)
})
```

# Exec Example

```
fs = require('fs')
process = require('child_process')
var p = process.exec('node program.js', function (error, stdout, stderr) {
 if (error) console.log(error.code)
})
```

# There are few more methods

- child_process.execFile()
- child_process.execSync()
- child_process.execFileSync()

^child_process.execFile(): similar to child_process.exec() except that it spawns the command directly without first spawning a shell. child_process.execSync(): a synchronous version of child_process.exec() that will block the Node.js event loop. child_process.execFileSync(): a synchronous version of child_process.execFile() that will block the Node.js event loop.

# How to handle async errors?

# Handling Async Errors

Event Loop: Async errors are harder to handle/debug, because system loses context of the error. Then, application crashes.

Try/catch is not good enough.

### Synchronous Error in Node

```
try {
 throw new Error('Fail!')
} catch (e) {
 console.log('Custom Error: ' + e.message)
}
```

For sync errors try/catch works fine.

### Async Error Example

```
try {
 setTimeout(function () {
 throw new Error('Fail!')
 }, Math.round(Math.random()*100))
} catch (e) {
 console.log('Custom Error: ' + e.message)
}
```

The app crashes!

# Me When Async Error's Thrown

![azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/baby_elephant.gif](azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/baby_elephant.gif)

### Async Errors

How to deal with it?

![azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/1f605.png](azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/1f605.png)

## Best Practices for Async Errors?

- Listen to all “on error” events
- Listen to `uncaughtException`
- Use `domain` (soft deprecated) or [AsyncWrap](http://blog.trevnorris.com/2015/02/asyncwrap-tutorial-introduction.html)
- Log, log, log & Trace
- Notify (optional)
- Exit & Restart the process

### on('error')

Anything that inherits from or creates an instance of the above: Express, LoopBack, Sails, Hapi, etc.

```
server.on('error', function (err) {
 console.error(err)
})
```

### on('error') Chained Method Example

```
var http = require(‘http’)
var server = http.createServer(app)
 .on('error', function(e) {
 console.log(‘Failed to create server’)
 console.error(e)
 process.exit(1)
 })
```

### on(‘error’) Named Variable Example

```
var req = http.request(options, function(res) {
 // … processing the response
})

req.on('error', function(e) {
 console.log('problem with request: ' + e.message)
})
```

### uncaughtException

`uncaughtException` is a very crude mechanism for exception handling. An unhandled exception means your application - and by extension Node.js itself - is in an undefined state. Blindly resuming means anything could happen.

### uncaughtException

Always listen to `uncaughtException`!

```
process.on(‘uncaughtException’, handle)
```

or

```
process.addListener('uncaughtException', handle)
```

### uncaughtException Expanded Examples

```
process.on('uncaughtException', function (err) {
 console.error('uncaughtException: ', err.message)
 console.error(err.stack)
 process.exit(1)
})
```

or

```
process.addListener('uncaughtException', function (err) {
 console.error('uncaughtException: ', err.message)
 console.error(err.stack)
 process.exit(1)
```

# Domain

(Just out of curiosity)

Domain Example

```
let domain = require('domain').create()
domain.on('error', function(error){
 console.log(error)
})
domain.run(function(){
 throw new Error('Failed!')
})
```

Domain with Async Error Demo

domain-async.js:

```
let d = require('domain').create()
d.on('error', function(e) {
 console.log('Custom Error: ' + e)
})
d.run(function() {
 setTimeout(function () {
 throw new Error('Failed!')
 }, Math.round(Math.random()*100))
})
```

# Source code for Domain

[https://github.com/nodejs/node/blob/master/lib/domain.js](https://github.com/nodejs/node/blob/master/lib/domain.js)

```
var _domain = [null];
Object.defineProperty(process, 'domain', {
 enumerable: true,
 get: function() {
 return _domain[0];
 },
 set: function(arg) {
 return _domain[0] = arg;
 }
});
```

# Domain overwrites uncaught exception

```
if (process.hasUncaughtExceptionCaptureCallback()) {
 throw new errors.Error('ERR_DOMAIN_CALLBACK_NOT_AVAILABLE');
}
```

```
process.on('removeListener', (name, listener) => {
 if (name === 'uncaughtException' &&
 listener !== domainUncaughtExceptionClear) {
 // If the domain listener would be the only remaining one, remove it.
 const listeners = process.listeners('uncaughtException');
 if (listeners.length === 1 && listeners[0] === domainUncaughtExceptionClear)
 process.removeListener(name, domainUncaughtExceptionClear);
 }
});
```

^When domains are in use, they claim full ownership of the uncaught exception capture callback.

# C++ Addons

## How to Write C/C++ binding for your IoT, hardware, drone, smartdevice, etc.?

### Node and C++

Create the `hello.cc` file:

```
#include <node.h>

namespace demo {

using v8::FunctionCallbackInfo;
using v8::HandleScope;
using v8::Isolate;
using v8::Local;
using v8::Object;
using v8::String;
using v8::Value;
```

### Node and C++

Create the `hello.cc` file:

```
void Method(const FunctionCallbackInfo<Value>& args) {
 Isolate* isolate = args.GetIsolate();
 args.GetReturnValue().Set(String::NewFromUtf8(isolate, "capital one"));
}

void init(Local<Object> exports) {
 NODE_SET_METHOD(exports, "hello", Method);
}

NODE_MODULE(addon, init)

} // namespace demo
```

### Creating `binding.gyp`

Create `binding.gyp`:

```
{
 "targets": [
 {
 "target_name": "addon",
 "sources": [ "hello.cc" ]
 }
 ]
}

```

### node-gyp

```
$ npm install -g node-gyp

```

[https://github.com/nodejs/node-gyp](https://github.com/nodejs/node-gyp)

^Needs Python

### Configuring and Building

```
$ node-gyp configure
$ node-gyp build

```

Check for compiled `.node` files in build/Release/

### C++ Addons Examples

[https://github.com/nodejs/node-addon-examples](https://github.com/nodejs/node-addon-examples)

### Including Addon

Create `hello.js` and include your C++ addon:

```
var addon = require('./build/Release/addon')
console.log(addon.hello()) // 'capital one'
```

Run

```
$ node hello.js

```

Moaaarr *core* Node

- NAPI
- Crypto
- HTTP/2
- Node modules
- npm commands and scripts

# 30-Second Summary

1. Event Emitters
2. Streams
3. Buffers
4. Clusters
5. C++ Addons
6. Domain

^We have covered a lot in the last 60 minutes

# There are big, big, big problems

- 2 days
- 5 days
- 8 days

^2 days - won't remember my name and most of what I said ^5 days - remember only a joke ^8 days - won't remember being here

# New information

- Repetition
- Immersion
- Practice

# Solution: You Don't Know Node Online Course

![azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/you-dk-node-course-cover-v1.png](azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/you-dk-node-course-cover-v1.png)

[https://node.university/p/you-dont-know-node](https://node.university/p/you-dont-know-node)

# Sign up for Node University NOW!

![azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/watermark-inverted-no-bk.png](azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/watermark-inverted-no-bk.png)

[Node.University](https://node.university/) is the ultimate resource for the best online Node education!

[https://node.university](https://node.university/)

![azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/1f680.png](azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/1f680.png)

# This is how to do it

# Take out your laptops or phones

![azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/1f4bb.png](azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/1f4bb.png)

![azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/1f4f1.png](azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/1f4f1.png)

Seriously. Do it now!

# Go to node.university

([https://node.university](https://node.university/) in Safari, Chrome, Edge)

[.hide-footer] [.slidenumbers: false]

![azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/nodeu-1.png](azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/nodeu-1.png)

^Click/press on Free courses

[.hide-footer] [.slidenumbers: false]

![azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/nodeu-2.png](azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/nodeu-2.png)

^ Click/press on You Don't Know Node

[.hide-footer] [.slidenumbers: false]

![azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/nodeu-3.png](azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/nodeu-3.png)

^Click/Press on enroll

[.hide-footer] [.slidenumbers: false]

![azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/nodeu-4.png](azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/nodeu-4.png)

^Put your email and create a password

# One Last Thing

![azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/1f449.png](azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/1f449.png)

# CodingHorror.com

![azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/atwoods_law.png](azat-co%20you-dont-know-node%20You%20Don't%20Know%20Node%20js%204518cb558f47457c8d7c1471423fb9b1/atwoods_law.png)

# The End