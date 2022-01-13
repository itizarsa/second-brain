# 15. Systemizing kick-off

Source: Article
Status: Unprocessed
URL: https://world.hey.com/rjs/15-systemizing-kick-off-c05bbbf2

![https://world.hey.com/rjs/c05bbbf2/representations/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBCR2QvcWh3PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--79bf4588ecedf1a5f1313e07dcc78feb5f70deff/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaDdDRG9UY21WemFYcGxYM1J2WDJacGJHeGJCMmtDc0FScEFuWUNPZ3h4ZFdGc2FYUjVhUzA2Q25OMGNtbHdWQT09IiwiZXhwIjpudWxsLCJwdXIiOiJ2YXJpYXRpb24ifX0=--f2badd95ce31e495769e48a538e401dea1aca2ae/Screen%20Shot%202021-07-29%20at%202.32.55%20PM.png](https://world.hey.com/rjs/c05bbbf2/representations/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBCR2QvcWh3PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--79bf4588ecedf1a5f1313e07dcc78feb5f70deff/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaDdDRG9UY21WemFYcGxYM1J2WDJacGJHeGJCMmtDc0FScEFuWUNPZ3h4ZFdGc2FYUjVhUzA2Q25OMGNtbHdWQT09IiwiZXhwIjpudWxsLCJwdXIiOiJ2YXJpYXRpb24ifX0=--f2badd95ce31e495769e48a538e401dea1aca2ae/Screen%20Shot%202021-07-29%20at%202.32.55%20PM.png)

---

[Ryan Singer](https://world.hey.com/rjs)

[15%20Systemizing%20kick-off%2012575ab000f8409ba6f8241e1d641f2c/avatar-20210622183431000000-126024283](15%20Systemizing%20kick-off%2012575ab000f8409ba6f8241e1d641f2c/avatar-20210622183431000000-126024283)

Recently I tried a new exercise to systemize the way we kick off projects.

Kick-off is that moment when the person who shaped the work hands it off to the development team. It's an important moment in Shape Up because the dev team takes [full responsibility](https://basecamp.com/shapeup/3.1-chapter-10) for interpreting the pitch, defining tasks, and coming up with the concrete solution.

Shape Up can make it seem like you "just" give the shaped work to the team and off they go. In reality, there are a lot of anxieties to calm and questions to answer for hand-off to go smoothly.

The programmer is wondering:

- *Is this actually possible within the time frame they're giving me?*
- *What pieces do I have to implement and how do they fit together?*
- *What will I work on first?*
- *What happens if a part of this turns out to be harder than it looks?*

The manager handing off the pitch has concerns too:

- *How long will I wait before I see something that shows they understand the pitch?*
- *How can I know they're focused on the right things without micromanaging them?*

Very experienced teams find their own ways to negotiate these questions. At Basecamp, it was hard to even *see* these difficulties because the product team was so small and senior.

The challenges become more evident when (1) the programmers are less experienced or (2) the product team is much bigger.
When senior programmers approach a problem, they look over the whole, chunk it into separate areas, and target the hairiest area first — which could be somewhere in the middle of the pitch. Junior programmers tend to work top-to-bottom. Their noses aren't as trained to sniff out interdependencies and separations of concerns, so they pick the easiest starting point and plow forward from there. This causes them to hit critical unknowns unexpectedly and much later in the project.

For larger companies, the problem is they can't wait around for dozens of different teams to organically find their own way. Scale depends on modularity — on systematizing and doing things the same way every time.

Which brings me back to the new kick-off exercise. On the one hand it's a prescribed process, which can help less experienced programmers. And since the process is prescribed, it's also reproducible at scale.

Here's what the exercise looked like.

First, the programmer read the pitch and the shaper answered questions about it.

Then, the programmer dumped every task they could think of into a box. This helped them consider the pitch as a whole by turning the whole thing into rough implementation tasks, before they started on any one area.

Next, the programmer dragged work together into groups by asking themselves which tasks can be completed together, in isolation of the rest. This guided them toward dividing the work into separate concerns, whether they have trained those muscles or not.

1. The number of boxes is fixed. There are no more than ten. This makes sure that the groups are at the right level of abstraction to start.
2. The boxes are all **unnamed** at first. They only get names **after** they are filled. This ensures that the programmer looks at the actual work to decide what belongs together instead of using pre-conceived categories.

After the boxes were populated, the programmer gave each one a name. These named boxes are the [scopes](https://basecamp.com/shapeup/3.3-chapter-12) in Shape Up.

Now the programmer had a way to look at the work from a higher vantage point, with short-hand names for each piece. In the next step, they asked themselves: are any of these more unknown than the others?

We're learning that seeing all of the scopes together helps to do this, because the question of "what is unknown" is relative. It can be easier to first spot all the things that are routine and familiar, and what's left are the unknowns.

In this prototype, the programmer used a red outline to flag the scopes with unknowns.

Finally, the programmer chose a starting point by asking themselves how they can get into the most unknown areas as early as possible. This is another example of externalizing what senior programmers do in their heads.

This all happened in less than a day, without touching any code:

Afterward, our programmer described his experience like this:

> [Before doing this] conceptually, I understood the pitch, but I couldn’t really speak to what should be worked on first … what goes together … what might we be able to be cut if we’re hitting our six weeks … or how to communicate with you if we need more time or less scope.
> 

> I haven’t written any code, but my feelings have drastically changed about am I going to be able to deliver this well within the timeframe and am I gonna deliver everything that’s wanted.
> 

I wanted to share this here so other Shape Up teams can give it a try. After tweeting a summary of this technique, I already heard from a couple teams who are eager to apply it. I'd love to hear your questions, observations, experiences, or anything else if this seems like something that might be useful for your team.