# System Design Interview Checklist | Questions | Resources | System Architecture | Towards Data Science

Source: Article
Status: Unprocessed
URL: https://towardsdatascience.com/my-system-design-interview-checklist-86b64b5ac5e2

[https://miro.medium.com/max/1080/0*hIa-GHMPo0nxgRPB](https://miro.medium.com/max/1080/0*hIa-GHMPo0nxgRPB)

---

[System%20Design%20Interview%20Checklist%20Questions%20Resour%20936716f280464c5697ed6a3e0477b7c4/0hIa-GHMPo0nxgRPB](System%20Design%20Interview%20Checklist%20Questions%20Resour%20936716f280464c5697ed6a3e0477b7c4/0hIa-GHMPo0nxgRPB)

Image via [Unsplash](https://unsplash.com/photos/RLw-UC03Gwc)

*That dreaded system design interview. I remember the first system design question I was asked. “Design WhatsApp”, he said. I didn’t know where to start! I was a fresher. Data structures and Algorithms were the only things I knew. I am sure you can guess how that interview went. Then after enough research, I made myself a checklist of components, of sorts, to navigate me through my next system design interviews!*

So I’ll stop with the chit-chat and get right into it!

# User Interface

First things first, how are the users interacting with your system? Is it via a mobile app or on a laptop or a smart TV? This gives us an indication of what kinds of limitations and hidden requirements we are dealing with. For example, in the case of a mobile user, we might have to handle fluctuating networks, for a smart TV and laptop user kind of scenario we might have to support different file formats and different resolutions and aspect ratios.

# Load Balancer

You cannot design a distributed system without a load balancer. Load balancing means distributing the requests between various nodes of a distributed system, so as to decrease response time and improve resource utilization. By distributing the load between various nodes, we rule out the chance of having a single point of failure and also ensure that a single node is not being overloaded while another server might be sitting idle.

# Web Sockets

Or to be more specific *web socket handler* and *web socket manager*. I know, these are not standard terms. But it is something I came across recently on a youtube video and it makes total sense. A **Web Socket Handler** is basically a server that keeps an open web socket connection with all active user devices. Any request from the user will enter the system via a web socket handler and any notifications or responses to the user will be sent via the web socket handler as well. Now if we are working on a large-scale application, with users distributed across various locations, we are going to need web socket handlers distributed across various geographical locations. Think *low latency*. Now users could also switch between various web socket handlers due to let’s say network fluctuations, or simply because they are now physically closer to another web socket handler. In this case, we need a central repository to keep track of which user is connected to which web socket handler. This is done by a **Web Socket Manager**.

# Database

Well, not just database, storage solutions in general. If we need to save images or files, we will need blob storage like Amazon S3, if we are storing payment records, we need it to follow ACID properties and need a relational database in such a case. If we are storing product-related information on a platform like Amazon we will probably need a document DB like Mongo DB. If we were building Twitter or Facebook, we cannot design our system without a Caching solution like Redis. There are so many things we need to consider while deciding which storage solution to use! Here is one of the best articles I came across during my prep -> [Choosing the best Database Solution in a System Design Interview](https://www.codekarle.com/system-design/Database-system-design.html) by CodeKarle.

# CDN

Again, if our users are distributed geographically, it makes sense to maintain copies of frequently accessed data in a data center closer to the users’ location. For example, a lot of traffic for “Scared Games” on Netflix probably comes from India. So it makes sense to keep the data in a data center close to India to reduce the latency and improve the user experience. Here is a short video by Akamai, explaining briefly exactly what a CDN does -> [What is a CDN](https://youtu.be/l6X_IxyGHHU)

# Analytics Components

Remember, no matter what kind of a system you are creating, there is always scope for analytics. It is one of those things that are never called out during requirement gathering but are always required. This is when we use a stream processing software like Kafka. Whatever goes on in the system, a user logs in or logs out, gets dropped off from a call, cancels an order, cancels a payment, anything! It is all useful information for us! Whenever an event occurs, it should be written to Kafka. On Kafka, we could have some simple spark streaming jobs running for real-time processing. Or we could simply dump the data in a Hadoop cluster and later run some fancy machine learning algorithms for detailed analytics.

# Pluggable components

If we were designing Twitter, post length is one of the limitations we need to handle. But what if a user wants to share a link? That would take up half the post! Which is why we need a *URL shortening service*. No matter what system you build, there will always be something or the other that needs to be notified to the user. This is where you might need a *notification service*. Notification services are actually a great way to understand the requirement for pluggability. What if as per our requirement, we need to send in-app notifications if a friend likes a profile picture on Facebook. So we build that into our system. Now a new requirement comes in to send out an email notification to users who haven’t accessed the app in more than 3 days. We can’t add another service to handle email notifications. This is why our notification service needs to be pluggable, so we can add handlers as we go and support new notification methods easily.

Another example of an independent service being used as a separate component would be an *asset delivery service*. If you were building something like Netflix, we need a system to load video content to CDNs depending on the incoming traffic, manage what resolutions and aspect ratio data needs to be sent to which user, takes care of transcoding the main file to all other supported file formats, etc. I will attach a link to one of the videos I referred to, to understand how an asset delivery system might work.

# Monitoring and Alerting

Are you reaching milestones? Meeting deadlines? Is your system working as expected? Be it any application, no matter how well it is planned or designed, there is always a chance for something to go wrong. A third-party dependency could crash, a server could go down, maybe a server’s CPU utilization is very high while another is underutilized, maybe the system could not scale enough during the Black Friday Sale! Wouldn’t it be great to know these things beforehand?

But how? By monitoring your system of course! And alerting. Anything that is behaving unexpectedly or is reaching its limit, must be called out BEFORE it gets out of hand. This is another one of those things that are not called out initially but are very important while building a system. [Here](https://youtu.be/YyOXt2MEkv4?t=2056) is an example of how you can do that.

# Brownie Points

Once you have come up with a solution that meets all the requirements called out in the requirement gathering stage, it is your time to actually shine and stand out from other applicants. This is when you consider **edge cases** that people usually don’t consider in interviews. Like how does Google handle disputed areas like India-Pakistan-China borders in Google Maps? Or you could demonstrate how you can **extend your solution** to support a much larger scale than intended. Like can your video conferencing system be extended to live broadcast an event?

# Resources you might want to look at

*What is a load balancer? -> [https://medium.com/@itIsMadhavan/what-is-load-balancer-and-how-it-works-f7796a230034](https://medium.com/@itIsMadhavan/what-is-load-balancer-and-how-it-works-f7796a230034)*

*How to choose the best storage solution in your system design interview? -> [https://www.codekarle.com/system-design/Database-system-design.html](https://www.codekarle.com/system-design/Database-system-design.html)*

*What exactly is a CDN? -> [https://youtu.be/l6X_IxyGHHU](https://youtu.be/l6X_IxyGHHU)*

*How to scale your system with Redis -> [https://youtu.be/CtV-QymAeIc](https://youtu.be/CtV-QymAeIc)*

*How an asset delivery system works (with Netflix example) -> [https://youtu.be/lYoSd2WCJTo](https://youtu.be/lYoSd2WCJTo)*

*Here’s another medium article I wrote about choosing the best DB for a system design interview -> [https://towardsdatascience.com/choosing-the-right-database-in-a-system-design-interview-b8af9c6dc525?source=friends_link&sk=d78ef7e0b0f4071636c57681b9fce1c8](https://towardsdatascience.com/choosing-the-right-database-in-a-system-design-interview-b8af9c6dc525?source=friends_link&sk=d78ef7e0b0f4071636c57681b9fce1c8)*

*A comprehensive guide for cracking the next system design interview by CodeKarle -> [https://www.codekarle.com/](https://www.codekarle.com/)*

*Commonly asked system design interview questions -> [https://www.youtube.com/watch?v=EpASu_1dUdE&list=PLhgw50vUymyckXl3D1IlXoVl94wknJfUC](https://www.youtube.com/watch?v=EpASu_1dUdE&list=PLhgw50vUymyckXl3D1IlXoVl94wknJfUC)*

I hope this can help you come up with a checklist of your own to refer to during your next system design interview. Think I missed an important step? Let me know in the comments!