# santoshshinde2012/node-boilerplate: Node Typescript Boilerplate for Microservices. Skeleton for Node.js Apps written in TypeScript (with Setup Instructions for ESLint, Prettier, and Husky)

Source: Article
Status: Unprocessed
URL: https://github.com/santoshshinde2012/node-boilerplate

[https://opengraph.githubassets.com/7e654efcfded63a437fc0cc9e2d793cc79ef78f283df6b0957d556cbbf924ba3/santoshshinde2012/node-boilerplate](https://opengraph.githubassets.com/7e654efcfded63a437fc0cc9e2d793cc79ef78f283df6b0957d556cbbf924ba3/santoshshinde2012/node-boilerplate)

---

# Node-Typescript-Boilerplate

Skeleton for Node.js applications written in TypeScript

## Purpose

Our main purpose with this Skeleton is to start server application with node js and typescript.

Try it!! I am happy to hear your feedback or any kind of new features.

## Common Features

- Quick start
- Integrated eslint, prettier and husky
- Common Error Handler
- Common Response Handler
- Simple and Standard scaffolding
- Followed SOLID Principles
- Based on Typescript Syntax
- Simple Enviroment Configuration
- Global Enviroment Object
- Request/Response Encryption & Decryption Implementation
- Easily Add new feature
- Integrated winston Logger
- Production Ready Skeleton
- Follwed Production Ready Best Practices: Security
- Added only used npm modules
- Unit & Integration Test Cases

## Core NPM Module

- `express`, `@types/express`
- `@types/node`
- `typescript`
- `dotenv`
- `cors`
- `helmet`
- `http-status-codes`
- `winston`, `@types/winston`

## Start The application in Development Mode

- Clone the Application `git clone https://github.com/santoshshinde2012/node-boilerplate.git`
- Install the dependencies `npm install`
- Start the application `npm start`

## Start The application in Production Mode

- Install the dependencies `npm install`
- Create the build `npm run build`
- Start the application `npm run start:production`
- Before starting make sure to creat prod environment `.env.prod` file

## Project Structure

[Untitled](santoshshinde2012%20node-boilerplate%20Node%20Typescript%200394934967ee47e8bb535aedf4f6f2bf/Untitled%20Database%2006450cd43bd246ccb7fbe6158ac9f83e.csv)

## Workflow

![santoshshinde2012%20node-boilerplate%20Node%20Typescript%200394934967ee47e8bb535aedf4f6f2bf/boilerplate-workflow.png](santoshshinde2012%20node-boilerplate%20Node%20Typescript%200394934967ee47e8bb535aedf4f6f2bf/boilerplate-workflow.png)

## Encryption

Set the `APPLY_ENCRYPTION` environment variable to `true` to enable encryption.

## Global Environment Object

You can directly access the environment attributes in any component/file using global environment object. For more details please check file `src/global.ts`.

*Example*

To access the `applyEncryption` attribute from `Envionment` class to Response Handler, write `environment.applyEncryption`;

## Default System Health Status API

- `${host}/api/status/system` - Return the system information in response
- `${host}/api/status/time` - Return the current time in response
- `${host}/api/status/usage` - Return the process and system memory usage in response
- `${host}/api/status/process` - Return the process details in response
- `${host}/api/status/error` - Return the error generated object in response

## Refrences

- [Skeleton for Node.js Apps written in TypeScript](https://javascript.plainenglish.io/skeleton-for-node-js-apps-written-in-typescript-444fa1695b30)
- [Setup Eslint Prettier and Husky in Node JS Typescript Project](https://gist.github.com/santoshshinde2012/e1433327e5f7a58f98fe3e6651c4d5de)

## Notes

### 1. Why is my git pre-commit hook not executable by default?

- Because files are not executable by default; they must be set to be executable.

```
chmod ug+x .husky/*
chmod ug+x .git/hooks/*

```

### 2. [Production Best Practices: Security](https://expressjs.com/en/advanced/best-practice-security.html)

- Don’t use deprecated or vulnerable versions of Express
- Use TLS
- Use Helmet
- Use cookies securely
- Prevent brute-force attacks against authorization
- Ensure your dependencies are secure
- Avoid other known vulnerabilities
- Additional considerations

# Please connect with me on Twitter [@shindesan2012](https://twitter.com/shindesan2012) & [https://blog.santoshshinde.com](https://blog.santoshshinde.com/)