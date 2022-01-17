# Questionable Advice: The Trap of The Premature Senior – charity.wtf

Source: Article
Status: Unprocessed
URL: https://charity.wtf/2020/11/01/questionable-advice-the-trap-of-the-premature-senior/

![https://i0.wp.com/charity.wtf/wp-content/uploads/2021/01/mepurp-15.jpg?fit=902%2C1200&ssl=1](https://i0.wp.com/charity.wtf/wp-content/uploads/2021/01/mepurp-15.jpg?fit=902%2C1200&ssl=1)

---

> I’ve been at my current job for three years, and I am suddenly, accidentally, the most senior engineer on the team. I spend my days handling things like bootcamps, mentoring, architecture, and helping other engineers carve off meaningful work. This has taken a huge toll on the kind of work I want to do as an IC. I still enjoy writing and shipping features, and I am not a manager, but now I feel like I spend my days conducting meetings, interviewing, and unblocking others constantly instead of writing code myself. What should I do? How can I deal with this situation in an effective manner? How can I keep from getting burned out on zoom? How can I reclaim more of my time to write code for myself, without sacrificing my influence? Should I get a new job? I have thought about going out and getting a new job, but I really like having a say at a high level. Here I get looped into all of the most important decisions and meetings. If I get a new job, how can I avoid starting over at the bottom of the heap and just taking assignments from other people? P.S., this is my first job.
> 

Get a new job.

Yes, you will reset your seniority and have to earn it all over again. Yes, it will be uncomfortable and your ego will be cranky over it. Yes, you will be at the bottom of the heap and take assignments from other people for a while. Yes, you should do it anyway.

What you are experiencing now is the alluring comfort of premature seniority. You’re the smartest kid in the room, you know every corner of the system inside and out, you win every argument and anticipate every objection and you are part of every decision and you feel so deeply, pleasingly needed by the people around you.

It’s a trap.

![Questionable%20Advice%20The%20Trap%20of%20The%20Premature%20Seni%2092e3c65f07534ddab4e606c54d3947f1/quit.png](Questionable%20Advice%20The%20Trap%20of%20The%20Premature%20Seni%2092e3c65f07534ddab4e606c54d3947f1/quit.png)

Get the fuck out of there.

There is a world of distance between being expert in *this system* and being an actual expert in your chosen craft. The second is seniority; the first is merely .. familiarity

Deep down I think you know this, and feel a gnawing insecurity over your position; why else would you have emailed me? *You were right.* Treasure that uneasy feeling in your gut, that discomfort in the face of supreme comfortable-ness. It will lead you to a long and prosperous career as an engineer if you learn to trust it.

Think of every job like an escalator — a 50-foot high escalator that takes about two years to ride to the top. But once you’ve summited, you stall out. You can either stay and wander on that floor, or you can step to the left and pick another escalator and ride it up another 50 feet. And another.

In my mind, someone becomes a real senior engineer after they’ve done this about three times. 2-3 teams, stacks, languages, and roles, over a 5-8 year period, and then they’re solidly baked. There are insights you can derive from having seen problems solved in a few different ways that you can’t with only a single point of reference.

You don’t become a senior engineer at the 50-foot ascent, no matter how thoroughly you know the landscape. You become a senior engineer somewhere well over 100 feet, with a couple of lane changes under your belt.

The act of learning a new language and/or stack is itself an important skill. Experiencing how different orgs ship code in vastly different ways is how you internalize that there’s no one blessed path, only different sets of tradeoffs, and how you learn to reason about those tradeoffs.

![Questionable%20Advice%20The%20Trap%20of%20The%20Premature%20Seni%2092e3c65f07534ddab4e606c54d3947f1/powerskillsjob.png](Questionable%20Advice%20The%20Trap%20of%20The%20Premature%20Seni%2092e3c65f07534ddab4e606c54d3947f1/powerskillsjob.png)

And it is *good* for us to start over with beginner eyes. It’s humbling, it’s clarifying, it’s a cleanse for the soul. If you get too attached to feeling senior, to feeling necessary, you will undervalue the virtues of fresh eyes and questioning, of influence without authority. It is *good* for you to practice uncertainty and influencing others without the cheat codes of deep familiarity.

Nobody wants to work with seniors who clutch their authority with a white knuckled grip. We want to work with those who wear it lightly, who remember what it was like in our shoes.

Ultimately, this is a strong argument for building our teams behind a Rawlsian [veil of ignorance](https://en.wikipedia.org/wiki/Veil_of_ignorance) concerning our own place in the pecking order. Starting fresh yourself will help you build teams where it is not miserable to be a beginner, where beginners’ contributions are recognized, where even beginners do not simply “take orders”, as you said. Because *literally nobody* wants that, including the beginners you are working with on your teams today.

After you have gotten a new job or two, and proven to yourself that you can level up again and master new stacks and technologies, that fretful inner voice questioning whether you deserve the respect you receive or not will calm down. You will have proven to yourself that your success wasn’t just a one-off, that you can be dropped into any situation, learn the local ropes and succeed. You will be a senior engineer.

Get the fuck out of there. Go. <3

![Questionable%20Advice%20The%20Trap%20of%20The%20Premature%20Seni%2092e3c65f07534ddab4e606c54d3947f1/selfie-15.jpg](Questionable%20Advice%20The%20Trap%20of%20The%20Premature%20Seni%2092e3c65f07534ddab4e606c54d3947f1/selfie-15.jpg)

Over the past couple of weeks I’ve been tweeting a LOT about lead time to deploy: the interval encompassing the time from when the code gets written and when it’s been deployed to production. Also described as “how long it takes you to run CI/CD.”

How important is this?

**Fucking central.**

Here is a quickie thread from this week, or just go read “Accelerate” like everybody already should have.

- 
    
    > * swift deploys let you ship a single changeset by a single dev at a time* making it easy to isolate the owner of any problem* preventing the blast radius from expanding* and making it easy to fix while the intended effects of the code are fresh in their mind— Charity Majors (@mipsytipsy) December 28, 2020
    > 

It’s nigh impossible to have a high-performing team with a long lead time, and becomes drastically easier with a dramatically shorter lead time.

![Questionable%20Advice%20The%20Trap%20of%20The%20Premature%20Seni%2092e3c65f07534ddab4e606c54d3947f1/deploy-banner-violet.png](Questionable%20Advice%20The%20Trap%20of%20The%20Premature%20Seni%2092e3c65f07534ddab4e606c54d3947f1/deploy-banner-violet.png)

**Shorter is always better. 
 One mergeset per deploy. 
 Deploy should be automatic.**

And it should clock in under 15 minutes, all the way from “merging!” to “deployed!”.

Now some people will nod and agree here, and others freak the fuck out. “FIFTEEN MINUTES?” they squall, and begin accusing me of making things up or working for only very small companies. Nope, and nope. There are no magic tricks here, just high standards and good engineering, and the commitment to maintaining your goals quarter by quarter.

If you get CI/CD right, a lot of other critical functions, behaviors, and intuitions are aligned to be comfortably successful and correct with minimal effort. If you get it wrong, you will spend countless cycles chasing pathologies. It’s like choosing to eat your vegetables every day vs choosing a diet of cake and soda for fifty years, then playing whackamole with all the symptoms manifesting on your poor, mouldering body.

![Questionable%20Advice%20The%20Trap%20of%20The%20Premature%20Seni%2092e3c65f07534ddab4e606c54d3947f1/deploy_at_will.png](Questionable%20Advice%20The%20Trap%20of%20The%20Premature%20Seni%2092e3c65f07534ddab4e606c54d3947f1/deploy_at_will.png)

Is this ideal achievable for every team, on every stack, product, customer and regulatory environment in the world? No, I’m not being stupid or willfully blind. But I suggest pouring your time and creative energy into figuring out how closely you can approximate the ideal given what you have, instead of compiling all the reasons why you can’t achieve it.

Most of the people who tell me they can’t do this are quite wrong, turns out. And even if you can’t down to 15 minutes, ANY reduction in lead time will pay out massive, compounding, benefits to your team and adjacent teams forever and ever.

So — what was it you said you were working on right now, exactly? that was so important?

> “Cutting my build time by 90%!” — you
> 

Huzzah.

So let’s get you started! Here, courtesy of my twitterfriends, is a long compiled list of Likely Suspects and CI/CD Offenders, a long list of anti-patterns, and some unresolved personal pain & suffering to hunt down and question when your build gets slow..

15 minutes or bust, baby!

> off the top of my head ...* building a new AMI* using EBS* using lots of any AWS calls, really* not parallelizing tests* tests that take several seconds to init* setup/teardown of dbs* importing test data* selenium and other UX tests* rsyncing sequentiallywhat else? https://t.co/Kurr5d42y7— Charity Majors (@mipsytipsy) December 23, 2020
> 

Where it all started: what keeps you from getting under 15 minute CI/CD runs?

### Generally good advice.

![Questionable%20Advice%20The%20Trap%20of%20The%20Premature%20Seni%2092e3c65f07534ddab4e606c54d3947f1/friday.png](Questionable%20Advice%20The%20Trap%20of%20The%20Premature%20Seni%2092e3c65f07534ddab4e606c54d3947f1/friday.png)

- [Instrument your build pipeline with spans and traces](https://www.infoq.com/presentations/honeycomb-build-ssc/) so you can see where all your time is going. ALWAYS. Instrument.
- Order tests by time to execute and likelihood of failure.
- Don’t run all tests, only tests affected by your change
- Similarly, reduce build scope; if you only change front-end code, only build/test/deploy the front end, and for heaven’s sake don’t fuss with all the static asset generation
- Don’t hop regions or zones any more than you absolutely must.
- Prune and expire tests regularly, don’t wait for it to get Really Bad
- Combine functionality of tests where possible — tests need regular massages and refactors too
- Pipeline, pipeline, pipeline tests … with care and intention
- You do not need multiple non-production environment in your CI/CD process. **Push your artifacts to S3 and pull them down from production.** Fight me on this
- Pull is preferable to push. (see below)
- Set a time elapsed target for your team, and give it some maintenance any time it slips by 25%

> this seems to get asked a lot, so i'm going to retweet myself. if you're designing a deploy or distribution process at scale, pull is superior to push in most cases. https://t.co/7zqQC2Rom6— Charity Majors (@mipsytipsy) December 23, 2020
> 

### The usual suspects

- tests that take several seconds to init
- setup/teardown of databases (HINT try ramdisks)
- importing test data, seeding databases, sometimes multiple times
- rsyncing sequentially
- rsyncing in parallel, all pulling from a single underprovisioned source
- long git pulls (eg cloning whole repo each time)
- CI rot (eg large historical build logs)
- poor teardown (eg prior stuck builds still running, chewing CPU, or artifacts bloating over time
- integration tests that spin up entire services (eg elasticsearch)
- npm install taking 2-3 minutes
- bundle install taking 5 minutes
- resource starvation of CI/CD system
- not using containerized build pipeline
- …(etc)

> You can still deploy frequently/continuously to robots in production, but it took us a couple years to build a platform & culture that let us (sort of) pretend we were working on websites. I think this is probably a startup someone should do, I would have bought it.— Paul Liu (@pwyliu) December 24, 2020
> 

Continuous deployment to industrial robots in prod?? Props, man.

### Not properly separating the streams of “Our Software” (changes constantly) vs “infrastructure” (changes rarely)

- running cloudformation to setup new load balancers, dbs, etc for an entire acceptance environment
- docker pulls, image builds, docker pushes container spin up for tests

### “Does this really go here?”

- packaging large build artifacts into different format for distribution
- slow static source code analysis tools
- trying to clone production data back to staging, or reset dbs between runs
- launching temp infra of sibling services for end-to-end tests, running canaries
- selenium and other UX tests, transpiling and bundling assets

> Selenium tests can be speedy, but the main problem I see is people using too many of the things. Ideally, they’re there to check something that nothing else can. *sigh*@aslak_hellesoy did a fun talk about architectures to improve test times @seleniumconf https://t.co/kSzwfNAmlC— Simon Mavi Stewart (@shs96c) December 23, 2020
> 

### “Have a seat and think about your life choices.”

- excessive number of dependencies
- extreme legacy dependencies (things from the 90s)
- tests with “sleep” in them
- entirely too large frontends that should be broken up into modules

### “We regret to remind you that most AWS calls operate at the pace of ‘Infrastructure’, not ‘Software'”

- AWS CodeBuild has several minutes of provisioning time before you’re even executing your own code — even a few distinct jobs in a pipeline and you might suffer 15 min of waiting for CodeBuild to do actual work
- building a new AMI
- using EBS
- spinning up EC2 nodes .. sequentially
- cool it with the AWS calls basically

> - QA insists on writing all the tests themselves so it takes 2+hrs to run, can only run one at a time, and doesn’t cover most of the actual bug surface area(yes, these are burning red flags for SEVERAL parts of the dev process, but there we were)— It is no longer November, Dave (@6502_ftw) December 24, 2020
> 

A few responses were oozing with some unresolved trauma, lol.

### Natural Born Opponents: “Just cache it” and “From the top!”

- builds install correct version of toolchain from scratch each time
- rebuilding entire project from source every build
- failure to cache dependencies across runs (eg npm cache not set properly)

### “Parallelization: the cause of, and solution to, all CI problems”

- shared test state, which prevents parallel testing due to flakiness and non-deterministic test results
- not parallelizing tests

> Cross stack tests which move data among different moving pieces, hard to mantain and used to be one of the sources of having a slow and unreliable pipeline which adds friction to your deploy strategy.— pfreixes (@pfreixes) December 25, 2020
> 

I have so many questions….

Thanks to @wrd83, @sorenvind, @olitomli, @barney_parker, @dastbe, @myajpitz, @gfodor, @mrz, @rwilcox, @tomaslin, @pwyliu, @runewake2, @pdehlkefor, and many more for their contributions!

P.S. what did I say about instrumenting your build pipeline? For more on honeycomb + instrumentation, see this thread. Our free tier is incredibly generous, btw

> ok i don't think i've ever actually properly pointed people at this fabulous talk, so here is a sample of some favorite ben moments."We read through our build log and we couldn't really tell what we were supposed to care about, so we put it in honeycomb. " https://t.co/P4Z3yPCVBd— Charity Majors (@mipsytipsy) June 10, 2020
> 

Stay tuned for more long form blog posts on this topic. Coming soon.

charity

P.S. [this blog post is the best thing i’ve ever read about reducing your build time. EVER.](http://dan.bodar.com/2012/02/28/crazy-fast-build-times-or-when-10-seconds-starts-to-make-you-nervous/)

![Questionable%20Advice%20The%20Trap%20of%20The%20Premature%20Seni%2092e3c65f07534ddab4e606c54d3947f1/IMG_1540.png](Questionable%20Advice%20The%20Trap%20of%20The%20Premature%20Seni%2092e3c65f07534ddab4e606c54d3947f1/IMG_1540.png)