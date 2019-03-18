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

### Arrray Manipulation

`push` and `unshift` are methods of every array. 
they add a new element respectively in the back and in the front of the array they belong to.

`pop` and `shift` are also methods of every array. 
they remove and return the element respectively in the back and in the front of the array they belong to.

```javascript
let sequence = [1, 2, 3];
sequence.push(4);
sequence.push(5);
console.log(sequence); // → [1, 2, 3, 4, 5]
console.log(sequence.pop()); // → 5
console.log(sequence); // → [1, 2, 3, 4]
console.log(sequence.shift()); // → 1
console.log(sequence); // → [2, 3, 4]
console.log(sequence.unshift()
```

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

It is possible to assign a value to a property expression with the = operator. This will replace the property’s value if it already existed or create a new property on the object if it didn’t.

`delete` is a unary operator that, when applied to an object property, removes the named property from the object.

`in` is a binary operator that, when applied to a string and an object, produces true if and only if the object has a property named as the string.

`Object.keys` is a function with a single parameter. when called returns an array of the properties of the given parameter.

```javascript
console.log(Object.keys({x: 0, y: 0, z: 2})); // → ["x", "y", "z"]
```

#### Immutability

The types of values discussed in earlier chapters, such as numbers, strings, and Booleans, are all immutable—it is impossible to change values of those types.

Objects work differently. You can change their properties, causing a single object value to have different content at different times.

Therefore is a difference between having two references to the same object and having two different objects that contain the same properties at a given time. Because object can change, two objects are equal only if they conrrespond to the same bits in memory

```javascript
let object1 = {value: 10};
let object2 = object1;
let object3 = {value: 10};

console.log(object1 == object2);
// → true
console.log(object1 == object3);
// → false
```
