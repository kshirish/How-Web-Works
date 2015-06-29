
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
 


### References
- https://developer.mozilla.org/en-US/docs/Web/API/Web_Workers_API/Using_web_workers
