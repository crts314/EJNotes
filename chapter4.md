# EJNotes

## Chapter 4 - Data Structures: Objects and Arrays

### Arrays

JavaScript provides a data type specifically for storing sequences of values. 
It is called an array and is written as a list of values between square brackets, separated by commas.

The i'th element of an array `a` (element at index i) is accessed like this `a[i]`

Indexing in JavaScript starts from `0`

### Properties

Values and objects (including arrays) have properties. inversly a property belongs to an object or a value.

To access a property named `prop` we use the syntax `.prop` after the value or the object with such property.

Almost all JavaScript values have properties. The exceptions are `null` and `undefined`.

A property can hold a value or an object like any regular binding.

### Methods

Properties that contain functions are generally called methods of the value they belong to. 
For example `toUpperCase` is a method of every string.

```javascript
let sentence = "my way";
console.log(typeof sentence.toUpperCase); // → function
console.log(sentence.toUpperCase()); // → MY WAY
```
