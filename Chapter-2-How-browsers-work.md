### The Flow
- The way the browser interprets and displays HTML files is specified in the HTML and CSS specifications (maintained by W3C). 
- Essential components of a browser
  - **User interface**: this includes the address bar, back/forward button, bookmarking menu, etc. Every part of the browser display except the window where you see the requested page.
  - **Browser engine**: marshals actions between the UI and the rendering engine.
  - **Rendering engine**: responsible for displaying requested content. For example if the requested content is HTML, the rendering engine parses HTML and CSS, and displays the parsed content on the screen. For example, Gecko, webkit & Trident.
  - **Networking**: for network calls such as HTTP requests, using different implementations for different platform behind a platform-independent interface.
  - **JavaScript engine**: Used to parse and execute JavaScript code.  For example, V8
  - **Data storage**: This is a persistence layer. The browser may need to save all sorts of data locally, such as cookies. Browsers also support storage mechanisms such as localStorage, IndexedDB, WebSQL and FileSystem.
- ![alt Basic flow](http://www.html5rocks.com/en/tutorials/internals/howbrowserswork/webkitflow.png)
- Firefox blocks all scripts when there is a style sheet that is still being loaded and parsed. WebKit blocks scripts only when they try to access certain style properties that may be affected by unloaded style sheets.

### Event loop
- It is a programming construct that handles instructions in following order
  - Call stack 
  - Render Queue
  - Callback Queue
  
Recommended
- http://www.html5rocks.com/en/tutorials/internals/howbrowserswork/
- http://blog.carbonfive.com/2013/10/27/the-javascript-event-loop-explained/
- 2014.jsconf.eu/speakers/philip-roberts-what-the-heck-is-the-event-loop-anyway.html
