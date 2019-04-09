# EJ exercices 

## Chapter 6 - The Secret Life of Objects

### Exercice 1 - A vector type

```javascript
class Vec {
  constructor(x, y) {
    this.x = x;
    this.y = y;
    this._needToOptimize = false;
  }
  minus(otherVec) {
    return new Vec ((this.x - otherVec.x), (this.y - otherVec.y));
  }
  plus(otherVec) {
    return new Vec ((this.x + otherVec.x), (this.y + otherVec.y));
  }
}

//let Vec1 = new Vec(1, 2);
//let Vec2 = new Vec(2, 3);

//console.log(Vec1);
//console.log(Vec2);


console.log(new Vec(1, 2).plus(new Vec(2, 3))); // → Vec{x: 3, y: 5}
console.log(new Vec(1, 2).minus(new Vec(2, 3))); // → Vec{x: -1, y: -1}
//console.log(new Vec(3, 4).length); // → 5
```
### Exercice 2 - Groups

```javascript
class Group {
  constructor() {
    this.a = [];
  }
  
  add(element) {
    if (this.a.indexOf(element) === -1) {
      this.a.push(element);
    }
    console.log(this.a);
  }
  
  has(element) {
    if (this.a.indexOf(element) === -1) {
      return false;
    }
    else {
      return true;
    }
  }
  
  delete(element) {
    let index = this.a.indexOf(element);
    if (index !== -1) {
      this.a = this.a.slice(0, index).concat(this.a.slice(index + 1));
    }
    console.log(this.a);
  }
}

let group = new Group();

group.add(0);
group.add(10);
group.add(20);

console.log(group.has(10)); // → true
console.log(group.has(30)); // → false
group.add(10);
group.delete(10);
console.log(group.has(10)); // → false
```
### Exercice 3 - Iterable groups

```javascript
class Group {
  constructor() {
    this.a = [];
  }
  
  add(element) {
    if (this.a.indexOf(element) === -1) {
      this.a.push(element);
    }
  }
  
  has(element) {
    if (this.a.indexOf(element) === -1) {
      return false;
    }
    else {
      return true;
    }
  }
  
  delete(element) {
    let index = this.a.indexOf(element);
    if (index !== -1) {
      this.a = this.a.slice(0, index).concat(this.a.slice(index + 1));
    }
  }
  
  [Symbol.iterator]() {
    //return new GroupIterator(this);
    return new GroupIterator2(this);
  }
}

class GroupIterator {
  constructor(group) {
    this.index = 0;
    this.group = group;
  }
  next () {
    
    if (this.index == this.group.a.length) return {done: true};
    
    let value = this.group.a[this.index];
    
    this.index++;
    return {value , done: false};
 }    
}


class GroupIterator2 {
  constructor(group) {
    this.aIterator = group.a[Symbol.iterator]();
    this.group = group;
  }
  next () {
    return this.aIterator.next();    
 }    
}
  
let group = new Group();
 
group.add("a");
group.add("b");
group.add("c");

console.log(group.a);

for (let value of group) {
  console.log(value);
}

// → a
// → b
// → c
```

### Exercice 3.1 - Iterable huskies

```javascript
class Husky {
  constructor(name, age, color) {
    this.name = name;
    this.age = age;
    this.color = color;
    this.puppies = new Map();
  }
    
  speak() {
    console.log(`Bow wow! My name is ${this.name}. I'm ${this.color}` + 
      	` ${this.age} years old husky`);
  }
  
  add(name, age) {
    this.puppies.set(name, age);    
  }
  
  speak2(){
    console.log(`${this.name} says: I have ${this.puppies.size} puppies`);
  }
  
  [Symbol.iterator]() {    
    return new HuskyIterator(this);
  }
  
  getChildAge(name) {
    return this.puppies.get(name);
  }
  
}

class HuskyIterator {
  constructor(husky) {
    this.puppiesIterator = husky.puppies[Symbol.iterator]();
    this.husky = husky;
  }
  next () {
    
    let result = this.puppiesIterator.next();
    
    let value = undefined;
    
    if (!result.done) {
      value = result.value[0];
    }
    
    return {
             value: value ,
      	     done:result.done
           }
 }    
}

let max = new Husky ("max", 5, "black");
max.speak(); //Bow wow! My name is max. I'm black 5 years old husky
  
let bella = new Husky ("bella", 4, "white");
bella.speak(); //Bow wow! My name is bella. I'm white 4 years old husky

max.add("Lulu", 1);
max.add("Miko", 2);

bella.add("Maya", 1);
bella.add("Tony", 3);
bella.add("Shiva", 2);

max.speak2(); //max says: I have 2 puppies
bella.speak2(); //bella says: I have 3 puppies


//iterating on the husky 
for (let value of max) {
  console.log(value);
}
//Lulu Miko

console.log(max.getChildAge("Miko")) // 2
console.log(max.getChildAge("Lulu")) // 1
```
