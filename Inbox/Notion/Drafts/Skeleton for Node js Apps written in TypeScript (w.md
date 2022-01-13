# Skeleton for Node.js Apps written in TypeScript (with Setup Instructions for ESLint, Prettier, and Husky) | by Santosh Shinde | JavaScript in Plain English

Status: Unprocessed
URL: https://javascript.plainenglish.io/skeleton-for-node-js-apps-written-in-typescript-444fa1695b30

![https://miro.medium.com/max/1200/1*bGWHGFTuvAqfvDmz4ftpKQ.png](https://miro.medium.com/max/1200/1*bGWHGFTuvAqfvDmz4ftpKQ.png)

---

![Skeleton%20for%20Node%20js%20Apps%20written%20in%20TypeScript%20(w%205bf4027685c647099c7eb21cf4b0637e/1bGWHGFTuvAqfvDmz4ftpKQ.png](Skeleton%20for%20Node%20js%20Apps%20written%20in%20TypeScript%20(w%205bf4027685c647099c7eb21cf4b0637e/1bGWHGFTuvAqfvDmz4ftpKQ.png)

Skeleton for Node.js applications

# **Why do we really need boilerplate code?**

The **Wikipedia** [definition](https://en.wikipedia.org/wiki/Boilerplate_code#:~:text=In%20computer%20programming%2C%20boilerplate%20code,Such%20code%20is%20called%20boilerplate.) of boilerplate code is:

> In computer programming, boilerplate code or just boilerplate are sections of code that are repeated in multiple places with little to no variation. When using languages that are considered verbose, the programmer must write a lot of code to accomplish only minor functionality. Such code is called boilerplate.
> 

Boilerplate codes are repetitive codes required to be included in the application with little to no change by the program/framework and contribute nothing to the logic of the application.

Also, we can say that it’s the code from which we can start with the development and follow the structure or approach which is already defined in the boilerplate code.

Boilerplate in software development can mean different things to different people but generally means the block of code that is used over and over again.

# Purpose

Our main purpose with this skeleton is to start server applications with Node.js and TypeScript. And along with that, to also get started with the integration of ESLint, Prettier, and Husky.

Give it a try. I am happy to hear your feedback or any kind of new features you’d like to tell me about.

# Common Features

1. Quick start
2. Integrated ESLint, Prettier and Husky
3. Common Error Handler
4. Simple and Standard scaffolding
5. Followed SOLID Principles
6. Based on TypeScript Syntax
7. Simple Environment Configuration
8. Easily add a new feature
9. Integrated Winston Logger
10. Production-Ready Skeleton
11. Follows Production Ready Best Practices: Security

# Project Structure

Project Folder Structure

Project Source code Structure

**Please find below the boilerplate source code for Node.js applications written in TypeScript.**

# Boilerplate Workflow

Boilerplate Workflow

# **What are the Production Ready Best Practices: Security?**

- Don’t use deprecated or vulnerable versions of Express
- Use TLS
- Use Helmet
- Use cookies securely
- Prevent brute-force attacks against authorization
- Ensure your dependencies are secure
- Avoid other known vulnerabilities
- Additional considerations

# Set up ESLint, Prettier, and Husky in a Node.js TypeScript Project

## ESLint

ESLint is a tool for identifying and reporting on patterns found in ECMAScript/JavaScript code, with the goal of making code more consistent and avoiding bugs.

```
npm install --save-dev eslint typescript-eslint/parser eslint-config-airbnb @typescript-eslint/eslin-plugin
```

Last year, TSLint was deprecated in favour of ESLint ([TSLint in 2019](https://medium.com/palantir/tslint-in-2019-1a144c2317a9)).

`eslint`ESLint is a tool for identifying and reporting on patterns found in ECMAScript/JavaScript code.

`typescript-eslint/parser`An ESLint parser which leverages TypeScript ESTree to allow for ESLint to lint TypeScript source code.

`eslint-config-airbnb`This package provides Airbnb’s `.eslintrc`as an extensible shared config.

`@typescript-eslint/eslin-plugin`An ESLint plugin that provides lint rules for TypeScript codebases.

Create `.eslintrc` file in the root directory and add the below configuration to it.

```
{
        "parser": "@typescript-eslint/parser",
        "extends": [
            "airbnb/base",
            "plugin:@typescript-eslint/recommended",
            "plugin:import/errors",
            "plugin:import/warnings",
            "plugin:import/typescript"
        ],
        "parserOptions": {
            "ecmaVersion": 2018,
            "project": "./tsconfig.json"
        },
        "rules": {
            "semi": ["error", "always"],
            "object-curly-spacing": ["error", "always"],
            "camelcase": "off",
            "@typescript-eslint/explicit-function-return-type": "off",
            "@typescript-eslint/no-explicit-any": 1,
            "@typescript-eslint/no-inferrable-types": [
                "warn",
                {
                "ignoreParameters": true
                }
            ],
            "no-underscore-dangle": "off",
            "no-shadow": "off",
            "no-new": 0,
            "@typescript-eslint/no-shadow": ["error"],
            "@typescript-eslint/no-unused-vars": "warn",
            "quotes": [2, "single", { "avoidEscape": true }],
            "class-methods-use-this": "off",
            "import/extensions": [
                "error",
                "ignorePackages",
                {
                "js": "never",
                "jsx": "never",
                "ts": "never",
                "tsx": "never"
                }
            ]
        }
    }
```

Add the `.eslintignore` file, it can help tell ESLint to ignore specific files and directories using `ignorePatterns` in your config files. `ignorePatterns` patterns follow the same rules as `.eslintignore`.

```
    /node_modules/*

    # build artefacts
    dist/*
    build/*
    coverage/*

    # data definition files
    **/*.d.ts

    # 3rd party libs
    /src/public/

    # custom definition files
    /src/types/
```

Add action script in `package.json`.

eslint

## Prettier

By far the biggest reason for adopting **Prettier** is to stop all the ongoing debates over styles. It is generally accepted that having a common style guide is valuable for a project and team but getting there is a very painful and unrewarding process. Because **Prettier** is the only “style guide” that is fully automatic.

`prttier` Prettier is an opinionated code formatter. It enforces a consistent style by parsing your code and re-printing it with its own rules that take the maximum line length into account, wrapping code when necessary.

`eslint-config-prettier` Turns off all rules that are unnecessary or might conflict with Prettier. This lets you use your favourite shareable config without letting its stylistic choices get in the way when using Prettier.

`eslint-plugin-prettier` Runs Prettier as an ESLint rule and reports differences as individual ESLint issues.

Create `.prettierrc` file in the root directory and add the below configuration to it.

```
{
        "bracketSpacing": true,
        "printWidth": 80,
        "proseWrap": "preserve",
        "semi": true,
        "singleQuote": true,
        "trailingComma": "all",
        "tabWidth": 4,
        "useTabs": true,
        "parser": "typescript",
        "arrowParens": "always",
        "requirePragma": true,
        "insertPragma": true,
        "endOfLine": "lf",
        "overrides": [
            {
                "files": "*.json",
                "options": {
                    "singleQuote": false
                }
            },
            {
                "files": ".*rc",
                "options": {
                    "singleQuote": false,
                    "parser": "json"
                }
            }
        ]
    }
```

Add `"prettier"` to the `"extends"` array in your `.eslintrc.*` file. Make sure to put it last, so it gets the chance to override other configs.

Add the `"prettier"` entry in `"plugins"` array in your `.eslintrc.*` file.

Also, add the net `"prettier/prettier": ["error"]` entry in `"rules"` object in your `.eslintrc.*` file.

Please check the below updated `.eslintrc` config.

```
{
        "parser": "@typescript-eslint/parser",
        "extends": [
            "airbnb/base",
            "plugin:@typescript-eslint/recommended",
            "plugin:import/errors",
            "plugin:import/warnings",
            "plugin:import/typescript",
            "prettier"
        ],
        "parserOptions": {
            "ecmaVersion": 2018,
            "project": "./tsconfig.json"
        },
        "plugins": ["prettier"],
        "rules": {
            "prettier/prettier": ["error"],
            "semi": ["error", "always"],
            "object-curly-spacing": ["error", "always"],
            "camelcase": "off",
            "@typescript-eslint/explicit-function-return-type": "off",
            "@typescript-eslint/no-explicit-any": 1,
            "@typescript-eslint/no-inferrable-types": [
                "warn",
                {
                "ignoreParameters": true
                }
            ],
            "no-underscore-dangle": "off",
            "no-shadow": "off",
            "no-new": 0,
            "@typescript-eslint/no-shadow": ["error"],
            "@typescript-eslint/no-unused-vars": "warn",
            "quotes": [2, "single", { "avoidEscape": true }],
            "class-methods-use-this": "off",
            "import/extensions": [
                "error",
                "ignorePackages",
                {
                "js": "never",
                "jsx": "never",
                "ts": "never",
                "tsx": "never"
                }
            ]
        }
    }
```

Add the `.prettierignore` file. To exclude files from formatting, create a `.prettierignore` file in the root of your project. `.prettierignore` uses gitignore syntax.

```
    build
    dist
    coverage

    # Ignore all HTML files:
    *.html

    .gitignore
    .prettierignore
```

Add action script in `package.json`.

prettier — npm run pretty

## Husky

**Husky** improves your commits and more — 🐶 woof! You can use it to lint your commit messages, run tests, lint code, etc when you commit or push. **Husky** supports all Git **hooks**.

```
npm install --save-dev huksy
```

Add action script in `package.json`.

husky — `npm run prepare`

Add the git hooks actions in `pre-commit`and `pre-push` files, create the `pre-commit` and `pre-push` files in `.husky folder` and this folder is created after running `npm run prepare`on terminal.

Add below script in `pre-commit file`

husky — `npm run precommit`

Add below script in `pre-push file`

husky — `npm run prepush`

Please execute the below command on the terminal to make hooks executable by default. Because files are not executable by default; they must be set to be executable

Getting started with Node JS & Typescript

# References