# EJNotes

## Chapter 15 - Handling events

Browsers allow us to register functions as handlers for specific events. Here is a basic example

````javascript
<p>Click this document to activate the handler.</p>
<script>
  window.addEventListener("click", () => {
    console.log("You knocked?");
  });
</script>
````

### Registering events

We can add an event listenner with Function `handlerF` to handle on a `node` the events triggered by `"xxx"` (such as `"click"`).

````javascript
node.addEventListener("xxx", handlerF)
````

We can also remove such event listenner

````javascript
node.removeEventListener("xxx", handlerF)
````

`handlerF` is a function that takes the event as an input and does the handling as a side effect. 
Events have properties that hold useful information on the event. 
Those properties depend on the event type (https://www.w3schools.com/jsref/obj_events.asp).

### Propagation

Events propagate from the node to its parent and so on... The propagation can be stopped using

````javascript
event.stopPropagation();
````

### Default handlers

For a specific node and a specific event several events may be registred and all will be called when such event occur on the node.
Some nodes have by default a registered handler. One can not remove it but can prevent it 
Since the default handler is the last handler to be called, any other registered handler may choose to cancel it using:

````javascript
event.preventDefault();
````

### Key events

"keyup", "keydown" are the main key event names.

The key name is accessed using `event.key`.
For special keys such as enter, it holds a string that names the key ("Enter", in this case). 
If you hold shift while pressing a key, that might also influence the name of the key—"v" becomes "V".

Modifier keys such as shift, control, alt, and meta (command on Mac) generate key events just like normal keys. 
But when looking for key combinations, you can also find out whether these keys are held down by looking at the 
`shiftKey`, `ctrlKey`, `altKey`...

````javascript
<p>Press Control-Space to continue.</p>
<script>
  window.addEventListener("keydown", event => {
    if (event.key == " " && event.ctrlKey) {
      console.log("Continuing!");
    }
  });
</script>
````


