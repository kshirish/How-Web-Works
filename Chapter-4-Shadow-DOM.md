## What is Shadow DOM?

SVG, input slider, audio, video etc. they all use it to hide/encapsulate the implementation from the user. Generally in case of <video>, we don't indulge ourselves in the petty details rather just use it. But behind the functioning of <video>, a lot of code has been written which can be called as *shadow dom*. Shadow DOM refers to the ability of the browser to include a subtree of DOM elements into the rendering of a document, but not into the main document DOM tree.


## Can I use it?

[Shadow Dom Support](http://caniuse.com/#search=shadow%20dom)

## See it in action

```html
<html>
  <head></head>
  <body>
    <h1 id="foo"></h1>
    <script>
      // create shadow DOM on the <h1> element above
      var foo = document.getElementById('foo');
      var shadow = foo.createShadowRoot();
      shadow.innerHTML = '<p>I am your shadow.</p>';
    </script>
  </body>
</html>
```

## Styling shadow DOM

Usual styling methods won't get applied here i.e. it only works for main DOM tree but not for shadow tree. For it, we can do something like :

```js
    shadow.innerHTML = '<style>p {color: red;}</style>';
```
