# socketkit/awacs: Next-gen mobile first analytics server (think Mixpanel, Google Analytics) with built-in encryption supporting HTTP2 and gRPC. Node.js, headless, API-only, horizontally scaleable.

Source: Website
Status: Unprocessed
URL: https://github.com/socketkit/awacs

[https://opengraph.githubassets.com/cee1918ad66bfd6a12fc602f6ba47c1706ddd137f1b3753d593a627c2478281f/socketkit/awacs](https://opengraph.githubassets.com/cee1918ad66bfd6a12fc602f6ba47c1706ddd137f1b3753d593a627c2478281f/socketkit/awacs)

---

# 

![socketkit%20awacs%20Next-gen%20mobile%20first%20analytics%20se%20132cced5a16c4aa0a799121c8ea498c7/awacs-logo.png](socketkit%20awacs%20Next-gen%20mobile%20first%20analytics%20se%20132cced5a16c4aa0a799121c8ea498c7/awacs-logo.png)

![socketkit%20awacs%20Next-gen%20mobile%20first%20analytics%20se%20132cced5a16c4aa0a799121c8ea498c7/badge.svg](socketkit%20awacs%20Next-gen%20mobile%20first%20analytics%20se%20132cced5a16c4aa0a799121c8ea498c7/badge.svg)

[socketkit%20awacs%20Next-gen%20mobile%20first%20analytics%20se%20132cced5a16c4aa0a799121c8ea498c7/68747470733a2f2f696d672e736869656c64732e696f2f636f766572616c6c732f6769746875622f736f636b65746b69742f61776163732e7376673f7374796c653d666c61742d737175617265](socketkit%20awacs%20Next-gen%20mobile%20first%20analytics%20se%20132cced5a16c4aa0a799121c8ea498c7/68747470733a2f2f696d672e736869656c64732e696f2f636f766572616c6c732f6769746875622f736f636b65746b69742f61776163732e7376673f7374796c653d666c61742d737175617265)

[socketkit%20awacs%20Next-gen%20mobile%20first%20analytics%20se%20132cced5a16c4aa0a799121c8ea498c7/68747470733a2f2f696d672e736869656c64732e696f2f6769746875622f6c6963656e73652f736f636b65746b69742f61776163732e7376673f7374796c653d666c61742d737175617265](socketkit%20awacs%20Next-gen%20mobile%20first%20analytics%20se%20132cced5a16c4aa0a799121c8ea498c7/68747470733a2f2f696d672e736869656c64732e696f2f6769746875622f6c6963656e73652f736f636b65746b69742f61776163732e7376673f7374796c653d666c61742d737175617265)

## Introduction to Awacs

Next-gen behavior analysis server (think Mixpanel, Google Analytics) with built-in encryption supporting HTTP2 and gRPC. Node.js, headless, API-only, horizontally scaleable.

## Installation

We support [Docker](https://awacs.socketkit.com/guides/deployment/docker), [Kubernetes](https://awacs.socketkit.com/guides/deployment/kubernetes), and [Helm](https://awacs.socketkit.com/guides/deployment/helm) out of the box.

## Security

We take security seriously in Awacs. We believe that security & privacy is a human right, and should be done properly.

### Authorization

Every active application in Awacs has a unique authorization token to tell the server where the information belongs to. This token is sent using the x-socketkit-key HTTP header. It's recommended to have an SSL certificate in between the client and server to make it harder for an attacker to read the application authorization token.

### Request Signing

It's required that every request sent to Awacs public API should be signed with ed25519 on the client side. This digital signature algorithm enables us that the information did not get manipulated in the transit between client and server. Signed payload is sent through the `x-signature` HTTP header.

## High Availability

We have a solid health check mechanism which allows us to have the perfect horizontally scaleable infrastracture. Additionally, we support [Prometheus](http://prometheus.io/) and [OpenTelemetry](https://opentelemetry.io/) out of the box.

## SDKs

We have a variety of SDKs for Awacs and additionally support OpenAPI auto-generated SDKs.

- JavaScript: Available on [Github](https://github.com/socketkit/socketkit-js).
- Swift: Available on [Github](https://github.com/socketkit/socketkit-swift) **[WIP]**

## Contributing to Awacs

We welcome every contribution to Awacs with love. Please read our [CONTRIBUTING guide](https://github.com/socketkit/socketkit/blob/main/CONTRIBUTING.md) for more details.