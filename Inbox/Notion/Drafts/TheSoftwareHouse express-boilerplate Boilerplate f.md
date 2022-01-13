# TheSoftwareHouse/express-boilerplate: Boilerplate for setting up express.js applications

Source: Notes
Status: Unprocessed
URL: https://github.com/TheSoftwareHouse/express-boilerplate

[https://opengraph.githubassets.com/eff9c2453ca419f65c56524ffec8c4806dbca70ccc477317413b8ac194cc01a0/TheSoftwareHouse/express-boilerplate](https://opengraph.githubassets.com/eff9c2453ca419f65c56524ffec8c4806dbca70ccc477317413b8ac194cc01a0/TheSoftwareHouse/express-boilerplate)

---

![TheSoftwareHouse%20express-boilerplate%20Boilerplate%20f%204e4e51cda0704ebda7e4138919d6d0bd/logo.svg](TheSoftwareHouse%20express-boilerplate%20Boilerplate%20f%204e4e51cda0704ebda7e4138919d6d0bd/logo.svg)

Current travis build:

[TheSoftwareHouse%20express-boilerplate%20Boilerplate%20f%204e4e51cda0704ebda7e4138919d6d0bd/68747470733a2f2f7472617669732d63692e636f6d2f546865536f667477617265486f7573652f657870726573732d626f696c6572706c6174652e7376673f6272616e63683d6d6173746572](TheSoftwareHouse%20express-boilerplate%20Boilerplate%20f%204e4e51cda0704ebda7e4138919d6d0bd/68747470733a2f2f7472617669732d63692e636f6d2f546865536f667477617265486f7573652f657870726573732d626f696c6572706c6174652e7376673f6272616e63683d6d6173746572)

A highly scalable and a focus on performance and best practices boilerplate code for Nodejs and TypeScript based web applications.

Start a new application in seconds!

### Features

- 
    
    Quick scaffolding
    
    Create actions, routes, and models - right from the CLI using Plop micro-generator framework.
    
- 
    
    TypeScript
    
    The best way to write modern applications. Code is easier to understand. It is now way more difficult to write invalid code as was the case in dynamically typed languages
    
- 
    
    Dependency injection
    
    DI is a central part of any nontrivial application today and is the core of this project.
    
- 
    
    Static code analysis
    
    Focus on writing code, not formatting! Code formatter and linter keeps the code clean which makes work and communication with other developers more effective!
    

**Note** If you have discovered a bug or have a feature suggestion, feel free to create an issue on [Github](https://github.com/TheSoftwareHouse/express-boilerplate/issues).

Don't forget to star or fork this if you liked it.

### Configuration

After checkout of a repository, please perform the following steps in exact sequence:

1.  
    
    Copy docker-compose.override
    
    ```
    $ cp docker-compose.override.yml.dist docker-compose.override.yml
    
    ```
    
2.   
    
    Create `.env` file from `.env.dist`
    
    ```
    $ cp .env.dist .env
    
    ```
    
    Remember to fill up required values in `.env`
    
3. 
    
    Run `npm i`
    
4. 
    
    Run `npm run docker-build`
    
5. 
    
    Run watch - `npm run watch`
    

### Dev setup

This app is fully dockerized, so in order to use it you have to have docker and docker-compose installed. What's more you need to have npm in order to run npm scripts.

1.  
    
    In order to run the whole app type:
    
    ```
    npm run start
    
    ```
    
2.  
    
    In order to watch files for dev purpose type:
    
    ```
    npm run watch
    
    ```
    
3.  
    
    If you need to close all containers run:
    
    ```
    npm run down
    
    ```
    
4.  
    
    To get into Docker container's shell:
    
    ```
    npm run shell
    
    ```
    

### Code generation

We're using Plop for routes, models, actions, graphql (queries and mutations), commands and handlers generation.

```
npm run plop

```

### Code style

We're using Prettier and ESLint to keep code clean. In order to reformat/check code run:

```
npm run lint
npm run format

```

### Database migrations

Migrations should be stored inside migrations directory.

Easiest way to create a migration is to generate it from entity/ies:

```
npm run generate-migration -- <migration-name>

```

This should generate a migration for all connected entities.

### Adminer setup

Adminer is configured in `docker-compose.override.yml` and should work out of the box on port 8080. To login to adminer use the following values:

```
Database type: postgres
Server: postgres
User: postgres
Password: password
Database: app

```

Of course, if any of this is changed via configuration or otherwise, then these changes must be reflected here as well.

### GraphQL

Boilerplate has GraphQL support. Apollo server runs as a middleware and should be available locally under:

```
http://localhost:1337/graphql

```

To add new query/mutation run relevant `plop` commands and then:

1. Modify `schema.gql` under `graphql/schema.gql`
2. Run codegen: `npm run generate-schema`
3. Restart watcher / API

### Debugging

### VS Code

There is `launch.json` configuration inside `editors/vsc` directory. Just copy it and create new debugger to make it work with vsc :)

### Tests

There are two types of tests:

- integration: `npm run integration`
- units: `npm run units`

### **Issues:**

If you notice any issues while using, let as know on **[github](https://github.com/TheSoftwareHouse/express-boilerplate/issues)**. Security issues, please sent on **[email](mailto:security.opensource@tsh.io)**

### **You may also like our other projects:**

- **[RAD Modules](https://github.com/TheSoftwareHouse/rad-modules)**
- **[RAD Modules Tools](https://github.com/TheSoftwareHouse/rad-modules-tools)**
- **[Serverless Boilerplate](https://github.com/TheSoftwareHouse/serverless-boilerplate)**
- **[Kakunin](https://github.com/TheSoftwareHouse/Kakunin)**
- **[Babelsheet-js](https://github.com/TheSoftwareHouse/babelsheet-js)**
- **[Fogger](https://github.com/TheSoftwareHouse/fogger)**

### **About us:**

**[The Software House](https://tsh.io/pl)**

![TheSoftwareHouse%20express-boilerplate%20Boilerplate%20f%204e4e51cda0704ebda7e4138919d6d0bd/tsh.png](TheSoftwareHouse%20express-boilerplate%20Boilerplate%20f%204e4e51cda0704ebda7e4138919d6d0bd/tsh.png)

### License

[TheSoftwareHouse%20express-boilerplate%20Boilerplate%20f%204e4e51cda0704ebda7e4138919d6d0bd/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f6c6963656e73652d4d49542d3464633731662e737667](TheSoftwareHouse%20express-boilerplate%20Boilerplate%20f%204e4e51cda0704ebda7e4138919d6d0bd/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f6c6963656e73652d4d49542d3464633731662e737667)

This project is licensed under the terms of the [MIT license](https://github.com/TheSoftwareHouse/express-boilerplate/blob/main/LICENSE).