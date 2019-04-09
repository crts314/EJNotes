# EJNotes

## Chapter 14 - The Document Object Model (DOM)

### Document structure

You can imagine an HTML document as a nested set of boxes. 
Tags such as `<body>` and `</body>` enclose other tags, which in turn contain other tags or text.

```html
<!doctype html>
<html>
  <head>
    <title>My home page</title>
  </head>
  <body>
    <h1>My home page</h1>
    <p>Hello, I am Marijn and this is my home page.</p>
    <p>I also wrote a book! Read it
      <a href="http://eloquentjavascript.net">here</a>.</p>
  </body>
</html>
```

This page has the following structure

<p align="center">
  <img src="https://eloquentjavascript.net/img/html-boxes.svg">
</p>

Another way to visualize our document tree is as follows

<p align="center">
  <img src="https://eloquentjavascript.net/img/html-tree.svg">
</p>

This tree has two type of nodes:

- **Element nodes** : representing the tags in the html page 
- **Text nodes** : representing the text in the html page (They can only be leaves)

### Navigating the DOM

Every node has a set of methods that allow to move to the direct childs/parent.

<p align="center">
  <img src="https://eloquentjavascript.net/img/html-links.svg">
</p>

An alternative way of navigating is to look for an element based on its tag or id.

To access the first element node in the subtree of node with tag `ttt`

```javascript 
let nodeWeLookFor = node.getElementByTag("ttt");
```

To access the element node with id `123`.

```javascript
let nodeWeLookFor = document.getElementById("123");
```

### Modifying the DOM

To create a new element node with tag `ttt`

```javascript
let newNode = document.createElement("ttt");
```

To create a new text node with text `hello`

```javascript
let newNode = document.createTextNode("hello");
```

To append `newNode` as a child of `node`

```javascript
node.appendChild(ndewNode);
```

To append `newNode` as a child of `node` before one of its `existingChildNode`

```javascript
node.insertBefore(newNode, existingChildNode);
```

To replace a child of `node`, that is `existingChildNode`, with `newNode`. 
(if `newNode` is already in the tree, it will be removed from his old position in the tree) 

```javascript
node.replaceChild(newNode, existingChildNode);
```


