# EJ exercices 

## Chapter 4 - Objects and Arrays

### Exercice 1 - The sum of ranges

```javascript
function range(start, end, step = 1) {
  let result =  [];
  for (i = start; true ; i = i + step) {
    result.push(i);
    if (i == end) {
      break;
    }
  }
  return result;
}

function sum(array) {
  let result = 0;
  for (let element of array) {
    result = result + element;
  }
  return result;
}

console.log(range(1, 10)); // → [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
console.log(range(5, 2, -1)); // → [5, 4, 3, 2]
console.log(sum(range(1, 10))); // → 55
```

### Exercice 2 - Reversing an array

```javascript
function reverseArray(array) {
  let result = [];
  for (let i = array.length - 1; i >= 0 ; i--) {
    result.push(array[i]);
  }
  return result;
}

function reverseArrayInPlace(array) {
  let tmp;
  let middleIndex = Math.floor(array.length/2);
  for (let i = 0; i <= middleIndex; i++) {
    tmp = array[i];
    array[i] = array[array.length-i-1];
    array[array.length-1-i] = tmp;
  }  
}

console.log(reverseArray(["A", "B", "C"])); // → ["C", "B", "A"];
let arrayValue = [1, 2, 3, 4, 5];
reverseArrayInPlace(arrayValue);
console.log(arrayValue); // → [5, 4, 3, 2, 1]
```

### Exercice 3 - List

```javascript
function arrayToList(array) {
  list = { 
    value: array[0],
    rest: null
  };
  
  lastObject = list;
  for (let i = 1; i < array.length; i++) {
    element = array[i];
    
    lastObject.rest = { 
      value: element,
      rest: null
    }
    
    lastObject = lastObject.rest;
  }
  return list;
}

function listToArray(list) {
  let result = [];
  lastObject = list;
  result.push(lastObject.value);  
  
  while (lastObject.rest != null) {
    lastObject = lastObject.rest;
    result.push(lastObject.value);
  }
    
  return result;
}

function prepend(element, list) {
  let newList = {
    value: element,
    rest: list
  }
  
  return newList;
}

function nth(list, n) {
  lastObject = list;
  currentIndex = 0;
  
  while (currentIndex != n) {
    lastObject = lastObject.rest;
    currentIndex ++;
  }
  
  return lastObject.value;
}

console.log(arrayToList([10, 20])); // → {value: 10, rest: {value: 20, rest: null}}
console.log(listToArray(arrayToList([10, 20, 30]))); // → [10, 20, 30]
console.log(prepend(10, prepend(20, null))); // → {value: 10, rest: {value: 20, rest: null}}
console.log(nth(arrayToList([10, 20, 30]), 1)); // → 20
```
