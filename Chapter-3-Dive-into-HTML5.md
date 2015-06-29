
### localStorage and sessionStorage
- Both of them survive page reloads and quite identical API wise, the only thing distinguishes them is sessionStorage will be cleared once the browser session is over (window close) but localStorage will persist forver unless you do it manually. 
- 'storage' event is triggered on window object whenever any changes happen on localStorage.

### Cookies
- As cookies are used for authentication purposes and persistence of user data, all cookies valid for a page are sent from the browser to the server for every request to the same domain - this includes the original page request, any subsequent Ajax requests, all images, stylesheets, scripts and fonts. For this reason cookies should not be used to store large amounts of information.

- *localStorage, sessionStorage and cookies are all subject to "same-origin" rules which means browsers should prevent access to the data except from the domain that set the information to start with.*

- *localStorage, sessionStorage and cookies are all client storage solutions. Session data is held on the server where it remains under your direct control.*

### Web Worker
- A web worker is a JavaScript that runs in the background, independently of other scripts, without affecting the performance of the page. You can continue to do whatever you want: clicking, selecting things, etc., while the web worker runs in the background.
- Data is sent between workers and the main thread via a system of messages — both sides send their messages using the `postMessage()` method, and respond to messages via the `onmessage` event handler (the message is contained within the Message event's data attribute.) The data is *copied* rather than shared.
 
### Application Cache
- With HTML5 it has become easier now to make your web application offline accessible. You only have to serve a manifest file which turns out to be a simple text file, which tells the browser what to cache (and what to never cache).
- Manifest file looks something like this `<html manifest="demo.appcache">`

```
CACHE MANIFEST  // cache 
/theme.css
/logo.gif
/main.js

NETWORK:   // never cache
login.asp

FALLBACK: 
/html/ /offline.html
```
- For a webpage to use application cache, need to add an attribute like this `<html manifest="manifest_file.appcache">`
- But be careful with what you cache, once a file is cached, the browser will continue to show the cached version, even if you change the file on the server. To ensure the browser updates the cache, you need to change the manifest file.

### Semantics
- `<nav>` represents a section with navigation links.
- `<section>` represents a generic section of document/application, it can also have its own `<header>` as well as a `<footer>`. `<section>` is analogous to a section of a printed book that contains chapters or a section of a newspaper that contains news items.
- `<article>` represents a section which can be *independently distributable or reusable*.
- `<aside>` is intended to house *extra* content that is related to the surrounding content but at the same time is a standalone piece of content in itself.
- `<figcaption>` defines a caption for `<figure>`.
- `<mark>` highlights the text.


### Recommended
- http://www.developer.com/lang/understanding-the-proper-way-to-lay-out-a-page-with-html5.html
- https://developer.mozilla.org/en-US/docs/Web/API/Web_Workers_API/Using_web_workers
- http://www.html5rocks.com/en/tutorials/appcache/beginner/
- http://diveintohtml5.info/detect.html
- https://developers.whatwg.org/
- http://diveintohtml5.info/semantics.html
- http://www.smashingmagazine.com/2011/11/18/html5-semantics/
- http://html5doctor.com/lets-talk-about-semantics/
