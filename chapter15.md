# EJNotes

## Chapter 15 - Handling events

Browsers allow us to register functions as handlers for specific events. handlers are just callbacks.

### Registering events

We can add an event listenner with a function `handlerF` to handle on a `node` the events triggered by `"xxx"` (such as `"click"`).

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

For a specific node and a specific event, several handlers may be registred and all will be called when such event occur on the node.
Some nodes have by default a registered handler. One can not remove it but can prevent it 
Since the default handler is the last handler to be called, any other registered handler may choose to cancel it using:

````javascript
event.preventDefault();
````

### Key events

`"keyup"`, `"keydown"` are key event names.

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

### Mouse events

`"mousedown"`, `"mouseup"`, `"click"` and `"dblclick"` are mouse click event names.

If we want to know which mouse button was pressed, we can look at the event object’s button property.

````javascript
<button>Click me any way you want</button>
<script>
  let button = document.querySelector("button");
  button.addEventListener("mousedown", event => {
    if (event.button == 0) {
      console.log("Left button");
    } else if (event.button == 1) {
      console.log("Middle button");
    } else if (event.button == 2) {
      console.log("Right button");
    }
  });
</script>
````

`"mousemove"` is a mouse motion event name. 

This event can be used to track the position of the mouse.
A common situation in which this is useful is when implementing some form of mouse-dragging functionality.

we can use the buttons property (note the plural), which tells us about the buttons that are currently held down. 
When this is zero, no buttons are down. When buttons are held, its value is the sum of the codes for those buttons—the left button has code 1, the right button 2, and the middle one 4. 

To get precise information about the place where a mouse event happened, 
you can look at its clientX and clientY properties, which contain the event’s coordinates (in pixels) 
relative to the top-left corner of the window, 
or pageX and pageY, which are relative to the top-left corner of the whole document.

