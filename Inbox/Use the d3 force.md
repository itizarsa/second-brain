# Use the d3 force

Source: Article
Status: Unprocessed
URL: https://wattenberger.com/blog/d3-force

Usually, we position elements on our web pages in static, explicit places. But what if we want to make them feel more alive, or move them based on loose rules?

Then, we have to **use the force**. The [d3-force](https://github.com/d3/d3-force).

[d3-force](https://github.com/d3/d3-force) is a module in the [d3.js](https://github.com/d3/d3) API that runs a simulation, moving a set of particles on every "tick".

To create a new simulation, we can use `d3.forceSimulation()`.

`d3.forceSimulation()` takes one parameter: the array of particles that we want to move about. These particles will each be an object:

`const particles = [`

`// data about the particle here, for example:`

`date: "2020-11-23",`

`d3.forceSimulation(particles)`

To start our particles in a specific location, we can specify that by adding an `x` and `y` key to the object. If we don't specify an initial location, our particles will start in a [Phyllotaxis arrangement](https://observablehq.com/@d3/force-layout-phyllotaxis).

Read about [how a spiral starting position could be beneficial](https://wattenberger.com/blog/spirals) (and also how unoriginal I am with article names)

Once our simulation is created, we'll move our particles according to a set of **forces**.

There are several built-in forces that we can use with a d3-force simulation. The first I'll teach you is the **x force**.

The **x force** urges our particles to move towards a specific x (horizontal) position.

Add new **x forces** (in the **Simulation Control Panel**) to our active forces, and move the sliders to change the targeted x position.

When adding a new force, we call the simulation's `.force()` method, passing two parameters: a name (for later cancelling the force) and the force function itself.

We can also specify a function, using the provided parameters (the particle, and the index of the particle). Try this by clicking **buckets** or **in a line**.

But this **x force** isn't very powerful on its own. Let's learn some other ones! Much to learn you still have, my young padawan.

The **y force** is very similar to the **x force**, but moves our particles vertically.

Try moving the **y force** around.

This is my favorite force! The **collide force** checks each particle to see if it's colliding with another particle. If so, it will move both particles away from each other.

`.force("collide", d3.forceCollide())`

Our particles have run amok! Let's learn a way to keep them from spreading out too far.

We can use as many **forces** as we want! Let's add an **x force** and **y force** to keep our particles close to the middle of our screen.

`d3.forceSimulation()`

`.force("x", d3.forceX())`

`.force("y", d3.forceY())`

`.force("collide", d3.forceCollide())`

Some forces may counteract each other. Control which one is stronger by changing their `strength`.

`d3.forceSimulation()`

`.force("x", d3.forceX().strength())`

`.force("y", d3.forceY().strength())`

`.force("collide", d3.forceCollide().strength())`

The simulation works by running a **tick** function on every layout frame. We've paused the simulation using `simulation.stop()` - hit the **tick** button (in the top left) to run `simulation.tick()` and step through one frame at a time.

Our **collide force** can also run multiple times per frame - set the number of times it runs by changing its `iterations`. This can help with jittering simulations, where the **collide force** fights against other forces.

`d3.forceSimulation()`

`.force("x", d3.forceX())`

`.force("y", d3.forceY())`

`.force("collide", d3.forceCollide().iterations())`

The **radial force** moves the particles towards the edge of a circle. We can change the `radius` of that circle, and also its `x` and `y` position.

The **radial force** doesn't evenly space our particles, so sometimes we'll want to add another force (try adding a **collide force**) to prevent our particles from clumping all in one place.

The **many body force** affects how the particles interact with each other and is the closest we get to simulate physics - a negative `strength` mimics repulsion and a positive `strength` mimics gravity.

Because this force causes particles to affect each other, we can get interesting behavior like clumping. See if you can cause our particles to glom into distinct groups.

The **center force** may seem like a repeat of our **x force** and **y force**, but it's actually very different.

Instead of zooming our particles around, the **center force** will move the entire particle system so that it's centered at a specific spot. This is helpful for keeping our particles centered in our screen, but not modifying other active forces.

The **link force** is great for network diagrams, similar to [this infographic from the South China Morning Post](https://www.scmp.com/infographics/article/1670384/infographic-satellites-network).

![Use%20the%20d3%20force%20223cbefb3f7f43f092f9b1c07e6b5c6f/scmp.e3e870d6.png](Use%20the%20d3%20force%20223cbefb3f7f43f092f9b1c07e6b5c6f/scmp.e3e870d6.png)

We pass an array of links (objects with a `source` and a `target`) to tell our **link force** which particles are connected.

`d3.forceSimulation()`

`.force("link", d3.forceLinks([`

`{source: 0, target: 1},`

`{source: 1, target: 2},`

`// ...`

These values correspond to each particle's `id`, which defaults to its index in the particles array.

Here is where we learn the true power of forces - we can make custom ones to move our particles in any way we can imagine!

For example, we could create a **bounding force** that keeps our particles within x and y positions.

This force could be really helpful for making sure our particles stay on screen.

Go and make your own custom forces! If you make your own force, ping me on [Twitter](http://twitter.com/wattenberger) and I'll start a list here!