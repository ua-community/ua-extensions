We have a few parts that make up this pattern:

1. Some kind of **context** the protocol is anchored to.
2. Has some internal **state**, or data in other words, that may be communicated externally.
3. An **interface** that can be used to trigger actions or execute functions that provide a result.

This pattern recognises the following protocols/standards:

- [Autonomous custom elements](https://developer.mozilla.org/en-US/docs/Web/API/Web_components/Using_custom_elements) (DOM)
- [Matrix Widgets](https://matrix.org/blog/2017/08/23/introducing-matrix-widgets/)
- [Mini Apps](https://miniapps.farcaster.xyz/docs/specification) (Farcaster)
- [OpenFrames](https://www.openframes.xyz)
- [Peergos apps](https://book.peergos.org/features/apps.html)
- [Web Activities](https://wiki.mozilla.org/WebActivities)
- [Web Applets](https://github.com/unternet-co/web-applets)
- [Web Intents](https://www.w3.org/TR/web-intents/)
- [Web Tiles](https://hackmd.io/@robin-berjon/tiles)
- [WebXDC](https://webxdc.org/docs/)

Another way of looking at this is [information substrates](https://www.youtube.com/watch?app=desktop&v=ntaudUum06E&themeRefresh=1). We could say that a **context**¹ is a substrate, the **state**² or data being the material, and this substrate having an **interface**³ making it an instrument.



## Communication

Many of the listed approaches above have a different **interface**³, and others standardize on the `postMessage` Web API. The former option is usually chosen because the protocol works outside the standard web same-origin **context**¹.

We might see contexts as sandboxes, to list a few:

- **Same-origin model**: The **state**² is contained within the same DNS origin. This can be further divided into  the different threads: main UI thread, workers (web, shared, service, etc). All contexts can communicate with each other using the `postMessage` interface.
- **Web Tiles**: The state is contained within a tile. Wishes are the interface that is used to get data in and out the context.
- **WebXDC**: The context is a container which has all the files that make up a web application.



## What can we learn from this?

When we write a web application we must recognize in what environment it is executed and how that environment influences our application. That environment is also the reason why so many of these protocols use a different interface.

Another pattern here is that the interface is of a SDK-like shape, a few examples:

- Custom elements: postMessage is used when a custom element is combined with a worker
- Matrix Widgets: SDK with a postMessage transport
- Mini Apps: SDK that wraps postMessage
- Web Activities: SDK that wraps postMessage
- Web Applets: SDK that wraps postMessage
- Web Intents: `navigator.startActivity()`
- Web Tiles: `window.makeWish()`
- WebXDC: `window.webxdc.sendUpdate()`

Perhaps a question we can ask ourselves here, what if every protocol in this list opts for `postMessage` directly and the difference lies in the data format + message target instead? In this manner we're not changing the way how we write web pages, but instead what is communicated. Is that realistic?



## Post Message Interface

One interesting option here is that we can set the [`targetOrigin`](https://developer.mozilla.org/en-US/docs/Web/API/Window/postMessage#targetorigin) argument to `*`. Though MDN does warn us that in that case extensions can no longer discern the origin. Another option would be to listen to the messages from a given context. Annoyingly postMessage doesn't listen for messages from the same context. Though [extensions](https://github.com/niexia/postMessage-catcher/tree/62ca9d114f03d30c10870cb726200813a4451100) that deal with postMessage observing get around that by creating an iframe that does the observing.

But supposing we could easily listen for messages from the same context, would that enable progressive enhancement? For example, instead of doing `window.makeWish()` directly we could listen for messages using `context.addEventListener('message')`, filter out the appropriate messages and then do whatever `window.makeWish()` does. In that scenario a Web Tile could be loaded in a regular browser, where `window.makeWish` doesn't exist, and there might instead be a browser extension which understands the data coming through the postMessage interface. Interop on the data format.



## Composition

A large portion of these protocols serve to pull apart the monolithic app or cloud-first paradigms. They mean to redefine what the web is, or at least a part of it. What is the overlap between these "definitions" of the web? Any materials or instruments shared by various proposals?

Custom elements and web workers seem solid choices here. Though we can't create a set of web components that would work in all environments or protocols. What we can do is find the optimal balance to divide them, what the architecture is and how they communicate. Find abstractions that work on the most amount of environments while still keeping the performance and user agency of the software intact.

For example, you can split up your custom elements in such a way that it allows easy usage in both Web Tiles and in a regular browser application. Separate logic and UI.



## Related links

- [Custom elements manifest](https://github.com/webcomponents/custom-elements-manifest), similar to Web Tile manifests.
