# EJNotes

## Chapter 6 - The secret life of objects

### This

When defining a method, in order to access the object on which a method is called, we use a "special parameter" named `this`.

### Prototypes and Classes

Often a set of objects share a common behavior. This behavior can be described with a set of common methods. 

Instead of declaring those methods for everyone of those similar objects, 
javascript allows grouping those method in a single object known as "the prototype".

When a method is called on an object and if the object doesn't have such method, 
JavaScript falls back to its prototype to find such method.

JavaScript has the notion of class, which is an easy way to define the prototype and attach it to the corresponding objects.

In `class` we define all the methods that are common to the objects of this class.

In `class` we also define the `constructor` method which intializes the properties that are specific to each object.

To define a new object of a class, we use `new` keyword followed by a function with the same name of the class, 
to which we provide the same parameters as the `constructor` method.

Consider this example of many rabbits sharing the same `speak` behavior. 
In this example the speak method is added to every object.

```javascript
function speak(line) {
  console.log(`The ${this.name} rabbit says '${line}'`);
}

let happyRabbit = {name: "happy", speak};
let sadRabbit = {name: "sad", speak};

happyRabbit.speak("yaaay !!!") // → The happy rabbit says 'yaaay !!!' 
sadRabbit.speak("buuu ...") // → The sad rabbit says 'buuu ...' 
```

An alternative is to use a `class Rabbit`.

```javascript
class Rabbit {
  constructor(n) {
    this.name = n;
  }
  speak(line) {
    console.log(`The ${this.name} rabbit says '${line}'`);
  }
}

let happyRabbit = new Rabbit("happy");
let sadRabbit = new Rabbit("sad");

happyRabbit.speak("yaaay !!!") // → The happy rabbit says 'yaaay !!!' 
sadRabbit.speak("buuu ...") // → The sad rabbit says 'buuu ...' 
```

We get the prototype of an object using the method `Object.getPrototypeOf` which takes as a parameter the concerned object.
For example, after defining the class `Rabbit` and creating an instance of it, `happyRabbit` we have

```javascript
console.log(Object.getPrototypeOf(happyRabbit) == Rabbit.prototype); // → true
```

We have seen before that binary operator `in` allows to check if an a object has a given property. 
This also works for the properties coming from its prototype.

```javascript
console.log("name" in happyRabbit); // → true
console.log("speak" in happyRabbit); // → true
```

However to check if a property is specifique to the object we use the method `hasOwnProperty`

```javascript
console.log(happyRabbit.hasOwnProperty("name")); // → true
console.log(happyRabbit.hasOwnProperty("speak")); // → false
```

We have seen before that the method `Object.keys` allows to list all the property names of an object as an array. 
This array will not include the properties coming from its prototype.

```javascript
console.log(Object.keys(happyRabbit)); // → ["name"]
```
