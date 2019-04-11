# EJNotes

## Chapter 7 - Project: A Robot

### Measuring a robot

```javascript
function average(array) {
  let sum = array.reduce((current, element) => current + element);
  return sum / array.length;
}

function runAndComputeRobotTurns(state, robot, memory) {
  for (let turn = 0;; turn++) {
    if (state.parcels.length == 0) {
      //console.log(`Done in ${turn} turns`);
      return turn;
    }
    let action = robot(state, memory);
    state = state.move(action.direction);
    memory = action.memory;
  }
}

function compareRobots(robot1, memory1, robot2, memory2) {
  let array1 = [];
  let array2 = [];
  
  for (let counter = 0; counter < 20000; counter++) {
    let state = VillageState.random();
    let nbTurns1 = runAndComputeRobotTurns(state, robot1, memory1);
    let nbTurns2 = runAndComputeRobotTurns(state, robot2, memory2);
    array1.push(nbTurns1);
    array2.push(nbTurns2);   
  }
  
  console.log(average(array1));
  console.log(average(array2));
}

compareRobots(routeRobot, [], goalOrientedRobot, []);
```

### Robot efficiency

```javascript

function enhancedGoalOrientedRobot({place, parcels}, route) {
  if (route.length == 0) {
    minHops = 10000;
    bestIndex = -1;
    
    for (let index = 0 ; index < parcels.length; index++) {
      let parcel = parcels[index];
      
      if (parcel.place != place) {
        route = findRoute(roadGraph, place, parcel.place);
      } else {
        route = findRoute(roadGraph, place, parcel.address);
      }
      
      if (route.length < minHops) {
      	minHops = route.length;
        bestIndex = index;
      }
    }
    
    let parcel = parcels[bestIndex];
      
    if (parcel.place != place) {
      route = findRoute(roadGraph, place, parcel.place);
    } else {
      route = findRoute(roadGraph, place, parcel.address);
    }
    
  }
  return {direction: route[0], memory: route.slice(1)};
}


function enhancedGoalOrientedRobot2({place, parcels}, route) {
  if (route.length == 0) {
    minHops = 10000;
    bestIndex = -1;
    
    for (let index = 0 ; index < parcels.length; index++) {
      let parcel = parcels[index];
      
      if (parcel.place != place) {
        // route for picking
        route = findRoute(roadGraph, place, parcel.place);
        if (route.length <= minHops) {
          minHops = route.length;
          bestIndex = index;
        }
      } else {
        // route for delivering
        route = findRoute(roadGraph, place, parcel.address);
        if (route.length < minHops) {
          minHops = route.length;
          bestIndex = index;
        }
      }
      
    }
    
    let parcel = parcels[bestIndex];
      
    if (parcel.place != place) {
      route = findRoute(roadGraph, place, parcel.place);
    } else {
      route = findRoute(roadGraph, place, parcel.address);
    }
    
  }
  return {direction: route[0], memory: route.slice(1)};
}


// prefers picking even with more hops
function enhancedGoalOrientedRobot3({place, parcels}, route) {
  if (route.length == 0) {
    minHops = 10000;
    bestIndex = -1;
    picking = false;
    
    for (let index = 0 ; index < parcels.length; index++) {
      let parcel = parcels[index];
      
      if (parcel.place != place) {
        // route for picking
        route = findRoute(roadGraph, place, parcel.place);
        if (route.length <= minHops) {
          minHops = route.length;
          bestIndex = index;
          picking = true;
        }      
      }
    }
    
    if (!picking) {
      for (let index = 0 ; index < parcels.length; index++) {
        let parcel = parcels[index];

        if (parcel.place == place) {
          // route for delivering
          route = findRoute(roadGraph, place, parcel.address);
          if (route.length < minHops) {
            minHops = route.length;
            bestIndex = index;
          }
        }
      }
    }
    
    let parcel = parcels[bestIndex];
      
    if (parcel.place != place) {
      route = findRoute(roadGraph, place, parcel.place);
    } else {
      route = findRoute(roadGraph, place, parcel.address);
    }
    
  }
  return {direction: route[0], memory: route.slice(1)};
}

compareRobots(enhancedGoalOrientedRobot3, [], enhancedGoalOrientedRobot2, []);

//runRobotAnimation(VillageState.random(), enhancedGoalOrientedRobot3, []);
```

### Persistent group

```javascript
"use strict";

class PGroup {
  constructor(array = []) {
    this.a = array;
  }
  
  add(element) {
    if (this.a.indexOf(element) === -1) {   
      let newA = this.a.concat([element]);
      return new PGroup(newA);
    }
    else {
      return this;
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
      let newA = this.a.slice(0, index).concat(this.a.slice(index + 1));
      return new PGroup(newA);
    }
    else {
      return this;
    }
  }
}

function ccc() {
    
    this.a = 3;
}

let g = ccc();

console.log(g)
console.log("yo", a);

/*
PGroup.empty = new PGroup([]);

let a = PGroup.empty.add("a");
console.log(a)
let ab = a.add("b");
console.log(ab)
let b = ab.delete("a");
console.log(b)

console.log(b.has("b"));
// → true
console.log(a.has("b"));
// → false
console.log(b.has("a"));
// → false
*/
```
