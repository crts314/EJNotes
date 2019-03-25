# EJNotes

## Chapter 4 - Data Structures: Objects and Arrays

### Arrays

JavaScript provides a data type specifically for storing sequences of values. 
It is called an array and is written as a list of values between square brackets, separated by commas.

The i'th element of an array `a` (element at index i) is accessed like this `a[i]`

Indexing in JavaScript starts from `0`

### Properties

Values (including objects and arrays) have properties. inversly a property belongs to a value.

To access a property named `prop` we use the syntax `.prop` after the value with such property (or its binding).

Almost all JavaScript values have properties. The exceptions are `null` and `undefined`.

A property can hold a value like any regular binding. To not confuse with the value it belongs to. 

### Methods

Properties that contain functions are generally called methods of the value they belong to. 
For example `toUpperCase` is a method of every string.

```javascript
let sentence = "my way";
console.log(typeof sentence.toUpperCase); // → function
console.log(sentence.toUpperCase()); // → MY WAY
```

The value to which the method belongs to is also part of its input.

### Objects

Values of the type `object` are arbitrary collections of properties. 

One way to create an object is by using braces as an expression like in this example

```javascript
let day1 = {
  squirrel: false,
  events: ["work", "touched tree", "pizza", "running"]
};
```

Inside the braces, there is a list of properties separated by commas. Each property has a name followed by a colon and a value.

It is possible to assign a value to a property expression with the `=` operator. This will replace the property’s value if it already existed or create a new property on the object if it didn’t.

`delete` is a unary operator that, when applied to an object property, removes the named property from the object.

`in` is a binary operator that, when applied to a string and an object, produces true if and only if the object has a property named as the string.

`Object.keys` is a function with a single parameter. when called returns an array of the property names of the given parameter.

```javascript
console.log(Object.keys({x: 0, y: 0, z: 2})); // → ["x", "y", "z"]
```

### Immutability

The types of values discussed in earlier chapters, such as numbers, strings, and Booleans, are all immutable—it is impossible to change values of those types.

Objects work differently. You can change their properties, causing a single object value to have different content at different times.

Therefore there is a difference between having two references to the same object and having two different objects that contain the same properties at a given time. Because object can change, two objects are equal only if they conrrespond to the same bits in memory

```javascript
let object1 = {value: 10};
let object2 = object1;
let object3 = {value: 10};

console.log(object1 == object2);
// → true
console.log(object1 == object3);
// → false
```

### Array loops

The following two ways of looping on an array `a` are equivalent.

```javascript
for (let i = 0; i < a.length; i++) {
  let element = a[i];
  // Do something with element
}
````

```javascript
for (let element of a) {
  // Do something with element
}
````

### Arrray methods 

`push` and `unshift` add a new element respectively in the back and in the front of the array they belong to. 
`pop` and `shift` they remove and return the element respectively in the back and in the front of the array.

```javascript
let sequence = [1, 2, 3];
sequence.push(4);
sequence.push(5);
console.log(sequence); // → [1, 2, 3, 4, 5]
console.log(sequence.pop()); // → 5
console.log(sequence); // → [1, 2, 3, 4]
console.log(sequence.shift()); // → 1
console.log(sequence); // → [2, 3, 4]
sequence.unshift(10);
console.log(sequence) // → [10, 2, 3, 4]
```

`slice` takes start and end indices and returns an array that has only the elements between them. 
The start index is inclusive, the end index exclusive.

```javascript
console.log([0, 10, 20, 30, 40].slice(2, 4)); // → [20, 30]
console.log([0, 10, 20, 30, 40].slice(2)); // → [20, 30, 40]
```

The `concat` method can be used to glue arrays together to create a new array, similar to what the `+` operator does for strings.

```javascript
console.log(["a", "b"].concat(["c", "d"])); // → ["a", "b", "c", "d"]
```

`indexOf` method takes as parameter a value and returns the first index of the array where such value is stored.
When such value is not stored in the array; the method `indexOf` returns -1 instead of an index.

```javascript
console.log([0, 10, 20, 30, 40].indexOf(20)); // → 2
```

### String methods

`slice` and `indexOf`, resemble the array methods of the same name.
One difference is that a string’s `indexOf` can search for a string containing more than one character, 
whereas the corresponding array method looks only for a single element.

```javascript
console.log("coconuts".slice(4, 7)); // → nut
console.log("coconut".indexOf("o")); // → 1
console.log("coconut".indexOf("on")); // → 3
```

`trim` removes whitespace (spaces, newlines, tabs, and similar characters) from the start and end of a string.

```javascript
console.log("  okay \n ".trim()); // → okay
```

`padStart` takes the desired length and padding character as arguments 
and keeps adding the charachter as prefix until the the string reaches the desired length.

```javascript
console.log(String(6).padStart(3, "0")); // → 006
```

You can split a string on every occurrence of another string with `split` and join it again with `join`.

```javascript
let sentence = "Secretarybirds specialize in stomping";
let words = sentence.split(" ");
console.log(words); // → ["Secretarybirds", "specialize", "in", "stomping"]
console.log(words.join(". ")); // → Secretarybirds. specialize. in. stomping
```

A string can be repeated with the `repeat` method, which creates a new string containing multiple copies of the original string, glued together.

```javascript
console.log("LA".repeat(3)); // → LALALA
```

### Functions with an arbitrary number of parameters

It can be useful for a function to accept any number of parameters. This can be acheived thanks to the use of arrays

classic syntax example:

```javascript
// function definition 
function printAll(param1, otherParams) {
  console.log(param1);
  for (let element of otherParams) {
    console.log(element);
  }
}

//function call 
printAll("a", [10, 20])
// → a
// → 10
// → 20
```

Here is the same example with the "Rest" syntax which is equivalent to the first one, 
with the exception that the array must be the last parameter.

```javascript
// function definition (3 dots added after the array parameter) 
function printAll(param1, otherParams...) {
  console.log(param1);
  for (let element of otherParams) {
    console.log(element);
  }
}

//function call 1 (no need for brackets around the array elements)
printAll("a", 10, 20)
// → a
// → 10
// → 20

//function call 2 (equivalent to call 1)
printAll("a", ...[10, 20])
// → a
// → 10
// → 20
```

If the number of elements of the array is fixed and known at the moment of defining the function,
it is possible to use a more explicit syntax:

```javascript
// function definition 
function printAll(param1, [elementA, elementB]) {
  console.log(param1);
  console.log(elementA);
  console.log(elementB);
}

//function call 
printAll("a", [10, 20])
// → a
// → 10
// → 20
```

### The Math object methods

The Math object is used as a container to group a bunch of related functionality. 
There is only one Math object, and it is almost never useful as a value. 
Rather, it provides a namespace so that all these functions and values do not have to be global bindings

`Math.max` (maximum), `Math.min` (minimum), and `Math.sqrt` (square root).

`Math.cos` (cosine), `Math.sin` (sine), and `Math.tan` (tangent).

`Math.PI` is the number π (pi)—or at least the closest approximation that fits in a JavaScript number.



































