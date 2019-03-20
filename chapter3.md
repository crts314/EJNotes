# EJNotes

## Chapter 3 - Functions

### Reminder

A function has an input and output. 

The input can be either a parameter  (and/or as we will see later the object to which the function is attached as a property).

The output of a function is either a side effect or a returned value or both.

### Function definition

A function can be defined using the `function` keyword. 

The function definition is a value. 

It can be binded to a name like any other value.

The function definition and binding can be done like this: 

```javascript
const functionName = function(param1, param2) {
  // The statements here form the block that we call the function body.
};
```

### Bindings and scope

Each binding has a scope, which is the part of the program in which the binding is visible. 

For bindings defined outside of any function or block, the scope is the whole program. 
You can refer to such bindings wherever you want. These are called global.

Otherwise, the scope usually starts at the instruction where the binding is declared and dies at the end of its block. 
Such bindings are known as local. 

Bindings created for function parameters or declared inside a function can be referenced only in that function, 
so they are local bindings as well. Every time the function is called, new instances of these bindings are created. 
This provides some isolation between functions

Bindings declared with let and const are in fact local to the block that they are declared in, 
so if you create one of those inside of a loop, the code before and after the loop does not “see” it. 

Each scope can “look out” into the scope around it. 
The exception is when multiple bindings have the same name—in that case, code can see only the innermost one. Example:

```javascript
const halve = function(n) {
  return n / 2;
};

let n = 10;
console.log(halve(100)); // → 50
console.log(n); // → 10
```

JavaScript distinguishes not just global and local bindings. 
Blocks and functions can be created inside other blocks and functions, producing multiple degrees of locality.

### Declaration notation

The same function above could be declared like this:

```javascript
function functionName(param1, param2) {
  // The statements here form the block that we call the function body.
}
```

Functions defined using the declaration notation are not part of the regular top-to-bottom flow of control. 
They are conceptually moved to the top of their scope and can be used by all the code in that scope.

### Arrow notation

Our same function can also be defined like this:

```javascript
const functionName = (param1, param2) => {
  // The statements here form the block that we call the function body.
};
```

Except the syntax there is no difference with the first syntax for defining a function.

When there is only one parameter name, you can omit the parentheses around the parameter list. 
If the body is a single expression, rather than a block in braces, that expression will be returned from the function. 
So, these two definitions of square do the same thing:

```javascript
const square1 = (x) => { return x * x; };
const square2 = x => x * x;
```

### Optional arguments

JavaScript is extremely broad-minded about the number of arguments you pass to a function. 

If you pass too many, the extra ones are ignored. 

If you pass too few, the missing parameters get assigned the value undefined.

```javascript
// function definition
function minus(a, b) {
  if (b === undefined) return -a;
  else return a - b;
}

// function call with fewer parameters (the second gets value undefined)
console.log(minus(10)); // → -10

// function call with extra parameters (the third is ignored)
console.log(minus(10, 5, true)); // → 5
```

### Closure

A function that references bindings from local scopes around it is called a closure. 
Such bindings will remain alive even after the end of the block where they were defined.
Thats how a function "closes on them" and can use their values whenever it is called. Example:

```javascript
function wrapValue(n) {
  let local = n;
  return () => local;
}

let wrap1 = wrapValue(1);
let wrap2 = wrapValue(2);
console.log(wrap1()); // → 1
console.log(wrap2()); // → 2
```

### Recursion

It is perfectly okay for a function to call itself, as long as it doesn’t do it a huge number of times. 
A function that calls itself is called recursive. Example:

```javascript
function power(base, exponent) {
  if (exponent == 0) {
    return 1;
  } else {
    return base * power(base, exponent - 1);
  }
}

console.log(power(2, 3)); // → 8
```



