# My 3 Biggest Failures as a Software Developer | by Adam Hughes | Level Up Coding

Source: Article
Status: Unprocessed
URL: https://levelup.gitconnected.com/my-3-biggest-failures-as-software-developer-6c16a171eaaf

[https://miro.medium.com/max/450/0*a4B539PK-EIKkxmV](https://miro.medium.com/max/450/0*a4B539PK-EIKkxmV)

---

[0*a4B539PK-EIKkxmV](My%203%20Biggest%20Failures%20as%20a%20Software%20Developer%20by%20A%202adaf98feabf47819e427debaa0a4465/0a4B539PK-EIKkxmV)

As programmers, we all know the story of the rockstar developer. She started coding young and had her first profitable website by age 11. College at 16; LLC at 17; billionaire at 23. We love these stories, these heroes; they inspire us with their prolific programming and their trendsetting. And between solving NP-complex problems and raising millions in Series A funding, they seemingly never misstep.

**Here’s the reality: every developer, even rockstars, screw things up** and overcome setbacks. The only difference is in scale; when we screw up, database records get corrupted. When they screw up, [billion dollar mistake](https://www.infoq.com/presentations/Null-References-The-Billion-Dollar-Mistake-Tony-Hoare/)s are made. Why are we collectively so afraid of mistakes? Mistakes are good; nothing is a better teacher than failure. Yet, it carries a stigma. No one talks about. No one wants to be seen as the dummy in the room of geniuses.

Such repression has consequences. When developers make mistakes, it’s perceived as a personal failing. They’re ashamed, and often blamed. “Mike forgot to update the release doc” or “Bill cherry-picked the wrong branch”. This is immensely counterproductive. Failures are almost always systematic in nature. As such, they are a great opportunity to identify and correct business deficiencies. There’s no better teacher than failure and we shouldn’t be afraid to talk about it. In this spirit, below I candidly dredge up my three worst blunders as a budding software developer. **I then go on to explain and how I grew from, and am thankful for, each and every one of them.**

# Deleted a Thousand URLs

While working at a major financial institution, I developed a system to purge unused routes in the F5 networking layer. The F5 route pool could only support about 5000 URLs or so before it got choked up. My system automated the process of monitoring traffic to these URLs, notify owners of unused resources, and ultimately purged them, keeping the F5 system from falling over, and freeing up operations from non-stop manual intervention.

The system was coming along nicely and had successfully been used to delete a few dozen routes in lower environments. However, one Sunday I awoke to an email chain that 1000 routes were removed the night prior and users were complaining that these were active/live URLs!

Ruining everyone’s weekend, our team sprung into action. It turned out that an old .YAML config file had been deployed with the app container, which removed routes that had non-activity for 1 week instead of 1 month. Thankfully, I had put a failsafe to prevent deleting of production resources, but these were still serious. Highly used, company-wide, application outages were likely if my program had in fact removed resources that were active.

It turned out that most resources that are inactive for 1 week remain so for 1 month; in other words, important apps aren’t inactive for a week. So ultimately the damage was manageable; out of 1000 URLs removed, only a handful of teams complained. However the flak and stress this caused for me and my managers was immense, especially early on when the scale of the damage was still unknown. As a result, we set up basically a war room, diverting the entire team’s resources into being ready to manually re-create these lost resources.

**How could this happen!?**

Initially I felt like this was all my fault (it didn’t help that my managers agreed). But in hindsight, it was also a systematic failure. First, the fact that existing F5 route management system couldn’t handle the needs of the business, nor did it have a clear backup/rollback strategy, were big problems. Furthermore, the old config file hanging around was because of a needlessly complex deployment process. It was overly bureaucratic and prone to such errors. Finally, this critical task was given to me alone (ie. no code-reviews/team engagement) and with a very optimistic deadline, was a recipe for disaster. We never treated this as a first-order priority, and looking back with more experience, the result seems inevitable.

**How I Grew**

I have never been so grateful to my colleagues who stepped up and dug us out of the mess I’d created. And at the same time, I’d never felt more professionally crushed when my manager and the most senior developer told me that they had lost faith in me as an engineer and would not allow me to continue to work on our important project. In other words, they couldn’t believe I had done something so stupid and didn’t trust me to continue working on this or other key projects (they eventually recanted).

If you’re not brought to tears routinely, are you *really* a software engineer? ([Image source](https://www.123rf.com/photo_68490295_deadline-technology-and-people-concept-sad-stressed-software-developer-with-computer-at-home-office.html))

As embarrassing as it is to admit, I actually cried over this. It was afterwards with a teammate who took me out for beers. When I relayed the conversation to him, he said it was extremely unfair and uncool and told me how much he and the rest of the team appreciated me. After being so crushed the entire week, I was a ball of nerves and hearing someone say that just was too much. My primary manager also took me out for lunch and helped me through the situation. Both of these gestures stayed with me for years.

What this taught me is that while code is extremely well controlled, infrastructure and data often isn’t. It is absolutely critical to use DB Migration tools like [DBMate](https://github.com/amacneil/dbmate) and [Terraform](https://www.terraform.io/) to manage these components of the system and treat them equal to, if not more important than, application code.

It is also paramount to limit access to the production environment. For example I don’t even keep a local master branch on my IDE, and prefer to lock down all direct pushes to non-feature branches teamwide. DB and cloud accounts should be read only by default, and should have clear backup and recovery strategies. In my next job for example, a developer accidentally deleted files from a prod S3 bucket. If not for the [S3 versioning strategy](https://docs.aws.amazon.com/AmazonS3/latest/userguide/Versioning.html) I’d setup only a week prior (it’s off by default — wtf Amazon!), we may have lost it permanently.

**Finally, the last and most important lesson I learned was one of empathy**. It sucks enough to make the mistake, so having management pile it on is both devastating and unnecessary. Something similar recently happened to a teammate of mine: he put errant code into production and we had to manually correct some data. He spoke guiltily about it. I took that opportunity to clearly explain that the reason it happened is because our deployment data migration processes were subpar. It was a failure of our team, not of him, and it was bound to happen. I also reminded him of the great features he’s been cranking out and how important they are to us and the business. His mistake was simply a reminder to revisit our tooling/processes, and it motivated him to contribute to the solution. **Mistakes are opportunities.**

# Emailed code outside company

Before leaving a job, I emailed myself code. I’d spent close to a year working on Spring libraries, and in the process, created some really nice testing patterns. I didn’t want to forget all of these great ideas and had planned to create a series of medium posts about them.

About a month later, on the first day of my new job, I got the most face color-draining text of my life. “Dude, our team is in hot water. Someone emailed code outside the company and legal is involved. Do you know who it was?”

I immediately called my former manager. No answer. Called my colleagues. No answer. Legal had intervened and instructed them to break contact with me. It was beyond scary. Sensing something wrong, my new manager asked me about it. Being a former lawyer, he told me to lawyer up just in case. I urgently called my wife’s family lawyer and we talked through various scenarios. Because it was utility code, it was less likely that they would “come after me”, but was still possible.

My wife picked me up that day and was in a great mood. She asked how my first day went, to which I answered “I think I screwed us”. Her expression melted. As I revealed what happened, she took it like a champ. Told me that, while really stupid, we’d get through it. I lived in a fog the next week until my former companies’ legal team reached out and told me that they would not be pressing charges if I signed an agreement to delete that code immediately.

**How could this happen!?**

I had tunnel vision — plain and simple. While it seems like some nefarious plot, the simple truth is that I was really proud of the patterns and utilities I’d built that I thought I’d lose something as a developer if I lost it. I had some grand idea that it would lead to a few interesting blog articles, and somehow in my one-track mind, the benefits outweighed the risk.

To this day, I still feel awful about how this affected my former teammates. This mistake was 100% mine, but they surely had to deal with the fallout. The team reputation was likely tarnished, and dealing with audit must have been a big hassle for everyone. It damaged my professional reputation and sadly burned a lot of bridges.

**How I Grew**

Foremost, I became extremely cautious about company emails and internal communications. Not a week into my new job, several employees were let go for inappropriate conversation in Slack DMs. It was a pretty messy affair — they were all let go and eventually the rest of us had to do mandatory HR training on harassment in the workplace. Despite how inept your company’s technology staff, **you should always assume they have complete visibility into your private communications**.

Another great lesson here was how my wife and parents rallied around me. I was dismayed about the situation and couldn’t think straight, and their calmness and understanding brought me back to reality. I was on the verge of an existential crisis — how could I have a PhD and work in this field, but at the same time be so careless and stupid? Did I just ruin my future? **Without a great support system, I may have went off the rails and just made the whole situation worse.** Their advice and guidance to bring in a lawyer stopped me from making the situation worse.

**YAGNI (you ain’t gonna need it), is not just a principle of software.** Would I really have even looked at that code again? Even if it did lead to a few blog articles, did that justify the risk? Hell no. When you leave a job, or any chapter in life for that matter, just leave. Don’t take anything with you; don’t look in the rear view; just move on.

# **Lost My Job During Covid**

In 2019, I was working at a relatively successful startup to modernize the process of pavement upkeep. Our main source of revenue was local governments and we also had venture backing. Both sources abruptly vanished in March 2020. Our company rode the Covid wave successfully for a few months, pivoting sharply to address shifting client priorities, and garnering some funding through small business relief funds.

However by July it was clear that we needed to shrink or sink. At 11:30, the CEO personally DM’d me on Slack with an ominous request to have a 12pm phone call. By 12:15, I was fired. To paraphrase: “Adam, we are letting you go effective immediately. We feel you have performed well; however, due to the current climate, we are cutting staff”. I was one of 15 or so folks unceremoniously let go that day — no warning, no severance, not even a 5 minute window to say goodbye to my team (Slack account disabled while on the call).

My wife and I had just moved into our first house six months prior and were not in a financial position to last long without steady income.

The next few months were brutal; I couldn’t land a job anywhere. The market was saturated with quality engineers in the same boat. Hell, I couldn’t get unemployment compensation, which became so frustrating that I wrote an entire [blog post about it](https://levelup.gitconnected.com/you-have-to-become-a-hacker-to-get-unemployment-compensation-de7b384d640e).

**How could this happen!?**

Covid was a 1–2 punch, leading directly to downsizing and a tough job market. But there’s a hard lesson here — **I was fired because I wasn’t essential**. The business could get on well enough without me. The engineers they kept were very technically strong, but more importantly, they were working on core business systems. Letting them go might tank the business completely. And therein lies my major misstep.

Being a relatively new hire, they put me on cool greenfield projects. I worked on ML pipelines and data analysis in Jupyter. However, our core systems were run-of-the-mill Flask apps. Nobody really pushed me into these systems, so I kept my distance. When they had bugs, I didn’t solve them. When they were slow, I didn’t support them; nobody asked me to and so I didn’t. I was doing the cool new stuff — the future of the company! It turned out that these systems, and the engineers that built and supported them were more valuable to the company than I was. Looking back, it’s clear now. **Reflecting on the tough choice the CEO had to make, he made the right choice to let me go**!

**How I Grew**

July — September was rough; I was passed over for job after job. It was especially crushing to come really close to getting my dream job at an AV company, only to be rejected at the last step (for the 2nd year running). Eventually, I took a *boring* Java job at a *boring* company. **What I quickly learned is that boring software is just dandy**. Boring software has straightforward requirements and dedicated users. Things like “this button doesn’t work” are easily fixed, and don’t require a PhD nor years of planning. It’s actually deeply satisfying to knock out low-hanging fruit for a standard web app and have actual people tell you how grateful they are!

**Doing the boring stuff also makes you critical**. I’ve volunteered for tons core work, from setting up infrastructure to working on hard features. And while my goal is not to become a piece of the system itself (ie. I still want to automate myself away), this should make it harder to let me go.

Also — **I no longer have anxiety about job interviews or losing my job**. We can only do our best, and the rest is out of our control. Maybe you didn’t get that job because another candidate had more experience in a certain technology. Maybe they had already made an offer. Or maybe you just aren’t as good as the next guy. Lose your ego and get comfortable with all of these reasons, and the fear will fade. Realize you’re probably not, nor never will be, a Rockstar developer, and that’s ok.

Finally, **the last thing I learned is to ask for constant feedback**. How am I doing? Why am I working on X — is X critical to the company’s success? If not, what is? Don’t get so attached to your work. Often we’re afraid of feedback because it bruises our ego, but embracing feedback is fast way forward. And PS, if you’re one of the many companies who refuse to give feedback to applicants, shame on you.

The takeaway to all of this is that failing and obstacles are not only inevitable, they are necessary. *Individual failures are rarely the fault of just individuals*. Failure is an opportunity — an opportunity to learn about yourself and those around you. Did your boss tear you down or pull you up? Did your friends and family have your back? What a great time to pause, reflect and correct course.

# Level Up Coding

Thanks for being a part of our community! **[Subscribe to our YouTube channel](https://www.youtube.com/channel/UC3v9kBR_ab4UHXXdknz8Fbg?sub_confirmation=1)** or join the **[Skilled.dev coding interview course](https://skilled.dev/)**.