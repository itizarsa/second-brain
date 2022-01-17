# React Ruined Web Development | by Ivan Lučin | Building Productive | Building Productive

Source: Article
Status: Unprocessed
URL: https://medium.com/building-productive/react-ruined-web-development-dd65342a833f

![https://miro.medium.com/max/1200/1*Sz2lk_siFBKAR1NXC7GvGw.jpeg](https://miro.medium.com/max/1200/1*Sz2lk_siFBKAR1NXC7GvGw.jpeg)

---

Last week I attended [.debug](https://www.debug.hr/), a developers conference, where my company held a booth. The idea was to have a “change my mind” kind of setup, where we represent a radical idea, invite people to debate with us, and show them that we’re building some interesting stuff at **[Productive](https://www.productive.io/).**

We decided to go with this one:

My first opponent was this young lad on the right, who builds apps with React native.

Jokes aside, React is a fine library. It’s important in web development because it introduced declarative and reactive templates, a paradigm shift that everyone needed at the time. There was a problem with rendering engines and reactivity back then (6 or 7 years ago) and React solved it pretty well.

As a side note, Ember solved the same problem earlier. It wasn’t as performant, though, and the framework was too opinionated to catch up with the way React had done it.

> useEffect(makeMess)
> 

What happened after React gained popularity was a mess. It started a new trend in the community where everything revolves around hype, novelty, and creating new paradigm shifts. Every few months there were new libraries emerging, setting new standards of how we should write React web apps, yet solving problems that were, for the most part — already solved.

Let’s take “state management” as an example. Since React is missing a traditional dependency injection system (DI is achieved through component composition), the community had to solve this problem on its own. And it did. Over and over and again. Each new year brought a new set of standards.

![React%20Ruined%20Web%20Development%20by%20Ivan%20Luc%CC%8Cin%20Buildi%205bfa47cb45d4400ba087769f04c4f16f/1bV7RX21ktKJwmeyw2FmEnw.jpeg](React%20Ruined%20Web%20Development%20by%20Ivan%20Luc%CC%8Cin%20Buildi%205bfa47cb45d4400ba087769f04c4f16f/1bV7RX21ktKJwmeyw2FmEnw.jpeg)

React State Management’s motto — “New year, new me!”

React is just a rendering engine, and in a typical web app, you need many libraries to build a framework for a project — e.g. data layers, state management, routing, asset bundlers, and more.

The ecosystem behind React gave you too many choices of this sort, which fragmented the tech stack and caused the infamous “Javascript fatigue”.

One of the trends that also emerged was “framework comparison obsession”. JS frameworks were constantly compared with properties like rendering speed and memory footprint. This is irrelevant most of the time because a slow app is not caused by a slow JS framework, it’s caused by bad code.

![React%20Ruined%20Web%20Development%20by%20Ivan%20Luc%CC%8Cin%20Buildi%205bfa47cb45d4400ba087769f04c4f16f/1nFMIp6GM08msH4nyZGGYMA.jpeg](React%20Ruined%20Web%20Development%20by%20Ivan%20Luc%CC%8Cin%20Buildi%205bfa47cb45d4400ba087769f04c4f16f/1nFMIp6GM08msH4nyZGGYMA.jpeg)

The line for discussion getting longer and longer…

As with every trend that is taking over the world — this one went too far, damaging new generations of web developers. I’m wondering how it’s possible for a library to be the most relevant skill on an average web developer’s CV? Even worse, it’s not even a library but a module inside that library. React hooks are more often mentioned as a “skill” as opposed to some actual skills like code refactoring or code review.

Seriously?! When did we stop bragging about the important stuff?

Why don’t you tell me, for example, that you know:

## 🎖 How to make simple and readable code

… not by mentioning the most starred library on Github, but by showing me one or two of your finest snippets.

## 🎖 **How to manage state**

… not by mentioning a popular state management library (preferably ending with “X”), but by telling me why “data should go down and actions should go up”. Or why state should be modified where it was created and not deeper in the component hierarchy.

## 🎖 How to test your code

… not by telling me that you know Jest or QUnit, but by explaining why it’s hard to automate end-to-end tests and why minimal meaningful rendering tests are 10% the effort and 90% the benefit.

## 🎖 **How to release your code**

… not by mentioning that you use CI/CD (as every other project today that has more than one person working on it), but by explaining that deployment and release should be separate so you should code new stuff in a way that doesn’t mess with the old stuff and can be turned on remotely.

## 🎖 How to write reviewable code

… not by mentioning that you’re a “team player”, but by telling me that code review is just as hard on the reviewer’s side and that you know how to optimize your PRs for readability and clarity.

## 🎖 How to build solid project standards

… because unless you’re a one-man band, you’ll hate your life if you don’t follow strict standards and conventions in a project. You should tell me that naming is hard and the broader the scope of the variable, the more time you should invest in coming up with a good name for it.

## 🎖 How to review other people’s code

… because code review ensures product quality, reduces bugs and technical debt, builds common team knowledge, and more — but only if done thoroughly. Code review shouldn’t only be done top-down. It’s a great learning mechanism for less experienced team members.

## 🎖 How to find your way in any JS framework

… because it’s not about the GitHub stars, it’s about common principles that most of today’s JS frameworks share. Finding out about the pros and cons of other frameworks makes you understand your framework of choice better.

## 🎖 How to build MVPs

… because technology is only a tool for making products, not the process. Spending time on optimizing the process is always better than spending time on arguing about technology.

## 🎖 How to optimize: not too early, not too late

… because most of the time, optimization isn’t necessary at all.

## 🎖 How to pair-program

… because pair-programming is, like code review, the most important practice for knowledge sharing and building team cohesion. It’s also fun!

## 🎖 How to continuously refactor

… because every project has technical debt and you should stop whining about it and start refactoring. Every new feature should be preceded by a minor code refactoring. Big refactoring or rewrites never turn out well.

So yeah, that’s why I think React ruined web development. People at the conference were intrigued by the claim and joined the debate eagerly. I had a great conversation with few experienced React developers. Nobody agrees with the title of this article, saying “ruined” is too strong of a word. But most of them agree with the problems discussed in this article.

You can try to convince me that React isn’t that bad, and I will absolutely agree with you! 😄

But instead, let’s debate about the more important topics — **the work that we actually do as software engineers**.