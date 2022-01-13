# stephenplusplus/stream-faqs: Let's learn these things together

Source: Article
Status: Unprocessed
URL: https://github.com/stephenplusplus/stream-faqs

[https://opengraph.githubassets.com/cc7614f71fb1926f159f6bfaa08dff5d393512407dcdbf9f3bebb0fad3eac111/stephenplusplus/stream-faqs](https://opengraph.githubassets.com/cc7614f71fb1926f159f6bfaa08dff5d393512407dcdbf9f3bebb0fad3eac111/stephenplusplus/stream-faqs)

---

[stream-faqs](stephenplusplus%20stream-faqs%20Let's%20learn%20these%20thin%20c5d0893088dd44c78bd4c854229b9dd2/stream-faqs)

# stream-faqs

> Let's learn these things together.
> 

The stream learning curve has been (embarrassingly) difficult for me. But I find that the more I talk about how confused I am, the more I find people are confused, too. I've received some great help along the way, and I want to share what I've found while I continue to learn more.

When you get stuck, keep in mind:

- The answer is almost always in the modules. The hard part is finding them and knowing what to use when
- Your use case can probably be "re-thought of" and applied to an existing solution for a similar problem
- You can come here to ask for help, and I'll try my best to answer or get one

## Questions

- [How can I make a paginated API request?](https://github.com/stephenplusplus/stream-faqs)
- [How can I destroy all of the streams in a pipeline if one gets an error?](https://github.com/stephenplusplus/stream-faqs)
- [How can I just get all of the results when they're done coming in?](https://github.com/stephenplusplus/stream-faqs)
- [How can I asynchronously assign a stream after one has already been created?](https://github.com/stephenplusplus/stream-faqs)
- [How do I know when a stream is first written to or read from?](https://github.com/stephenplusplus/stream-faqs)
- [What's the difference between "abort", "close", "end", "destroy", "finish", and "complete"?](https://github.com/stephenplusplus/stream-faqs)
- [Have a question?](https://github.com/stephenplusplus/stream-faqs/issues/new)

*If you find any of this information to be inaccurate or incomplete, feel free to contribute a PR!*

- -

### How can I make a paginated API request?

**Problem**

You need to pull down many results from a backend, but it limits the amount of responses you receive at a given time. You get some type of token to include with a follow up request to cursor through the results. How do you combine all of those results into one stream?

**Solutions**

- **[See an example](https://github.com/stephenplusplus/stream-faqs/tree/master/ex-paginate)**
- [https://github.com/feross/multistream](https://github.com/feross/multistream)
- [https://github.com/timhudson/continue-stream](https://github.com/timhudson/continue-stream)
- [https://github.com/timhudson/pagination-stream](https://github.com/timhudson/pagination-stream)
- [https://github.com/karissa/paged-http-stream](https://github.com/karissa/paged-http-stream)
- -

### How can I destroy all of the streams in a pipeline if one gets an error?

**Problem**

You have a bunch of streams piped together and one gets an error. The other streams and any listeners on them don't really know what happened and linger around without being properly destroyed.

**Solutions**

- **[See an example](https://github.com/stephenplusplus/stream-faqs/tree/master/ex-destroy)**
- [https://github.com/mafintosh/pump](https://github.com/mafintosh/pump)
- [https://github.com/mafintosh/pumpify](https://github.com/mafintosh/pumpify)
- -

### How can I just get all of the results when they're done coming in?

**Problem**

You have a source readable stream but don't really want to do anything stream-y with it. Registering `.on('data')` events is a lot of boilerplate to combine the results as they come in.

**Solution**

- **[See an example](https://github.com/stephenplusplus/stream-faqs/tree/master/ex-concat)**
- [https://github.com/maxogden/concat-stream](https://github.com/maxogden/concat-stream)
- -

### How can I asynchronously assign a stream after one has already been created?

**Problem**

You want to make an API request but have to fetch an access token first. If you just call `request(/*...*/)`, you will inevitably get a 401 error, so how do you get a stream, but only have it "start" *after* you fetch an access token?

**Solution**

- **[See an example](https://github.com/stephenplusplus/stream-faqs/tree/master/ex-async-stream)**
- [https://github.com/mafintosh/duplexify](https://github.com/mafintosh/duplexify)
- -

### How do I know when a stream is first written to or read from?

**Problem**

Since it's possible for you (or a user of your library) to create a stream, but then never connect it to anything, or not run it for an unknown amount of time, you might want to wait as long as possible to do something async.

**Solution**

- **[See an example](https://github.com/stephenplusplus/stream-faqs/tree/master/ex-wait)**
- [https://github.com/stephenplusplus/stream-events](https://github.com/stephenplusplus/stream-events)
    - Note: works well with the [duplexify problem](https://github.com/stephenplusplus/stream-faqs).
- -

### What's the difference between "abort", "close", "end", "destroy", "finish", and "complete"?

**Problem**

There's a holy-moly-lot of events that go on with streams. How do you know which to listen to for a given stream?

**Sub-problem**

Sometimes, you won't even know what kind of stream you have. Libraries may give you combined/duplex streams, a Transform stream, or a plain old readable stream. You really have to stay close to their documentation and source code to see what you're dealing with.

**Solution**

[Untitled](stephenplusplus%20stream-faqs%20Let's%20learn%20these%20thin%20c5d0893088dd44c78bd4c854229b9dd2/Untitled%20Database%207b7239ef0a8d4fd59f405ca3e41594a0.csv)

[Untitled](stephenplusplus%20stream-faqs%20Let's%20learn%20these%20thin%20c5d0893088dd44c78bd4c854229b9dd2/Untitled%20Database%20e5bea01e073c47e18d2dde866e6fa1fc.csv)

## More Helpful Resources

- [Mississippi](https://github.com/maxogden/mississippi) - See more examples and descriptions of the most popular stream modules (many of the ones mentioned here).