# EJ exrcices

## Chapter 3 - Functions

### Exercice 1 - Minimum

```javascript
function min(a, b) {
  if (a <= b) {
    return a;
  }
  else {
    return b
  }
}

console.log(min(0, 10)); // → 0
console.log(min(0, -10)); // → -10
```

### Exercice 2 - Recursion

```javascript
function isEven(n) {
  if (n == 0) {
    return true;
  }
  else if ( n == 1 || n == -1) {
    return false;
  }
  else if (n > 1) {
    return isEven(n-2);
  }
  else if (n < -1) {
    return isEven(-n);
  }
 
}

console.log(isEven(50)); // → true
console.log(isEven(75)); // → false
console.log(isEven(-1)); // → false
console.log(isEven(-7)); // → false
console.log(isEven(-6)); // → true
```
