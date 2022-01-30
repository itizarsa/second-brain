# kentcdodds/bookshelf: Build a ReactJS App workshop

Source: Notes
Status: Unprocessed
URL: https://github.com/kentcdodds/bookshelf

[https://repository-images.githubusercontent.com/185924208/c6ee0280-c0fc-11ea-9457-d6c23a064acf](https://repository-images.githubusercontent.com/185924208/c6ee0280-c0fc-11ea-9457-d6c23a064acf)

---

# [Build an Epic React App  EpicReact.Dev](https://epicreact.dev/app)

![kentcdodds%20bookshelf%20Build%20a%20ReactJS%20App%20workshop%204d6cb13d38344f45b0d3d1e0197ad850/1f680.png](kentcdodds%20bookshelf%20Build%20a%20ReactJS%20App%20workshop%204d6cb13d38344f45b0d3d1e0197ad850/1f680.png)

**Building a full React application**

The React and JavaScript ecosystem is full of tools and libraries to help you build your applications. In this (huge) workshop we’ll build an application from scratch using widely supported and proven tools and techniques. We’ll cover everything about building frontend React applications, from the absolute basics to the tricky parts you'll run into building real world React apps and how to create great abstractions.

[kentcdodds%20bookshelf%20Build%20a%20ReactJS%20App%20workshop%204d6cb13d38344f45b0d3d1e0197ad850/68747470733a2f2f6b656e7463646f6464732e636f6d2f696d616765732f6570696372656163742d70726f6d6f2f65722d312e676966](kentcdodds%20bookshelf%20Build%20a%20ReactJS%20App%20workshop%204d6cb13d38344f45b0d3d1e0197ad850/68747470733a2f2f6b656e7463646f6464732e636f6d2f696d616765732f6570696372656163742d70726f6d6f2f65722d312e676966)

[kentcdodds%20bookshelf%20Build%20a%20ReactJS%20App%20workshop%204d6cb13d38344f45b0d3d1e0197ad850/68747470733a2f2f696d672e736869656c64732e696f2f6769746875622f776f726b666c6f772f7374617475732f6b656e7463646f6464732f626f6f6b7368656c662f76616c69646174652f6d61696e3f6c6f676f3d676974687562267374796c653d666c61742d737175617265](kentcdodds%20bookshelf%20Build%20a%20ReactJS%20App%20workshop%204d6cb13d38344f45b0d3d1e0197ad850/68747470733a2f2f696d672e736869656c64732e696f2f6769746875622f776f726b666c6f772f7374617475732f6b656e7463646f6464732f626f6f6b7368656c662f76616c69646174652f6d61696e3f6c6f676f3d676974687562267374796c653d666c61742d737175617265)

[kentcdodds%20bookshelf%20Build%20a%20ReactJS%20App%20workshop%204d6cb13d38344f45b0d3d1e0197ad850/68747470733a2f2f696d672e736869656c64732e696f2f6769746875622f616c6c2d636f6e7472696275746f72732f6b656e7463646f6464732f626f6f6b7368656c663f636f6c6f723d6f72616e6765267374796c653d666c61742d737175617265](kentcdodds%20bookshelf%20Build%20a%20ReactJS%20App%20workshop%204d6cb13d38344f45b0d3d1e0197ad850/68747470733a2f2f696d672e736869656c64732e696f2f6769746875622f616c6c2d636f6e7472696275746f72732f6b656e7463646f6464732f626f6f6b7368656c663f636f6c6f723d6f72616e6765267374796c653d666c61742d737175617265)

[kentcdodds%20bookshelf%20Build%20a%20ReactJS%20App%20workshop%204d6cb13d38344f45b0d3d1e0197ad850/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f6c6963656e73652d47504c253230332e302532304c6963656e73652d626c75652e7376673f7374796c653d666c61742d737175617265](kentcdodds%20bookshelf%20Build%20a%20ReactJS%20App%20workshop%204d6cb13d38344f45b0d3d1e0197ad850/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f6c6963656e73652d47504c253230332e302532304c6963656e73652d626c75652e7376673f7374796c653d666c61742d737175617265)

[kentcdodds%20bookshelf%20Build%20a%20ReactJS%20App%20workshop%204d6cb13d38344f45b0d3d1e0197ad850/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f636f64652532306f662d636f6e647563742d6666363962342e7376673f7374796c653d666c61742d737175617265](kentcdodds%20bookshelf%20Build%20a%20ReactJS%20App%20workshop%204d6cb13d38344f45b0d3d1e0197ad850/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f636f64652532306f662d636f6e647563742d6666363962342e7376673f7374796c653d666c61742d737175617265)

## Prerequisites

- You'll want experience with React before going through this material. The lessons get progressively more advanced. Once you hit something you're unfamiliar with, that's your cue to go back and review the other parts of EpicReact.Dev.

## System Requirements

- [git](https://git-scm.com/) v2.13 or greater
- [NodeJS](https://nodejs.org/) `12 || 14 || 15 || 16`
- [npm](https://www.npmjs.com/) v6 or greater

All of these must be available in your `PATH`. To verify things are set up properly, you can run this:

```
git --version
node --version
npm --version
```

If you have trouble with any of these, learn more about the PATH environment variable and how to fix it here for [windows](https://www.howtogeek.com/118594/how-to-edit-your-system-path-for-easy-command-line-access/) or [mac/linux](http://stackoverflow.com/a/24322978/971592).

## Setup

> If you want to commit and push your work as you go, you'll want to fork first and then clone your fork rather than this repo directly.
> 

After you've made sure to have the correct things (and versions) installed, you should be able to just run a few commands to get set up:

```
git clone https://github.com/kentcdodds/bookshelf.git
cd bookshelf
node setup

```

This may take a few minutes.

If you get any errors, please read through them and see if you can find out what the problem is. If you can't work it out on your own then please [file an issue](https://github.com/kentcdodds/bookshelf/issues/new) and provide *all* the output from the commands you ran (even if it's a lot).

If you can't get the setup script to work, then just make sure you have the right versions of the requirements listed above, and run the following commands:

```
npm install
npm run validate

```

If you are still unable to fix issues and you know how to use Docker

![kentcdodds%20bookshelf%20Build%20a%20ReactJS%20App%20workshop%204d6cb13d38344f45b0d3d1e0197ad850/1f433.png](kentcdodds%20bookshelf%20Build%20a%20ReactJS%20App%20workshop%204d6cb13d38344f45b0d3d1e0197ad850/1f433.png)

you can setup the project with the following command:

```
docker-compose up

```

It's recommended you run everything locally in the same environment you work in every day, but if you're having issues getting things set up, you can also set this up using [GitHub Codespaces](https://github.com/features/codespaces) ([video demo](https://www.youtube.com/watch?v=gCoVJm3hGk4)) or [Codesandbox](https://codesandbox.io/s/github/kentcdodds/bookshelf).

## Running the app

To get the app up and running (and really see if it worked), run:

```
npm start
```

This should start up your browser. If you're familiar, this is a standard [react-scripts](https://create-react-app.dev/) application.

You can also open the production deployment: [bookshelf.lol](https://bookshelf.lol/).

## Running the tests

```
npm test
```

This will start [Jest](https://jestjs.io/) in watch mode. Read the output and play around with it. The tests are there to help you reach the final version, however *sometimes* you can accomplish the task and the tests still fail if you implement things differently than I do in my solution, so don't look to them as a complete authority.

## Working through the exercises

To get started, run:

```
node go
```

This will allow you to choose which exercise you want to work on. From there, open the `INSTRUCTIONS.md` file and follow the instructions.

If you'd like to work on an extra credit, but you want to skip the preceding steps, you can run `node go` again:

```
node go
```

This will let you choose the next exercise or you can choose which part of the exercise you'd like to work on. This will update your `exercise` files to the correct version for you to work on that extra credit.

### Exercises

The exercises are in different branches. Each branch changes the `INSTRUCTIONS.md` file to contain instructions you need to complete the exercise.

The purpose of the exercise is **not** for you to work through all the material. It's intended to get your brain thinking about the right questions to ask me as *I* walk through the material.

### Helpful Emoji

![kentcdodds%20bookshelf%20Build%20a%20ReactJS%20App%20workshop%204d6cb13d38344f45b0d3d1e0197ad850/1f428.png](kentcdodds%20bookshelf%20Build%20a%20ReactJS%20App%20workshop%204d6cb13d38344f45b0d3d1e0197ad850/1f428.png)

![kentcdodds%20bookshelf%20Build%20a%20ReactJS%20App%20workshop%204d6cb13d38344f45b0d3d1e0197ad850/1f4b0.png](kentcdodds%20bookshelf%20Build%20a%20ReactJS%20App%20workshop%204d6cb13d38344f45b0d3d1e0197ad850/1f4b0.png)

![kentcdodds%20bookshelf%20Build%20a%20ReactJS%20App%20workshop%204d6cb13d38344f45b0d3d1e0197ad850/1f4af.png](kentcdodds%20bookshelf%20Build%20a%20ReactJS%20App%20workshop%204d6cb13d38344f45b0d3d1e0197ad850/1f4af.png)

![kentcdodds%20bookshelf%20Build%20a%20ReactJS%20App%20workshop%204d6cb13d38344f45b0d3d1e0197ad850/1f4dd.png](kentcdodds%20bookshelf%20Build%20a%20ReactJS%20App%20workshop%204d6cb13d38344f45b0d3d1e0197ad850/1f4dd.png)

![kentcdodds%20bookshelf%20Build%20a%20ReactJS%20App%20workshop%204d6cb13d38344f45b0d3d1e0197ad850/1f989.png](kentcdodds%20bookshelf%20Build%20a%20ReactJS%20App%20workshop%204d6cb13d38344f45b0d3d1e0197ad850/1f989.png)

![kentcdodds%20bookshelf%20Build%20a%20ReactJS%20App%20workshop%204d6cb13d38344f45b0d3d1e0197ad850/1f4dc.png](kentcdodds%20bookshelf%20Build%20a%20ReactJS%20App%20workshop%204d6cb13d38344f45b0d3d1e0197ad850/1f4dc.png)

![kentcdodds%20bookshelf%20Build%20a%20ReactJS%20App%20workshop%204d6cb13d38344f45b0d3d1e0197ad850/1f4a3.png](kentcdodds%20bookshelf%20Build%20a%20ReactJS%20App%20workshop%204d6cb13d38344f45b0d3d1e0197ad850/1f4a3.png)

![kentcdodds%20bookshelf%20Build%20a%20ReactJS%20App%20workshop%204d6cb13d38344f45b0d3d1e0197ad850/1f4aa.png](kentcdodds%20bookshelf%20Build%20a%20ReactJS%20App%20workshop%204d6cb13d38344f45b0d3d1e0197ad850/1f4aa.png)

![kentcdodds%20bookshelf%20Build%20a%20ReactJS%20App%20workshop%204d6cb13d38344f45b0d3d1e0197ad850/1f3c1.png](kentcdodds%20bookshelf%20Build%20a%20ReactJS%20App%20workshop%204d6cb13d38344f45b0d3d1e0197ad850/1f3c1.png)

![kentcdodds%20bookshelf%20Build%20a%20ReactJS%20App%20workshop%204d6cb13d38344f45b0d3d1e0197ad850/1f468-1f4bc.png](kentcdodds%20bookshelf%20Build%20a%20ReactJS%20App%20workshop%204d6cb13d38344f45b0d3d1e0197ad850/1f468-1f4bc.png)

![kentcdodds%20bookshelf%20Build%20a%20ReactJS%20App%20workshop%204d6cb13d38344f45b0d3d1e0197ad850/1f6a8.png](kentcdodds%20bookshelf%20Build%20a%20ReactJS%20App%20workshop%204d6cb13d38344f45b0d3d1e0197ad850/1f6a8.png)

Each exercise has comments in it to help you get through the exercise. These fun emoji characters are here to help you.

- **Kody the Koala**  will tell you when there's something specific you should do version
- **Marty the Money Bag**  will give you specific tips (and sometimes code) along the way
- **Hannah the Hundred**  will give you extra challenges you can do if you finish the exercises early.
- **Nancy the Notepad**  will encourage you to take notes on what you're learning
- **Olivia the Owl**  will give you useful tidbits/best practice notes and a link for elaboration and feedback.
- **Dominic the Document**  will give you links to useful documentation
- **Berry the Bomb**  will be hanging around anywhere you need to blow stuff up (delete code)
- **Matthew the Muscle**  will indicate that you're working with an exercise
- **Chuck the Checkered Flag**  will indicate that you're working with a final
- **Peter the Product Manager**  helps us know what our users want
- **Alfred the Alert**  will occasionally show up in the test failures with potential explanations for why the tests are failing.

### Workflow

- Checkout the exercise branch
- Read through the `INSTRUCTIONS.md`
- Start exercise
- Go through every mentioned file and follow the instructions from the emoji
- We all come back together
- I go through the solution and answer questions
- Move on to the next exercise.
- Repeat.

### App Data Model

- 
    
    User
    
    - id: string
    - username: string
- 
    
    List Item
    
    - id: string
    - bookId: string
    - ownerId: string
    - rating: number (-1 is no rating, otherwise it's 1-5)
    - notes: string
    - startDate: number (`Date.now()`)
    - finishDate: number (`Date.now()`)

> For convenience, our friendly backend engineers also return a book object on each list item which is the book it's associated to. Thanks backend folks!
> 

> /me wishes we could use GraphQL
> 

If your "database" gets out of whack, you can purge it via:

```
window.__bookshelf.purgeUsers()
window.__bookshelf.purgeListItems()
```

- 
    
    Book
    
    - id: string
    - title: string
    - author: string
    - coverImageUrl: string
    - pageCount: number
    - publisher: string
    - synopsis: string

## Troubleshooting

Running "node go" does not list any branches

This means there was something wrong when you ran the setup. Try running:

```
node ./scripts/track-branches.js

```

If you're still not getting the branches, then you can do this manually:

```
git branch --track "exercises/01-bootstrap" "origin/exercises/01-bootstrap"
git branch --track "exercises/02-styles" "origin/exercises/02-styles"
git branch --track "exercises/03-data-fetching" "origin/exercises/03-data-fetching"
git branch --track "exercises/04-authentication" "origin/exercises/04-authentication"
git branch --track "exercises/05-routing" "origin/exercises/05-routing"
git branch --track "exercises/06-cache-management" "origin/exercises/06-cache-management"
git branch --track "exercises/07-context" "origin/exercises/07-context"
git branch --track "exercises/08-compound-components" "origin/exercises/08-compound-components"
git branch --track "exercises/09-performance" "origin/exercises/09-performance"
git branch --track "exercises/10-render-as-you-fetch" "origin/exercises/10-render-as-you-fetch"
git branch --track "exercises/11-unit-testing" "origin/exercises/11-unit-testing"
git branch --track "exercises/12-testing-hooks-and-components" "origin/exercises/12-testing-hooks-and-components"
git branch --track "exercises/13-integration-testing" "origin/exercises/13-integration-testing"
git branch --track "exercises/14-e2e-testing" "origin/exercises/14-e2e-testing"

git pull --all

```

## Contributors

Thanks goes to these wonderful people ([emoji key](https://github.com/kentcdodds/all-contributors#emoji-key)):

[Untitled](kentcdodds%20bookshelf%20Build%20a%20ReactJS%20App%20workshop%204d6cb13d38344f45b0d3d1e0197ad850/Untitled%20Database%207a852417fb364f63922664bb3d699556.csv)

This project follows the [all-contributors](https://github.com/kentcdodds/all-contributors) specification. Contributions of any kind welcome!

## Workshop Feedback

Each exercise has an Elaboration and Feedback link. Please fill that out after the exercise and instruction.

At the end of the workshop, please go to this URL to give overall feedback. Thank you!

- Part 1: [https://kcd.im/bra1-ws-feedback](https://kcd.im/bra1-ws-feedback)
- Part 2: [https://kcd.im/bra2-ws-feedback](https://kcd.im/bra2-ws-feedback)
- Part 3: [https://kcd.im/bra3-ws-feedback](https://kcd.im/bra3-ws-feedback)
- Part 4: [https://kcd.im/bra4-ws-feedback](https://kcd.im/bra4-ws-feedback)