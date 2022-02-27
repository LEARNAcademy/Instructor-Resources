# JavaScript Classes

- [Challenges](#challenges)
- [Lecture Notes](#lecture-notes)

## Video: Video Name
[![YouTube](http://img.youtube.com/vi/LudiZKHYvMo/0.jpg)](https://www.youtube.com/watch?v=LudiZKHYvMo)

## Overview
- Classes are the blueprint for objects
- Classes are reusable and customizable, much like functions

## Learning Objectives
- Understanding the anatomy of a class
- Creating a object with unique data from a class
- Understanding the purpose of a constructor
- Understanding the difference between an object and a class

## Vocabulary
- class
- object
- constructor
- this
- new
- PascalCase

## Additional Resources
- <a href="http://www.javascriptenlightenment.com/" target="blank">Javascript Enlightenment</a>
- <a href="https://github.com/getify/You-Dont-Know-JS/blob/master/up%20&%20going/ch2.md#objects" target="blank">You Don't Know JS: Up & Going - Chapter 2: Into JavaScript</a>
- <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript#Objects" target="blank">MDN: Objects</a>
- <a href="https://github.com/getify/You-Dont-Know-JS/blob/master/scope%20&%20closures/ch3.md#chapter-3-function-vs-block-scope" target="blank">You Don't Know JS: Function vs. Block Scope</a>
- <a href="https://github.com/getify/You-Dont-Know-JS/blob/master/scope%20&%20closures/ch5.md#chapter-5-scope-closure" target="blank">You Don't Know JS: Scope Closure</a>
(Caution: not for the faint of heart)
- <a href="https://github.com/airbnb/javascript" target="blank">Airbnb JavaScript Style Guidelines</a>

#### Process
- `cd` into the `javascript-foundations-challenges` repository
- Create a new branch: `classes-initials1-initials2` (ex. classes-aw-sp)
- `touch` a file with no spaces and `.js` extension: `classes-student1-student2.js` (ex. classes-austin-sarah.js)
- Open the folder in a text editor
- Code!

---

## Classes
Classes are a particular type of function that contain data and behavior. Classes are the blueprints of objects. Just like functions, classes have their own scope.

There are particular JavaScript keywords that are used to create and access information within a class:
- **constructor:** a special method for creating and initializing objects
- **this:** a JavaScript keyword that refers to the object it belongs to
- **new:** used when creating a new instance of a class (an object)

Class syntax conventions:

- Class names are always capitalized
- Class names are PascalCased (like camelCase, but the first word is capitalized)
- Instance of classes (objects) are always lowercase

```javascript
class Squirrel{
  constructor(){
    this.nutCount = 0
  }

  storeNut(){
    this.nutCount += 1
  }

  eatNut(){
    this.nutCount -= 1
  }
}
// creating the instance of the class, saved as a variable
// rocky now has access to the class methods
var rocky = new Squirrel()

console.log(rocky.nutCount)
--> 0

rocky.storeNut()
console.log(rocky.nutCount)
--> 1

rocky.storeNut()
console.log(rocky.nutCount)
--> 2

rocky.eatNut()
console.log(rocky.nutCount)
--> 1
```

Just like functions, classes are reusable. Each object created from the class is independent from each other.

```javascript
class Squirrel{
  constructor(){
    this.nutCount = 0
  }

  storeNut(){
    this.nutCount += 1
  }

  eatNut(){
    this.nutCount -= 1
  }
}

var rocky = new Squirrel()
var alvin = new Squirrel()

alvin.storeNut()
alvin.storeNut()

console.log("Rocky has ", rocky.nutCount )
--> "Rocky has 0"

console.log("Alvin has ", alvin.nutCount )
--> "Alvin has 2"
```

Class instances can be used like any other 'thing' in JavaScript. We can rewrite the above like this:

```javascript
class Squirrel{
  constructor(){
    this.nutCount = 0
  }

  storeNut(){
    this.nutCount += 1
  }

  eatNut(){
    this.nutCount -= 1
  }
}
// create a new array
var squirrels = []
// pushes new squirrel objects into the array
squirrels.push(new Squirrel())
squirrels.push(new Squirrel())

// accessing the object at array index 0
squirrels[0].storeNut()
squirrels[0].storeNut()

// mapping over array to access the information from the squirrels array
squirrels.map((value, index) => {
  console.log(`The squirrel at index ${index} has ${value.nutCount} nuts.`)
})
```

Class instances can store any kind of data.

```javascript
class DiceRoller{
  constructor(){
    this.rolls = []
  }

  roll(){
    // generating a random number between 1 and 6 and pushing to the this.rolls array
    this.rolls.push(Math.ceil(Math.random() * 6))
  }

  lastRoll(){
    //logging the last roll added to the array
    return this.rolls[this.rolls.length - 1]
  }
}

var roller = new DiceRoller()
console.log("Roll:", roller.lastRoll())
--> Roll: undefined

roller.roll()
console.log("Roll:", roller.lastRoll())
--> Roll: 6

roller.roll()
console.log("Roll:", roller.lastRoll())
--> Roll: 4

console.log("All Rolls:", roller.rolls)
--> All Rolls: [ 6, 4 ]
```
The constructor method can take arguments. This creates objects with unique data.

```javascript
class Dog{
  constructor(name, age){
    this.name = name
    this.age = age
  }

  description(){
    return `${this.name} is a ${this.age} year old dog.`
  }
}
// now when creating the new object, the constructor method is expecting two arguments: a name and an age
var rover = new Dog('Rover', 4)
console.log(rover.description())
--> "Rover is a 4 year old dog."
```
We can use the Dog class to create many different dog objects with different properties.

```javascript
var plato = new Dog('Plato', 8)
var bella = new Dog('Bella', 11)

console.log(plato.description())
--> "Plato is a 8 year old dog."

console.log(bella.description())
--> "Bella is a 11 year old dog."
```

Objects are still just variables that reference a class. Variables in JavaScript can be reassigned.

```javascript
var plato = new Dog('Plato', 8)
var bella = new Dog('Bella', 11)

console.log(plato.description())
--> "Plato is a 8 year old dog."

console.log(bella.description())
--> "Bella is a 11 year old dog."
bella = plato
console.log(bella.description())
--> "Plato is a 8 year old dog."
// !!!! bella got reassigned
```

## Challenges
``` javascript
// Coffee Maker
class Coffee {
  constructor(type, cream, sugar){
    this.type = type.toLowerCase()
    this.cream = cream
    this.sugar = sugar
  }

  coffeeProfile(){
    return `A ${this.type} coffee with ${this.creams()}, ${this.sugars()}`
  }

  creams(){
    if(this.cream > 1){
      return `${this.cream} creams`
    } else {
      return `${this.cream} cream`
    }
  }

  sugars(){
    if(this.sugar > 1){
      return `${this.sugar} sugars`
    } else {
      return `${this.sugar} sugar`
    }
  }
}

// Write the code that makes a black coffee. Then write the code that outputs the coffee's profile.
var blackCoffee = new Coffee("black", 0, 0)
console.log(blackCoffee.coffeeProfile())
// Output: "A black coffee with 0 cream, 0 sugar"

// Write the code that makes a coffee with 1 cream and 2 sugars. Then write the code that outputs the coffee's profile.
var blondeCoffee = new Coffee("blonde", 1, 2)
console.log(blondeCoffee.coffeeProfile())
// Output: A blonde coffee with 1 cream, 2 sugars

// Latte Maker
// Write a Latte class that takes a flavor, a milk type and a number of shots.
// Write a method for your Latte class that outputs the latte's profile.
class Latte {
  constructor(flavor, milkType, shots) {
    this.flavor = flavor
    this.milkType = milkType
    this.shots = shots
  }

  latteProfile() {
    return `A ${this.flavor} latte with ${this.milkType} milk and ${this.shots} shot(s) of espresso`
  }
}

// Write the code that makes a regular, single shot latte. Then, log the latte's profile.
var regularLatte = new Latte("regular", "regular", 1)
console.log(regularLatte.latteProfile())
// Output: "A regular latte with regular milk and 1 shot(s) of espresso"

// Write the code that makes a double shot hazelnut latte with almond milk. Then, log the latte's profile.
var doubleHazelnut = new Latte("hazelnut", "almond", 2)
console.log(doubleHazelnut.latteProfile())
// Output: "A hazelnut latte with almond milk and 2 shot(s) of espresso"

// Volume of a Cylinder
// Write a class that calculates the volume of a Cylinder to four decimal places. Volume of a cylinder : V = πr2h (r is the radius and h is the height of the cylinder)

class Cylinder {
  constructor(radius, height) {
    this.radius = radius
    this.height = height
  }
  findVolume() {
    return (this.radius * this.height * Math.PI).toFixed(4)
  }
}

// Write the code that creates three unique cylinder objects
var canCylinder = new Cylinder(1.5, 3.5)
console.log(canCylinder.findVolume())
// Output: 16.4934
var bucketCylinder = new Cylinder(5, 10)
console.log(bucketCylinder.findVolume())
// Output: 157.0796
var cupCylinder = new Cylinder(2, 6)
console.log(cupCylinder.findVolume())
// Output: 37.6991
```

---

# Lecture Notes

### Overview
- Establish the difference between classes and objects
- Discuss the differences between hard-coded and dynamic values
- Classes and objects are the intersection of data and behavior
- Classes need to be instantiated just like functions need to be invoked

### Process
- Ensure you are in the cohort-lecture-examples repo
- Ensure your local is up to date and there are no stale branches
- Create a new branch
- Create a JavaScript file with the naming convention `language-topic.js`
- Run the file with `node`

### Additional Notes and Goals
- Using the verbage of "instantiate a class" and that an object is an "instance of a class"

### Major Takeaways
- Objects are hard-coded while classes are dynamic
- PascalCase is the naming conventions for classes in many languages, not just JavaScript
- `constructor()` is a JavaScript method specifically for defining variables that belong to a class
- `new` is a keyword in JavaScript that instantiates a class (creates an object)

### Lecture
Objects are a way to store collections of data and methods. Objects are a really common data structure in all of development. The problem with how we created objects is that all the values are hard-coded.
- Hard-coded values vs dynamic values

We need a way to be able to make objects reusable. To make objects dynamic. So enter classes.

#### Class Anatomy
- Class declaration - just like functions and variables, classes have a declaration using the word `class` which is a protected word in JavaScript
- Class name - naming syntax for classes uses a casing convention called PascalCase
- Curly braces to define the scope of the class

```javascript
class DoingMath {
}
```

#### Static Data
Just like an object, a class can have both static information or data in the form of JavaScript data types and methods or behavior. So let's start with the data.
- Need to establish variables that belong to the class
- The `constructor()` method is a built in JavaScript method that is used to instantiate class variables, it "constructs" the values for the class


```javascript
class DoingMath {
  constructor() {

  }
}
```

- Creating variables that belong to the class requires the keyword `this`

```javascript
class DoingMath {
  constructor() {
    this.num1 = 5,
    this.num2 = 10,
    this.num3 = 15
  }
}
```

#### Methods
Now we can add a method to add up the variables that hold the numbers.
```javascript
class DoingMath {
  constructor() {
    this.num1 = 5,
    this.num2 = 10,
    this.num3 = 15
  }
  addUp() {
    return this.num1 + this.num2 + this.num3
  }
}
```

#### Instantiating a Class
AKA creating an object. Just like a function, the class is not doing anything at all right now. It is just describing the idea of variables that contain numbers and a method that adds up those numbers. To make the class useful it must be instantiate, meaning that we need to use the class to create an object.
- JavaScript keyword `new` instantiates a class, another way of saying this is it creates an object from the template of the class

```javascript
console.log(new DoingMath)
```

- The log will display an object with key:values pairs
- This can be saved into a variable

```javascript
const math = new DoingMath
console.log(math)
```

#### Accessing Data and Methods
Now that we have a variable containing an object we can use dot notation and access the data and the methods.

```javascript
console.log(math.num1)
console.log(math.addUp())
```

#### Making Multiple Classes
This same class can be instantiated as many times as we want, creating as many objects as we want.

```javascript
const math1 = new DoingMath
console.log(math1)

const math2 = new DoingMath
console.log(math2)
```

#### Making the Class Dynamic
We talked about the power of having dynamic values vs hard-coded values. Right now every object we make is exactly identical. To created dynamic values for the numbers we can remove the hard-coded values and have our constructor take these values as parameters.
- The keyword `new` calls the constructor method
- If the constructor method has parameters, that means we need to pass it arguments of actual data
- Now every object can have different values for the number variables

```javascript
class DoingMath {
  constructor(num1, num2, num3) {
    this.num1 = num1,
    this.num2 = num2,
    this.num3 = num3
  }
  addUp() {
    return this.num1 + this.num2 + this.num3
  }
}

const math1 = new DoingMath(5, 10, 15)
console.log(math1)
console.log(math1.addUp())

const math2 = new DoingMath(3, 7, 2)
console.log(math2)
console.log(math2.addUp())
```

#### Mix and Match
Sometimes you will want a mix of hard-coded data and dynamic data.
- Parameters just have to match the name that is assigned to the variable
- It is convention for the class variable names and the parameters to be the same

```javascript
class DoingMath {
  constructor(num2, num3) {
    this.num1 = 5
    this.num2 = num2,
    this.num3 = num3
  }
  addUp() {
    return this.num1 + this.num2 + this.num3
  }
}

const math = new DoingMath(5, 10)
console.log(math.addUp())
```

#### Adding Another Method
Can add as many methods as needed.
- Create a method that returns the largest number.
- Google "javascript method largest number" (or equivalent) and use MDN Math.max documentation to model the logic in the method

```javascript
class DoingMath {
  constructor(num2, num3) {
    this.num1 = 5
    this.num2 = num2,
    this.num3 = num3
  }
  addUp() {
    return this.num1 + this.num2 + this.num3
  }
  largestNum() {
    return Math.max(this.num1, this.num2, this.num3)
  }
}

const math1 = new DoingMath(5, 10)
console.log(math1.largestNum())

const math2 = new DoingMath(2, 3)
console.log(math2.largestNum())
```

### Review
- What is a class?
- What is the naming convention for a class?
- What is the difference between hard-coded and dynamic values?
- What does the keyword `new` do?
- What is the constructor?
- What is the difference between an object and a class?
- What is the difference between a function and a method?
- What does it mean to instantiate a class?
- What is an instance of a class?

### Next Steps
- Open the syllabus section and briefly run through the challenges and expectations
- Remind the student to use the `javascript-foundations-challenges` repo
- Remind the students of the appropriate naming conventions for their branch and file
- Post pairs in Slack
- Open breakout rooms with ability for participants to choose their room

---
[Back to Syllabus](../README.md#unit-one-javascript-foundations)
