# EJ exrcices

## Chapter 8 - Bugs and Errors

### Retry

```javascript
class MultiplicatorUnitFailure extends Error {}

function primitiveMultiply(a, b) {
  if (Math.random() < 0.2) {
    return a * b;
  } else {
    throw new MultiplicatorUnitFailure("Klunk");
  }
}

function reliableMultiply(a, b) {
  for (;;) {
    try {
      let multi = primitiveMultiply(a, b); 
      return multi;      
    } 
    catch (e) {       
    }
  }
}

console.log(reliableMultiply(8, 8));
// → 64
```

### The locked box

```javascript
const box = {
  locked: true,
  unlock() { this.locked = false; },
  lock() { this.locked = true;  },
  _content: [],
  getcontent() {
    if (this.locked) throw new Error("Locked!");
    return this._content;
  }
};

function withBoxUnlocked(body) {
  if (box.locked) {  
    box.unlock();
    try {
      return body();
    }
    finally {
      box.lock();
    }
  } else {
    return body(); 
  }
}

withBoxUnlocked(function() {
  box.getcontent().push("gold piece");
});

console.log(box._content);

try {
  withBoxUnlocked(function() {
    throw new Error("Pirates on the horizon! Abort!");
  });
} catch (e) {
  console.log("Error raised:", e);
}

console.log(box.locked); // → true
```
