# Publishing an npx command to npm

Source: Notes
Status: Unprocessed
URL: http://www.sheshbabu.com/posts/publishing-npx-command-to-npm/

[http://www.sheshbabu.comundefined/](http://www.sheshbabu.comundefined/)

---

[npx](https://blog.npmjs.org/post/162869356040/introducing-npx-an-npm-package-runner) is an useful tool to run one-off commands like `create-react-app`, `http-server` etc.

In this post I’ll go through the steps needed to create a command line tool that can be invoked using npx.

Let’s start with a simple hello world script

```
console.log("hello world");
```

This prints “hello world” when you run it

```
$ node index.js
hello world
```

To make this runnable by npx, we need to convert this into an executable file by adding the node [shebang](https://en.wikipedia.org/wiki/Shebang_(Unix)) line

```
#!/usr/bin/env node

console.log("hello world");
```

Let’s then create a npm package so this file can be published to npm

```
$ npm init -y
```

This will create the package.json file.

If you publish this package now, it can be installed by others but they won’t be able to execute it using npx. For this we need to reference this file in the [bin](https://docs.npmjs.com/files/package.json#bin) field of package.json

```
{
  "name": "npx-example",
  "version": "1.0.0",
  "main": "index.js",
  "bin": "index.js",
  "scripts": {
    "start": "node ."
  },
  "license": "MIT"
}
```

You can now publish this package

```
$ npm publish
```

You can find a complete example in [this repo](https://github.com/sheshbabu/gitrmbr).