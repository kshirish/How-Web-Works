## What is Shadow DOM?

`SVG`, `input` `slider`, `audio`, `video` etc. they all use it to hide/encapsulate the implementation from the user. Generally in case of `<video>`, we don't indulge ourselves in the petty details rather we just use it. But behind the functioning of `<video>`, a lot of code has been written which can be called as **shadow dom**. Shadow DOM refers to the ability of the browser to include a subtree of DOM elements into the rendering of a document, but not into the main document DOM tree.


## Can I use it?

[Shadow Dom Support](http://caniuse.com/#search=shadow%20dom)

## See it in action

```html
<html>
  <head></head>
  <body>
    <h1 id="foo">I am your host.</h1>
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

- By default usual styling won't get applied here i.e. it only works for main DOM tree but not for shadow trees. For it, we can do something like

```js
    shadow.innerHTML = '<style>p { color: red; }</style>';
```
 - Still you want to apply normal styles to your shadow DOM as well, you can do like
 
 ```js
    shadow.applyAuthorStyles = true;
 ```
 - `:host` allows you to select and style the element hosting a shadow tree. More on [styles](http://www.html5rocks.com/en/tutorials/webcomponents/shadowdom-201/)
  
```js
  shadow.innerHTML = '<style>:host { text-transform: uppercase; }</style>';
```
## Better road with `<template>` 

```html
<html>
  <head></head>
  <body>
    <h1 id="foo">I am your host.</h1>
    
    <template id="shadowTemplate">
    
      <style>
        h2 {color: red;}
        h3 {color: green;}
        h4 {color: yellow;}
        h5 {color: orange;}    
      </style>
      
      <h2>I am your shadow.</h2>
      <h3>me too.</h3>
      <h4>me tooo.</h4>
      <h5>me toooo.</h5>  
      
    </template>
    <script>
      var foo = document.getElementById('foo');
      var shadow = foo.createShadowRoot();
      var template = document.getElementById('shadowTemplate');
      var clone = document.importNode(template.content, true);
      shadow.appendChild(clone);
    </script>
  </body>
</html>
```

## Content vs implementation

HTML elements are compositional — you can put a button inside a table, for example. Till now, only shadow DOM is deciding the content of shadow host but we can do better. 

```html
<html>
  <head></head>
  <body>
    <h1 id="foo">I am your host.</h1>
    
    <template id="shadowTemplate">
    
      <style>
        ...
      </style>
      
      <!--  Content of shadow host will be injected here. -->
      <content></content>
      <h2>I am your shadow.</h2>
      <h3>me too.</h3>
      <h4>me tooo.</h4>
      <h5>me toooo.</h5>  
      
    </template>
    <script>
      ... 
    </script>
  </body>
</html>
```

- As soon as the shadow host's content changes, shadow DOM will be updated automatically. 
- By separating content and presentation, we can simplify the code that manipulates the content i.e. now we only need to deal with a simple structure containing one `<h1>` instead of several other tags.


## Advance `<content>`

```html
<h1 id="foo">
    <p>bald and fat.</p>
    <i>30 years old.</i>
    <div class="warning">I am the future.</div>    
</h1>
<template id="shadowTemplate">
    
<style>
    h2 {color: red;}
    h3 {color: green;}
    h4 {color: yellow;}
    h5 {color: orange;}    
</style>
    
  <div style="color: red;">
    <content select=".warning"></content>
  </div>
    
  <div style="color: blue;">
    <content select="i"></content>
  </div>
    
  <div style="color: yellow;">
    <content select="p"></content>
  </div>
    

<h3>me too.</h3>
<h4>me tooo.</h4>
<h5>me toooo.</h5>    
</template>
```

## Mutiple shadow DOMs

- Obviously later one will replace previous one.
```html
  <div id="foo">I am your host.</div>
  <script>
    var foo = document.getElementById('foo');
    var root1 = foo.createShadowRoot();
    var root2 = foo.createShadowRoot();
    root1.innerHTML = '<div>Root 1</div>';
    root2.innerHTML = '<div>Root 2</div>';
  </script>
```
- **Shadow insertion points** (`<shadow>`) are similar to normal insertion points (`<content>`) in that they're placeholders. However, instead of being placeholders for a host's content, they're hosts for other shadow trees.
```html
  <div id="foo">I am your host.</div>
  <script>
    var foo = document.getElementById('foo');
    var root1 = container.createShadowRoot();
    var root2 = container.createShadowRoot();
    root1.innerHTML = '<div>Root 1</div><content></content>';
    root2.innerHTML = '<div>Root 2</div><shadow></shadow>';
  </script>
```
- Reference to previous tree
```js
  root2.olderShadowRoot === root1;   //true
```
- Obtaining a shadow root
```js
  var root = host.createShadowRoot();
  host.shadowRoot === root; // true
```
