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
