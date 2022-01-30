# Everything You Ever Wanted to Know About WebRTC

Source: Article
Status: Unprocessed
URL: https://blog.openreplay.com/everything-you-ever-wanted-to-know-about-webrtc

![https://blog.openreplay.com/static/2302e50bef5fb5a69ae3970b8834d403/6050d/hero.png](https://blog.openreplay.com/static/2302e50bef5fb5a69ae3970b8834d403/6050d/hero.png)

---

![hero.png](Everything%20You%20Ever%20Wanted%20to%20Know%20About%20WebRTC%206e56078262ec462c880ec4e4213234d5/hero.png)

Live messaging, streaming, Torrents, and other similar **real-time data transfer** techniques have greatly affected and improved our virtual experiences. First, they were available natively, now through the web, bringing an impressive amount of possibilities to this universal platform. That’s all thanks to APIs known as [WebSocket](https://developer.mozilla.org/en-US/docs/Web/API/WebSocket) and [WebRTC](https://developer.mozilla.org/en-US/docs/Web/API/WebRTC_API).

## WebSocket revision

Now, I bet that you’ve heard of WebSocket. In fact, you’ve likely used it in some of your previous projects. Still, if not, here’s a brief overview.

WebSocket is a simple API that allows you to connect your clients **indirectly**, i.e., through a server. Basically, if one user wants to send some data to the other one, they both need to be **connected with the server** first and then pass the data through it. This approach naturally comes with some pros and cons. While it allows you to optionally process data on the server-side and assures the completeness of sent information (through [TCP protocol](https://en.wikipedia.org/wiki/Transmission_Control_Protocol)), it isn’t really fast. Because of the proxy-like server, a generic transfer can take up to 1 second, which isn’t much, but can make a huge difference in use-cases like audio and video calls.

That’s why WebRTC was introduced back in 2011. And, even if quite a lot of time has passed since then, its complexity and cross-browser support concerns result in beginners still having a hard time learning and using it. That’s why, in this post, we’ll go through the basics of WebRTC and explaining everything as simply as possible.

WebRTC stands for **Web Real-Time Communication**. The key concept to understand about it is that it’s meant for **direct connection**. This means that after the connection has been established (more on that later), in most cases, you don’t need any sort of server being involved in data transfer. That translates to, of course, faster transfer speeds. This fact makes it the best choice right now for audio/video streaming or creating P2P networks like [Torrent](https://webtorrent.io/).

### Servers in WebRTC

Don’t get me wrong tho. You still need a server - even when working with WebRTC. It’ll be used in a process called *“signaling”*, where the **peers** will be connected to each other. After that, all the data will be transferred directly between the peers in an encrypted state. This means that a WebRTC connection is **secure by default**.

Other than that, keep in mind that servers can still play other roles in a WebRTC connection. For example, they can serve as an always-online peers, ready to transfer or backup data at any time.

### Browser support

Because WebRTC is newer than e.g. WebSocket, it isn’t really backward-compatible, resulting in no support for IE and all older browsers. Still, according to *[caniuse.com](https://caniuse.com/#feat=rtcpeerconnection)*, it’s supported by more than **94%** of the reported browsers, so no worries here.

## Three in one

WebRTC is, in fact, a **collection of different APIs** rather than a single one. That’s why we’re not going to cover all but only the core parts of WebRTC. These are:

- **MediaStream API** - for getting access to user’s camera and audio (media);
- **RTCPeerConnection** & **RTCDataChannel** - for actual WebRTC connection;

While not being a part of the WebRTC connection process per se, MediaStream API, with its capabilities of capturing **video** and **audio** data through user’s device, is vital to one of WebRTC’s main use-cases - video/audio streaming.

### Video and audio

At the heart of MediaStream API is the `getUserMedia()` method of the `navigator.mediaDevices` object. Note that this object will only be available when you’re working in an **HTTPS** ****(secured) context.

```
1const getMedia = () => {2    const constraints = {7        const stream = await navigator.mediaDevices.getUserMedia(constraints);9    } catch (err) {
```

The method takes what’s called a *constraints* object and returns a promise that resolves to a new `MediaStream` instance. Such an interface is a representation of currently streamed media. It consists of zero or more separate `MediaStreamTrack`s, each representing video or audio track, from which audio tracks consist of right and left channels (for stereo and stuff). These tracks also provide some special methods and events if you need further control.

### Constraints

Let’s now talk about our [constraints object](https://developer.mozilla.org/en-US/docs/Web/API/MediaStreamConstraints), as this is a very important piece. It’s used to **configure** our `getUserMedia()` request and the resulting stream. This object can have two properties of either boolean or object value - `audio` and `video`.

```
2const constraints = {3    video: true,4    audio: true,
```

By setting both of them to true, we’re requesting access to the user’s default video and audio input devices, with default settings applied. Know that for `getUserMedia()` to work, you have to set at least one of those two properties.

If you want to configure your media source device settings further, you’ll need to pass an object. The list of properties available here is quite long and differs based on the type of track it’s applied to (video, audio). You can see a complete list of those [here](https://developer.mozilla.org/en-US/docs/Web/API/MediaTrackConstraints) and check for the available ones with the `getSupportedConstraints()` method.

So, let’s say that we want to be a bit more specific this time, and specify some additional configuration for our video track. That’ll be its width, height, and input device.

```
1const getConstraints = async () => {2    const supportedConstraints = navigator.mediaDevices.getSupportedConstraints();3    const video = {};5    if (supportedConstraints.width) {6        video.width = 1920;8    if (supportedConstraints.height) {9        video.height = 1080;11    if (supportedConstraints.deviceId) {12        const devices = await navigator.mediaDevices.enumerateDevices();13        const device = devices.find((device) => {14            return device.kind == "videoinput";17        video.deviceId = device.deviceId;20    return { video };
```

Notice how we check if the given constraint is supported (although all used above should always be - unless there’s no input device), and use the `enumerateDevices()` method to check for **available input devices**, together with setting the video’s resolution. It returns a promise which resolves to an array of `MediaDeviceInfo` objects, which we later use, to select the first one in line for video input.

Then, a simple edit to our `getMedia()` function, and we’re good to go!

### Screen capture

You might be interested in hearing that’s there’s also a method for accessing the device screen (and even sound in the latest browsers), called [Screen Capture API](https://developer.mozilla.org/en-US/docs/Web/API/Screen_Capture_API), which consists of a single `getDisplayMedia()` method.

There’s a lot of **potential** in using the `getUserMedia()` and `getDisplayMedia()` methods. Especially when combined with, e.g., Canvas and Web Audio APIs. But, as this is a topic for another day, we’re only interested in previewing our streams with simple `<video>` and `<audio>` elements.

As for actually using those from JS:

```
3const video = document.querySelector("video");4const audio = document.querySelector("audio");6video.srcObject = stream;7audio.srcObject = stream;
```

## WebRTC-based interaction: OpenReplay Assist

Debugging a web application in production may be challenging and time-consuming, however through the use of **[OpenReplay’s Assist](https://github.com/openreplay/openreplay)**, you can see the live screen of your users and even jump on a quick call with them. All thanks to the power of WebRTC.  [OpenReplay](https://github.com/openreplay/openreplay) is an Open-source alternative to FullStory, LogRocket and Hotjar. It allows you to monitor and replay everything your users do and shows how your app behaves for every issue.

Happy debugging, for modern frontend teams - [Start monitoring your web app for free](https://github.com/openreplay/openreplay).

The RTCPeerConnection is the main interface behind any WebRTC connection. It hides a lot of complex stuff like data encoding, encryption, processing and more, in a small and somewhat user-friendly API.

### Signaling

Before we start sending data, we need to first connect the two or more peers in the signaling process. As more than 2 peers would require special handling and a [TURN server](https://webrtc.org/getting-started/turn-server#:~:text=The%20term%20stands%20for%20Traversal,and%20as%20cloud%20provided%20services.), we’ll stick to the basics and work with only 2.

As the `RTCPeerConnection` relies on events, we’ll use these and something called `RTCIceCandidate` to set up our connection. ICE stands for **Internet Connectivity Establishment** and indicates the established protocol and routing used throughout the connection. Here you can, e.g., decide between the UDP and TCP protocols, depending on whether you need your data to be delivered fast with some possible losses or otherwise.

```
2const localConnection = new RTCPeerConnection();4const remoteConnection = new RTCPeerConnection();
```

Because demonstrating snippets with the involvement of server code can be tough, we’ll work with two connections created in the same environment. Don’t worry - if you already know WebSocket or any other form of data transfer for that matter, you should be able to use the herein code for real-world scenarios relatively easily.

After creating our connections, we’ll need to set up their respective `icecandidate` event handlers to listen for possible offers.

```
1localConnection.addEventListener("icecandidate", async (event) => {2    if (event.candidate) {4        try {6            await remoteConnection.addIceCandidate(event.candidate);7        } catch {13remoteConnection.addEventListener("icecandidate", async (e) => {14    if (e.candidate) {18            await localConnection.addIceCandidate(e.candidate);19        } catch {
```

With the code above, we listen to new ICE candidates and accept them immediately on both sides. In reality, this process can take a bit longer. Generally, the whole idea behind it is that the users will offer each other different connection configurations, until both sides settle on one, and the connection will start. It’s at that time that you will need the server to exchange the offers.

```
1const connect = async () => {3        const offer = await localConnection.createOffer();5        await localConnection.setLocalDescription(offer);8        await remoteConnection.setRemoteDescription(12        const answer = await remoteConnection.createAnswer();14        await remoteConnection.setLocalDescription(answer);17        await localConnection.setRemoteDescription(
```

Now we move onto creating an offer. You can do just that with the `createOffer()` call, to then use it to configure the local connection. After that, we have to send this configuration to the remote connection, where it’ll be either accepted or rejected. Here, as we don’t do any decision-making process, we’re accepting any configuration up-front. We do this using the `setRemoteDescription()`, and then we send the return information to be accepted again on the local side.

After all the “negotiations” are done, the `icecandidate` event will be fired, and the signaling process is complete.

### Streaming

So, with signaling done - somewhat of the toughest part of the process - we can now go straight to streaming.

I’ve already shown you how to get a `MediaStream` object from one of the user’s input devices. We’ll use that for this demo.

Let’s assume that we have a `MediaStream` object ready to go. In this case, you can use the `addTrack()` method to start transmitting individual tracks. It’s worth noting that there used to be an `addStream()` method to add whole `MediaStream`s at once, but it’s now obsolete and you shouldn’t use it (although some browsers might still support it).

```
1const startStreaming = async () => {2    const stream = await navigator.mediaDevices.getUserMedia({3        video: true,4        audio: true,7    for (const track of stream.getTracks()) {8        localConnection.addTrack(track);
```

On the receiving side, create a new `MediaStream` with its constructor, and listen for `track` events. Add all incoming tracks to the stream, and attach the stream itself to a video element.

```
1const startReceiving = () => {2    const video = document.getElementById("video");3    const stream = new MediaStream();5    video.srcObject = stream;6    remoteConnection.addEventListener("track", (event) => {7        stream.addTrack(event.track);
```

Now, to make the system work, you need to remember to set up streaming and receiving **before** you make an offer. In our case, this translates to before the `connect()` call.

```
1const run = async () => {2    await startStreaming();4    startReceiving();6    connect();9run();
```

If you’d like to update the streamed tracks down the line, you’ll need to handle `negotiationneeded` event on the `RTCPeerConnection` and renegotiate the offer there.

Apart from streams, you can also use WebRTC for transferring arbitrary data. That’s thanks to `RTCDataChannel`.

To create a data channel, you have to use the `createDataChannel()` method of `RTCPeerConnection`, passing the channel’s name as a parameter.

```
1const startSendingData = async () => {2    const dataChannel = localConnection.createDataChannel("my-data-channel");
```

On the other side, listen for `datachannel` events, and extract `channel` property from the event object.

```
1const startReceivingData = () => {2    remoteConnection.addEventListener("datachannel", async (event) => {3        const dataChannel = event.channel;
```

To actually use the channel, you need first to wait for it to open, using the `open` event listener. After that’s done, you can use the `send()` method to send [all kinds of data](https://developer.mozilla.org/en-US/docs/Web/API/RTCDataChannel/send#parameters) and receive it on the other side within the `message` event handler.

```
1const useDataChannel = (dataChannel, onMessage) => {2    return new Promise((resolve) => {3        dataChannel.addEventListener("open", () => {4            dataChannel.addEventListener("message", (event) => {5            if (onMessage) {6                onMessage(event);9            resolve((message) => {10                dataChannel.send(message);
```

Above, we’ve got a simple React Hook-like wrapper around `RTCDataChannel`. Its Promise resolves on `open`, returning a function for sending data and allowing for an optional callback to handle `message` events coming from the other side.

You can use the wrapper like so in the original connection functions:

```
1const startSendingData = () => {2    const dataChannel = localConnection.createDataChannel("my-data-channel");3    const sendMessage = useDataChannel(dataChannel, (event) => {4        console.log("Local:", event.data);5    }).then((sendMessage) => {6        sendMessage("Message from local");9const startReceivingData = () => {10    remoteConnection.addEventListener("datachannel", (event) => {11        const dataChannel = event.channel;12        const sendMessage = useDataChannel(dataChannel, (event) => {13            console.log("Remote:", event.data);14        }).then(() => {15            sendMessage("Message from remote");
```

You can initiate the system similarly to how it was done for streaming - with `connect()` function called last.

```
1const run = async () => {6    connect();
```

Note that you shouldn’t `await` for the channel to open - it’ll happen after the connection is made. To avoid confusion and illustrate this intention in both `startSendingData()` and `startReceivingData()` I’ve used the `then()` instead of `async`/`await`.

## Conclusion

As you can see, working with WebRTC API isn’t that hard. Furthermore, with additional help from WebSocket, or a public TURN server, you shouldn’t have much problem with establishing production-ready connections for 2 or more peers.

With the ability to both stream video and audio and exchange any arbitrary data directly between peers, WebRTC is a powerful tool for building performant, cost-efficient real-time applications.