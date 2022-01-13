# A Visual Guide to NodeJS Streams. In NodeJS, stream module provides the… | by Deepal Jayasekara | Deepal’s Blog

Source: Article
Status: Unprocessed
URL: https://blog.insiderattack.net/a-visual-guide-to-nodejs-streams-9d2d594a9bf5

![https://miro.medium.com/max/1200/1*Ea9ZoWv5Qpa2OHDkqR7neA.jpeg](https://miro.medium.com/max/1200/1*Ea9ZoWv5Qpa2OHDkqR7neA.jpeg)

---

![A%20Visual%20Guide%20to%20NodeJS%20Streams%20In%20NodeJS,%20stream%20a884a889ecf64e53b72e70ec43e111e0/1Ea9ZoWv5Qpa2OHDkqR7neA.jpeg](A%20Visual%20Guide%20to%20NodeJS%20Streams%20In%20NodeJS,%20stream%20a884a889ecf64e53b72e70ec43e111e0/1Ea9ZoWv5Qpa2OHDkqR7neA.jpeg)

Background Image Courtesy: Photo by [Joshua Sortino](https://unsplash.com/@sortino?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) on [Unsplash](https://unsplash.com/s/photos/digital?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)

Imagine you have a pile of bricks somewhere. And you want to build a wall with those bricks here. Let’s say you have a friend to help move the bricks. To start building, you now have two options. You can either wait until your friend brings the whole pile of bricks to you, or you can start building as soon as you have a few bricks to start with, while your friend keeps bringing more bricks.

Which would be efficient? **Clearly, it will be efficient to start building as soon as you have a few bricks to start with.** This is a classic example of how a ‘stream’ (in this case a stream of bricks) can improve the efficiency of a process. Another common example you might be very familiar with would be streaming a movie instead downloading the whole movie first and and watch it.

> In computer science, a stream is a sequence of data elements made available over time. A stream can be thought of as items on a conveyor belt being processed one at a time rather than in large batches.
> 

In NodeJS, `[stream](https://nodejs.org/api/stream.html)` module provides the capability to work with streams. Even if you haven’t used `stream` module explicitly there are a lots of underlying functionality in NodeJS applications which use streams. “Streams” is an easy concept, but it may sound very complex if you are unfamiliar with it. Therefore, I thought of describing a few key concepts in NodeJS streams in visuals so that it can be easily understood.

## Water flows, Information flows.

Information is like a liquid. It flows from one place to another place as a stream of bits. For example, this happens when two peers talking to each other via a network, or even when your application is communicating with the disk or a peripheral device. When such an I/O operation happens, the information is read from a device and is flowed towards an application, or vice versa.

However, it’s possible that one end of the above transaction is slower than the other for various reasons. Therefore, some of the data might need to be “buffered” in-between, while the receiver-end is ready to accept more data.

Have a look at the following picture where two faucets of different sizes are connected via a tank. The rate water flows from upstream is higher than the rate downstream can consume. Therefore, the tank has to temporarily store (“buffer”) the excess water while the downstream slowly consumes.

This is the fundamental idea of streams in NodeJS. `stream` module provides functionality to implement this behaviour when working with streaming data. There are two basic types of streams provided by NodeJS.

They are,

- Readable Streams
- Writable Streams

However, there are two additional types of streams which are hybrids of Readable and Writable streams, and serve special purposes.

- Duplex Streams
- Transform Streams

Let’s get into more details, and try to visualise each of these.

## Readable Stream

A readable stream can be used to read data from an underlying source such as a file descriptor. Data can be stored in a `[Buffer](https://nodejs.org/api/stream.html#stream_buffering)` within the readable stream if the application consumes slower than the operating system reads from the source.

![A%20Visual%20Guide%20to%20NodeJS%20Streams%20In%20NodeJS,%20stream%20a884a889ecf64e53b72e70ec43e111e0/1QcVF_5C7WtJx_ohqJJ8dYw.png](A%20Visual%20Guide%20to%20NodeJS%20Streams%20In%20NodeJS,%20stream%20a884a889ecf64e53b72e70ec43e111e0/1QcVF_5C7WtJx_ohqJJ8dYw.png)

A few of the most common readable streams in NodeJS are `[process.stdin](https://nodejs.org/api/process.html#process_process_stdin)`, `[fs.createReadStream](https://nodejs.org/api/fs.html#fs_fs_createreadstream_path_options)` and `[IncomingMessage](https://nodejs.org/api/http.html#http_class_http_incomingmessage)` object in an HTTP server.

## Writable Stream

A Writable stream is used to write data from an application to a certain destination. To prevent data loss or overwhelming of the destination in case the destination is slower than the writing application, the data may be stored in an internal `[Buffer](https://nodejs.org/api/stream.html#stream_buffering)`.

![A%20Visual%20Guide%20to%20NodeJS%20Streams%20In%20NodeJS,%20stream%20a884a889ecf64e53b72e70ec43e111e0/1zGPIBCmXFqzSowUmlpfs-Q.png](A%20Visual%20Guide%20to%20NodeJS%20Streams%20In%20NodeJS,%20stream%20a884a889ecf64e53b72e70ec43e111e0/1zGPIBCmXFqzSowUmlpfs-Q.png)

The most common writable stream which you might use every day would be `[process.stdout](https://nodejs.org/api/process.html#process_process_stdout)` which is used underneath `console.log`. In addition to that, two other very common writable streams in NodeJS are `[process.stderr](https://nodejs.org/api/process.html#process_process_stderr)` and `fs.createWriteStream`

## Duplex Stream

As I mentioned earlier, a duplex stream is a hybrid of a Readable stream and a Writable stream. An application connected to a duplex stream can both read from and write to the duplex stream. The most common example of a duplex stream is `[net.Socket](https://nodejs.org/api/net.html#net_class_net_socket)`. In a duplex stream, read and write parts are independent and have their own buffers.

![A%20Visual%20Guide%20to%20NodeJS%20Streams%20In%20NodeJS,%20stream%20a884a889ecf64e53b72e70ec43e111e0/1V51BbjIa70RblrM7aEKxgg.png](A%20Visual%20Guide%20to%20NodeJS%20Streams%20In%20NodeJS,%20stream%20a884a889ecf64e53b72e70ec43e111e0/1V51BbjIa70RblrM7aEKxgg.png)

## Transform Stream

A transform stream is an even special hybrid, where the Readable part is connected to the Writable part in some way. A common example would be a crypto stream created using `[Cipher](https://nodejs.org/api/stream.html#stream_buffering)` class. In this case, the application writes the plain data into the stream and reads encrypted data from the same stream.

![A%20Visual%20Guide%20to%20NodeJS%20Streams%20In%20NodeJS,%20stream%20a884a889ecf64e53b72e70ec43e111e0/1XBLmT-C8NhRJ9Z1eCIvtng.png](A%20Visual%20Guide%20to%20NodeJS%20Streams%20In%20NodeJS,%20stream%20a884a889ecf64e53b72e70ec43e111e0/1XBLmT-C8NhRJ9Z1eCIvtng.png)

Probably the most trivial transform stream is `[PassThrough](https://nodejs.org/api/stream.html#stream_class_stream_passthrough)`, where the input data is simply passed as the output with no transformation whatsoever. While it may sound very trivial, I’ve used it many times to implement custom behaviours with streams.

## Piping Streams

In many cases, streams are even more useful when connected together. As obvious as it may sound, this is called ‘piping’. You can connect a Readable stream to another Writable/Duplex or a Transform stream by using the Readable stream’s `pipe()` method.

![A%20Visual%20Guide%20to%20NodeJS%20Streams%20In%20NodeJS,%20stream%20a884a889ecf64e53b72e70ec43e111e0/1rKroHjnDgnO45qm79CgDRg.png](A%20Visual%20Guide%20to%20NodeJS%20Streams%20In%20NodeJS,%20stream%20a884a889ecf64e53b72e70ec43e111e0/1rKroHjnDgnO45qm79CgDRg.png)

A trivial example for this would be copying a file from one place to another place by piping an `fs.createReadStream()` to an `fs.createWriteStream()`.

## Copying Data with Streams

One interesting fact about piping is that you can pipe the same stream more than once. This can be very useful in situations where you need to read the same stream twice, as you cannot read from a Readable stream once again after it’s completely read by another consumer. However, by piping a Readable stream more than once, more than one consumers can read the same stream by copying the data from the original Readable stream.

Have a look at the following simple example, where we create two copies of the `original.txt` file.

The above program can be visualised as follows:

![A%20Visual%20Guide%20to%20NodeJS%20Streams%20In%20NodeJS,%20stream%20a884a889ecf64e53b72e70ec43e111e0/1nfu8H19tk5Lb3BXB4cVslg.png](A%20Visual%20Guide%20to%20NodeJS%20Streams%20In%20NodeJS,%20stream%20a884a889ecf64e53b72e70ec43e111e0/1nfu8H19tk5Lb3BXB4cVslg.png)

## Backpressure

Let’s go back and recap our water tank analogy. In that analogy, the upstream flows at a higher rate than the downstream can consume. In this case, the water level of the tank will keep rising until at some point it overflows and the water goes to waste.

What if we can ‘detect’ it’s going to happen and let the upstream know to stop the flow? We can mark the tank below the highest level, and ask the upstream to stop when the water level rises above the mark.

![A%20Visual%20Guide%20to%20NodeJS%20Streams%20In%20NodeJS,%20stream%20a884a889ecf64e53b72e70ec43e111e0/1K_lj7KgSy4UUpHzinvnFsA.png](A%20Visual%20Guide%20to%20NodeJS%20Streams%20In%20NodeJS,%20stream%20a884a889ecf64e53b72e70ec43e111e0/1K_lj7KgSy4UUpHzinvnFsA.png)

This is very similar to how streams work. While Readable and Writable streams can buffer data internally, the amount of data they can buffer is limited by the total available memory of the system. Therefore, streams have a threshold called `highWaterMark` which can be used to detect if the rate at which data is passed into the stream is way higher than the rate at which data is flushed out of the stream.

As an example, when a readable stream is piped to a writable stream, the writable stream can ask the readable stream to stop the flow if the writable stream’s buffer fills beyond the `highWatermark`.

While `highWaterMark` is not a hard limit but only a threshold, it’s important to adhere to that threshold when building custom streams to avoid data losses or undesirable memory usage. You can read more about this [in the official documentation](https://nodejs.org/api/stream.html#stream_buffering).

## Let’s put them all together

So far, we discussed different types of streams and how to use them. Let’s now try to put them all together and visualise a real-life example.

The following is a design of a simple image service I built some time back. In this service, an image is retrieved from an S3 bucket, and served as a resized image to the end-user.

If we build this without streams, we will fetch the whole file from the S3 bucket and keep it in the memory, resize the whole image at once, and then send the resized image to the end-user.

However, with streams, we can chain the above process in a very efficient manner to improve speed and optimise the memory usage in our application.

Since the data stream coming from the S3 bucket is a readable stream, we can pipe it straightaway to a transform stream where it’s resized. Since the transform stream is also readable, we can pipe it to the response stream directly so that a chunk of data coming from the S3 bucket is resized and sent to the user without having to wait for the whole file from S3 bucket.

![A%20Visual%20Guide%20to%20NodeJS%20Streams%20In%20NodeJS,%20stream%20a884a889ecf64e53b72e70ec43e111e0/19_a9Fpk8MSlkZEi7V0q87Q.png](A%20Visual%20Guide%20to%20NodeJS%20Streams%20In%20NodeJS,%20stream%20a884a889ecf64e53b72e70ec43e111e0/19_a9Fpk8MSlkZEi7V0q87Q.png)

> If you are curious, feel free to try to build this API on your own and let me know if you have any questions. Tip: You can have a look at sharp NPM module which can be used to build the image processing capability. Although, sharp uses Duplex streams instead of Transform streams at the time of this writing due to the reason mentioned here.
> 

In my next article, I explain how we can use streams in practical applications.

In this article, I wanted to visualise a few of the key concepts in NodeJS streams for ease of understanding. Please let me know if you have any feedback on this article which will be very helpful for me not only to improve this article but to write more helpful and detailed content in the future. I plan to write a few more detailed articles about the advanced concepts in streams, memory leaks and many more. So stay tuned in. Thanks.