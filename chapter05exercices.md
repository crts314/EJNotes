# EJ exercices 

## Chapter 5 - Higher-order functions

### Exercice 1 - Flattening

```javascript
let arrays = [[1, 2, 3], [4, 5], [6]];

function combineF(currentSummary, element) {
  return currentSummary.concat(element);
}

console.log(arrays.reduce(combineF, [])); // → [1, 2, 3, 4, 5, 6]
```

### Exercice 2 - Your own loop

```javascript
function loop(value, testF, updateF, bodyF) {
    while(testF(value)) {
      bodyF(value);
      value = updateF(value);
    }
}

loop(3, n => n > 0, n => n - 1, console.log);
// → 3
// → 2
// → 1
```

### Exercices 3 - Everything

```javascript
// Only one of the following should be used.

// implementation using the classic array loop
function every(array, testF) {
  for (let element of array) {
    if (!testF(element)) {
      return false;
    }
  }
  return true;
}

// implementation using the method some
function every(array, testF) {
  
  function test2F(element) {
    return !testF(element);
  }
  
  if(array.some(test2F)) {
    return false;
  }
  else {
    return true;
  }
}

console.log(every([1, 3, 5], n => n < 10)); // → true
console.log(every([2, 4, 16], n => n < 10)); // → false
console.log(every([], n => n < 10)); // → true
```

