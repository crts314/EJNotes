# EJNotes

## Chapter 5 - Higher-Order Functions

### Definition and examples

Functions that operate on other functions, either by taking them as parmeters or by returning them, 
are called higher-order functions. Since we have already seen that functions are regular values, 
there is nothing particularly remarkable about the fact that such functions exist. The term comes from mathematics.

The following is a higher-order functions returning a function.

```javascript
function greaterThan(n) {
  return m => m > n;
}
let greaterThan10 = greaterThan(10);
console.log(greaterThan10(15)); // → true
```

The next higher-order function not only returns a function but also take a function as its parameter.

```javascript
function makeNoisy(functionToDebug) {
  return (param) => {
    let result = functionToDebug(param);
    console.log("called with", param, ", returned", result);
    return result;
  };
}
makeNoisy(Math.sqrt)(9); // → called with 9 , returned 3
```

### Array looping

Assume we have the following action that we want to apply to all elements of an array `a`.

```javascript
// Defining the action  
function actionF(element) {
  // Do something to element
}
```

`forEach` is a higher-order method of arrays that allows to loop and apply an action on all elements of an array.

```javascript
a.forEach(actionF);
```

As seen in chapter 4 the same thing could be done using the equivalent for loop 

```javascript
for (let element of a) {
  actionF(a);
}
```

### Array filtering

`filter` is a a higher-order method of arrays that allows filtering an array `a` based on a test function `testF`. 
This function does not modify the original array but rather creates and returns the new filtered array.

```javascript
let filtered = a.filter(testF);
```

This can be again achieved using the equivalent for loop

```javascript
let filtered = [];
for (let element of a) {
  if (testF(element)) {
    filtered.push(element);
  }
}
```

### Array transforming

`map` is a a higher-order method of arrays that allows transforming an array `a` 
based on a test function `transformF` that can transform a single element of the array. 
like `filter` it does not modify the original array but rather creates and returns the new transformed array.

```javascript
let mapped = a.map(testF);
```

This can be again achieved using the equivalent for loop

```javascript
let mapped = [];
for (let element of a) {
  newElement = transformF(element));
  mapped.push(newElement);
}
```

### Array summarizing

`reduce` is a a higher-order method of arrays that allosw summarizing an array `a` into a single summary value
based on a start summary value, 
and a function that combines the current summary value with an additional element of the array. 
Such function is usually like this.

```javascript
function combineF(currentSummary, element) { 
  // computes and returns the new currentSummary by combining currentSummary and element
}
```

like `filter` and `map` it does not modify the original array but rather computes and returns the summary value.

```javascript
let summary = a.reduce(combineF, start);
```

This can be again achieved using the equivalent for loop

```javascript
let summary = start;
for (let element of a) {
  summary = combineF(summary, element));
}
```

the start summary value is optional. If not provided, the first element of the array is considered as the start value,
the combine function is only applied starting from the second element of the array.

### Composition

Functions can be composed. The two following calls are equivalent

```javascript
// without composition
let intermediaryResult = f(x)
let finalResult = g(intermediaryResult)

// with composition
let finalResult = g(f(x))
```

Methods can be composed. The two following calls are equivalent

```javascript
// without composition
let intermediaryResult = x.f()
let finalResult = intermediaryResult.g()

// with composition
let finalResult = x.f().g()
```

























