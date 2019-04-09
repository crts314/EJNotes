# EJ exrcices

## Chapter 2 - Program Structure

### Exercice 1 - Looping a triangle

```javascript
let abc = "abc";
let line = "";
for (let i = 0 ; i < 7 ; i++) {
  line = line + "#";
  console.log(line);
}
```

### Exercice 2 - FizzBuzz

```javascript
for (let i = 1; i <= 100; i++) {
  if ( i % 3 === 0 && i % 5 === 0 ) {
    console.log("FizzBuzz");   
  }
  else if ( i % 5 === 0 ) {
    console.log("Buzz");
  }
  else if ( i % 3 === 0 ) {
    console.log("Fizz");
  }
  else {
    console.log(i);
  }
}
```

### Exercice 3 - ChessBoard

```javascript
let width = 6
let height = 4

let oddLine = ""
let evenLine = ""

//loop on character index in line
for (let index = 0; index < width; index++) {
  if (index % 2 === 0) {
    oddLine = oddLine + "#";
    evenLine = evenLine + " ";
  }
  else {
    oddLine = oddLine + " ";
    evenLine = evenLine + "#";
  }
}

let paragraph = ""

// loop on line index in paragraph
for (let index = 0; index < height; index++){
  if (index % 2 == 0) {
    paragraph = paragraph + evenLine + "\n"; 
  }
  else {
    paragraph = paragraph + oddLine + "\n";
  }
}

console.log(paragraph);
```

