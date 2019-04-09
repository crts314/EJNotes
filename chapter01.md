# EJNotes

## Chapter 1 - Values, Types, and Operators

### Values 

Anything that can be stored in the memory as bits 

### Numbers

Numbers are values stored in 64 bits.

We can do all classic arithmetic on them.

The `%` symbol is used to represent the remainder operation. For example, `314 % 100` produces `14`.

Operators use precedance rules and parentheses similarily as in math.

Some numbers are special like `infinity` and `-Infinity`.

`NaN` stands for “not a number”, even though it is a value of the number type. 
You’ll get this result when you, for example, try to calculate `0 / 0`.

### Strings

Represent a sequence of characters written between quotes `"like this"`.

Special characters need to be escaped using `\`.

The character `\n` is used add a new line.

Strings can be concatenated. `"con" + "cat" + "e" + "nate"` is evaluated as `"concatenate"`.

Backtick-quoted strings, usually called template literals, can do a few more tricks. 
Apart from being able to span lines, they can also embed other values as in :
```javascript
`half of 100 is ${100 / 2}`

```

### Unary operators, Binary operators ...

Unary operators operate on a unique value. Example: `typeof 77` is evaluated as `"number"`

Binary operators operate on two values. Example: `3 + 6` is evaluated as `9`

### Booleans

They can take only one of the two values `true` and `false`

Comparison can be done with the following binary comparison operators `< > == != === !==`

A comparison expression is always evaluated as a boolean

This is also the case for the logical operators AND and OR which are in javacript `&&` and `||`

### Empty values

There are two special values, written `null` and `undefined`, that are used to denote the absence of a meaningful value.

### Automatic type conversion

When an operator is applied to the “wrong” type of value, JavaScript will quietly convert that value to the type it needs, 
using a set of rules that often aren’t what you want or expect. 
Example: `"5" - 1` is evaluated as 4 because the string is first transformed into a number before the operator `-` is applied.

A robust program should not use Automatic type conversion.

A robust program should use `=== !==` instead of `== !=` because they don't do any type conversion




