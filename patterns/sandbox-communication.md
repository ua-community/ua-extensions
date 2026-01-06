We have a few parts that make up this pattern:

1. Some kind of **context** the protocol is anchored to.
2. Has some internal **state**, or data, that may be communicated externally.
3. An **interface** that can be used to trigger actions or execute functions that provide a result.

This pattern recognises the following protocols/standards:
- [Matrix Widgets](https://matrix.org/blog/2017/08/23/introducing-matrix-widgets/)
- [Mini Apps](https://miniapps.farcaster.xyz/docs/specification) (Farcaster)
- [OpenFrames](https://www.openframes.xyz)
- [Peergos apps](https://book.peergos.org/features/apps.html)
- [Web Activities](https://github.com/google/web-activities)
- [Web Applets](https://github.com/unternet-co/web-applets)
- [Web Intents](https://www.w3.org/TR/web-intents/)
- [Web Tiles](https://hackmd.io/@robin-berjon/tiles)
- [WebXDC](https://webxdc.org/docs/)



## Communication

Many of the listed approaches above have a different **interface**³, and others standardize on the `postMessage` Web API. The former option is usually chosen because the protocol works outside the standard web same-origin **context**¹.

We might see contexts as sandboxes, to list a few:

- **Same-origin model**: The **state**² is contained within the same DNS origin. This can be further divided into  the different threads: main UI thread, workers (web, shared, service, etc). All contexts can communicate with each other using the `postMessage` interface.
- **Web Tiles**: The state is contained within a tile. Wishes are the interface that is used to get data in and out the context.
- **WebXDC**: The context is a container which has all the files that make up a web application.



## What can we learn from this?

When we write a web application we must recognize in what environment it is executed and how that environment influences our application. That environment is also the reason why so many of these protocols use a different interface.

Another pattern here is that the interface is of a SDK-like shape, a few examples:

- Matrix Widgets: SDK with a postMessage transport
- Mini Apps: SDK that wraps postMessage
- Web Activities: SDK that wraps postMessage
- Web Applets: SDK that wraps postMessage
- Web Intents: `navigator.startActivity()`
- Web Tiles: `window.makeWish()`
- WebXDC: `window.webxdc.sendUpdate()`

Perhaps a question we can ask ourselves here, what if every protocol in this list opts for `postMessage` directly and the difference lies in the data format + message target instead? In this manner we're not changing the way how we write web pages, but instead what is communicated. Is that realistic?



## `postMessage`

One interesting option here is that we can set the [`targetOrigin`](https://developer.mozilla.org/en-US/docs/Web/API/Window/postMessage#targetorigin) argument to `*`. Though MDN does warn us that in that case extensions can no longer discern the origin. Another option would be to listen to the messages from a given context. Annoyingly postMessage doesn't listen for messages from the same context. Though [extensions](https://github.com/niexia/postMessage-catcher/tree/62ca9d114f03d30c10870cb726200813a4451100) that deal with postMessage observing get around that by creating an iframe that does the observing.

But supposing we could easily listen for messages from the same context, would that enable progressive enhancement? For example, instead of doing `window.makeWish()` directly we could listen for messages using `context.addEventListener('message')`, filter out the appropriate and then do whatever `window.makeWish()` does. In that scenario a Web Tile could be loaded in a regular browser, where `window.makeWish` does not exist, and there might instead be a browser extension which understands the data coming through the postMessage interface. Interop on the data format.
