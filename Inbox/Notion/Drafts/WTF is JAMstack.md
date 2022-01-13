# WTF is JAMstack?

Source: Website
Status: Unprocessed
URL: https://jamstack.wtf/

![https://jamstack.wtf/postcard.png](https://jamstack.wtf/postcard.png)

---

![postcard.png](WTF%20is%20JAMstack%2032172b0f903844ff91413fd0a4f5a504/postcard.png)

JAMstack is revolutionising the way we think about workflow by providing a simpler developer experience, better performance, lower cost and greater scalability.

This simple guide will help you understand why it exists and how to get started.

### Table of contents

1. [What is JAMstack?](https://jamstack.wtf/)

## What is JAMstack

### Meaning

JAM stands for JavaScript, API & Markup.

> "A modern web development architecture based on client-side JavaScript, reusable APIs, and prebuilt Markup"— Mathias Biilmann (CEO & Co-founder of Netlify).
> 

### JavaScript

Dynamic functionalities are handled by JavaScript. There is no restriction on which framework or library you must use.

### APIs

Server side operations are abstracted into reusable APIs and accessed over HTTPS with JavaScript. These can be third party services or your custom function.

### Markup

Websites are served as static HTML files. These can be generated from source files, such as Markdown, using a Static Site Generator.

### Benefits

Here are the main benefits provided by the JAMstack

### Faster performance

Serve pre-built markup and assets over a CDN

### More secure

No need to worry about server or database vulnerabilities

### Less expensive

Hosting of static files are cheap or [even free](https://netlify.com/)

### Better developer experience

Front end developers can focus on the front end, without being tied to a monolithic architecture. This usually means quicker and more focused development

### Scalability

If your product suddenly goes viral and has many active users, the CDN seamlessly compensates

### Best practices

The following tips will help you leverage the best out of the stack.

### Content delivery network

Since all the markup and assets are pre-built, they can be served via CDN. This provides better performance and easier scalability.

[Learn more](https://www.cloudflare.com/learning/cdn/what-is-a-cdn/)

### Atomic deploys

Each deploy is a full snapshot of the site. This helps guarantee a consistent version of the site globally.

[Learn more](https://buddy.works/blog/introducing-atomic-deployments#what-are-atomic-deployments)

### Cache invalidation

Once your build is uploaded, the CDN invalidates its cache. This means that your new build is live in an instant.

[Learn more](https://www.netlify.com/blog/2015/09/11/instant-cache-invalidation/)

### Everything in version control

Your codebase lives in Version Control System, such as Git. The main benefits are: change history of every file, collaborators and traceability.

[Learn more](https://www.atlassian.com/git/tutorials/what-is-version-control)

### Automated builds

Your server is notified when a new build is required, typically via webhooks. Server builds the project, updates the CDNs and the site is live.

[Learn more](https://www.agilealliance.org/glossary/automated-build)

### Workflow

Here's how an ideal JAMstack workflow would look like

### Timeline

A brief history of stack shows its growth in popularity

A small group of developers believe that Static sites don't have to be static and the term "JAMstack" comes to life.

The modern web revolution starts prioritising the importance of performance, scalability and developer experience. The term JAMstack starts to be adopted by a wider group of developers and the first enterprise JAMstack projects are announced.

Tools like Netlify, Gatsby and Contentful have helped promote the term and the community is rapidly growing. This was also the year of the first JAMstack Conference.

## Getting started

### Development

However you decide to generate your HTML assets is up to you. The three most common approaches are:

### Hand coding

Simple and effective method of writing HTML, it's ideal for super simple pages.

Most JAMstack sites are powered by a static site generator. There's no enforcement on which SSG you decide to use.

### Frontend Framework

Most frameworks don't output static HTML files, however it is possible to do that but it requires more tooling experience and maintenance.

### Deployment

Your built site needs to be hosted somewhere. There are great services that provides this for free and with ease.

### Dynamic parts

JAMstack websites don't have to be static. There are great services available to help bring some dynamic data to your product.

### Custom functions

You can also abstract your own functions into reusable APIs. For this you can use [AWS lambda functions](https://aws.amazon.com/lambda/features/) or [Netlify Functions](https://functions.netlify.com/examples/)

### Custom data

As you add features to your site, you may want to store user profiles, shopping cart data, game levels, or other dynamic data. Get started for free with [FaunaDB Serverless GraphQL](https://fauna.com/)

### Comments

Many JAMstack products have dynamic comment sections. These are typically used on blogs

### Forms

A great way to interact with your audience

### E-Commerce

Setting up an online store on the JAMstack has never been easier

### Search

Rely on third party services to integrate a search functionality

### CMS

JAMstack sites can also be controlled via a Content Management System, these are typically known as Headless CMS. Once a change in the CMS is made, a new build of your site will be triggered and then deployed as static assets.