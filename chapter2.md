# EJNotes

## Chapter 1

### Expressions and statements

If an expression corresponds to a sentence fragment, a JavaScript statement corresponds to a full sentence

Statements end with `;`

### Bindings

To catch and hold values, JavaScript provides a thing called a binding, or variable. Example:

```javascript
let caught = 5 * 5;
```

After a binding has been defined, its name can be used as an expression. 
The value of such an expression is the value the binding currently holds

```javascript
let ten = 10;
console.log(ten * ten);
// → 100
```

When you define a binding without giving it a value, and ask for its value you'll get the value `undefined`.

`const` defines a constant binding, which points at the same value for as long as it lives. Example:

```javascript
const greeting = "Hello ";
```

Binding names can be any word. Digits can be part of binding names—catch22 is a valid name, for example, 
but the name must not start with a digit. A binding name may include dollar signs ($) or underscores (_) but 
no other punctuation or special characters. a biding can not be a javacript keyword.

The collection of bindings and their values that exist at a given time is called the environment. When a program starts up, 
this environment is not empty. It always contains bindings that are part of the language standard.

### Functions and function Calls

A function has an input and output. 

The input can be either a parameter  (and/or as we will see later the object to which the function is attached as a property).

The output of a function is either a side effect or a returned value or both.

A function that has a return value can be used like this

```javascript
let result = computeSomething(param1, param2, param3);
```

A function that has only a side effect can be used like this

```javascript
doSomething(param1, param2, param3);
```


