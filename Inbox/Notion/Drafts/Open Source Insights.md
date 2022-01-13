# Open Source Insights

Source: Website
Status: Unprocessed
URL: https://deps.dev/

Open Source Insights is an experimental project by Google.

Your software and your users rely not only on the code you write, but also on the code your code depends on, the code *that* code depends on, and so on. An accurate view of the complete dependency graph is critical to understanding the state of your project. And it’s not just code: you need to know about security vulnerabilities, licenses, recent releases, and more.

New

## Dive deeper into security advisories

We've heard your feedback, and we're excited to announce we have added a dedicated security advisory page! We've included more information about the advisory, including the severity and which package(s) the advisory affects. We have more improvements coming your way soon, such as fix path analysis and statistics.

Take a look, and let us know what you think!

New

## Explore dependencies using our new graph view

Transitive dependencies can be tricky to navigate, but we're here to help! There is a new graph view tool to let you visualize them. What's here is just the first cut of the tool, though, so stay tuned for updates and new features. To try it out, navigate to a package, click on Dependencies, and switch to the graph view.

## Seeing the big picture can be difficult—but it shouldn’t be

The Open Source Insights page for each package shows the full dependency graph and updates it every day. The information provided can help you make informed decisions about using, building, and maintaining your software.

With Open Source Insights, you can actually see the dependency graph for a package, then isolate the paths to a particular dependency. Or see whether a vulnerability in a dependency might affect your code. Or compare two versions of a package to see how the dependencies have changed in a new release.

![Open%20Source%20Insights%2082d8f2e84a384a61bc561064854cb034/napkins-gears.a6cf89f5.png](Open%20Source%20Insights%2082d8f2e84a384a61bc561064854cb034/napkins-gears.a6cf89f5.png)

## How it works

The service repeatedly examines sites such as [github.com](https://github.com/), [npmjs.com](https://npmjs.com/), and [pkg.go.dev](https://pkg.go.dev/) to find up-to-date information about open source software packages. Using that information it builds for each package the full dependency graph from scratch—not just from package lock files—connecting it to the packages it depends on and to those that depend on it. And then does it all again to keep the information fresh. This transitive dependency graph allows problems in any package to be made visible to the owners and users of any software they affect.