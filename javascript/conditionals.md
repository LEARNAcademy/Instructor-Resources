# JavaScript Conditionals

#### Overview
Decision structures, also called decision trees, conditional statements, or if/else statements, are fundamental to computer programming. Conditional statements are a sequence of well-defined instructions that produce a unique output based on the value of the input. Conditionals follow a flowchart-like structure and allow you create logic in your code.

#### Previous Lecture (41 min)
[![YouTube](http://img.youtube.com/vi/yHe4d6qQZC0/0.jpg)](https://www.youtube.com/watch?v=yHe4d6qQZC0)

#### Learning Objectives
- can recall the syntax of an if/else block
- can create a tree of if/else decisions in order to produce a solution to a given problem
- can use console.log to see the appropriate output
- can successfully run a JavaScript file in the terminal

#### Vocabulary
- conditional statement
- if
- else
- string interpolation

#### Additional Resources
- [Conditionals from MDN](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Building_blocks/conditionals)
- [String Interpolation](./template-literals.md)

#### Process
- `cd` into the `javascript-intro-challenges` repository
- Create a new branch: `conditionals-initials1-initials2` (ex. conditionals-aw-sp)
- `touch` a file with no spaces and `.js` extension: `conditionals-student1-student2.js` (ex. conditionals-austin-sarah.js)
- Open the folder in a text editor
- Code!

#### Troubleshooting Tips
- Is the file path is correct?

---

### Javascript Decisions
Programming is the art of solving very complex problems or processes by breaking each problem into tiny, solvable pieces.

In development, **conditionals statements** are commands for handling decisions. Specifically, conditionals perform different actions depending on whether the outcome of a Boolean condition evaluates to true or false.

A conditional statement is defined by the JavaScript keyword **if**. The `if` function takes a statement to be evaluated. If the statement evaluates to the Boolean value of true, the corresponding code statement will be executed.

```
if(this thing is true) {
  console.log(do this)
}
```

A minimum need for a conditional statement is just a single `if` function. However, there is often more decisions that need to be made. Think of the logic behind a simple switch that is either on or off. In code we can create logic that says, `if this thing is true, do this, otherwise, do this other thing.` To create an either-or statement we need to add an **else** statement will act as a catch all.

```
if(this thing is true) {
  console.log(do this)
} else {
  console.log(do this other thing)
}
```

### If/Else Statements
All conditionals must have an `if` statement. If the set condition is true, the program will continue to run. If the condition is not true, nothing will happen.

```javascript
var carOn = true

if(carOn === true) {
  console.log("The engine is running.")
}
```
If we want our code to execute something if the `if` condition is not true, we add an `else` to our program. `Else` is the catch all so we don't give it its own statement. It will automatically run if the `if` condition is not met.

```javascript
var carOn = false

if(carOn === true) {
  console.log("The engine is running.")
} else {
  console.log("The engine is off.")
}
```

If we want more options in our decision structure, we can add an `else if` statement. This runs after the initial `if` and before the catch all `else`. The cool thing about `else if` statements is that you can use as many as you want. Once a condition is met, the program has finished running so the most specific condition should be prioritized.

```javascript
var carOn = true

if(carOn === true) {
  console.log("The engine is running.")
} else if(carOn === false) {
  console.log("The engine is off.")
} else {
  console.log("The car is broken.")
}
```

### String Interpolation
When executing code logic, is it often necessary to return a detailed statement that can involve variables and additional text. Template literals, also known as **string interpolation** allows variables to be embedded into strings. Prior to this neat syntax the only way to use variables inside of strings was to use concatenation.

```javascript
var number1 = 34
var number2 = 78
console.log(number1 + " is less than " + number2)
```

This expression can be modified using string interpolation.

```javascript
var number1 = 34
var number2 = 78
console.log(`${number1} is less than ${number2}`)
```

### Conditional Statement Examples

**Example**: Write a statement that takes two variables and logs the one that has more letters.

```javascript
var fruit1 = "orange"
var fruit2 = "apple"

if(fruit1.length > fruit2.length) {
  console.log(`${fruit1} has more letters`)
} else if(fruit1.length < fruit2.length) {
  console.log(`${fruit2} has more letters`)
} else {
  console.log("They have the same letters")
}
```

**Example**: Write a statement that takes a number from 0 to 100 and logs the number of digits.

```javascript
var number = 9

if(number === 100) {
  console.log(`${number} is a triple digit number`)
} else if(number > 9 && number < 100) {
  console.log(`${number} is a double digit number`)
} else if(number >= 0 && number <= 9){
  console.log(`${number} is a single digit number`)
} else {
  console.log("please enter a number from 0 to 100")
}
```

---

### Challenges
```javascript
// Copy the challenges into your JavaScript file. Comment out the instructions and code the solution to each problem beneath the prompt.

// Make sure you try different options and change the variables to ensure properly working code.

// Write a statement that takes a variable of item and logs "in budget" if a price is $100 or less.
var item = 20
if(item < 100) {
  console.log("in budget")
} else {
  console.log("not in budget")
}
// Output: "in budget"

// Write a statement that takes a variable of hungry and logs "eat food" if you are hungry and "keep coding" if you are not hungry.
var hungry = true
if(hungry === true) {
  console.log("eat food")
} else if(hungry === false) {
  console.log("keep coding")
} else {
  console.log("oops, something went wrong!")
}
// Output: "eat food"

// Write a statement that takes a variable of trafficLight and logs "go" if the light is green, "slow down" if the light is yellow and "stop" if the light is red.
var trafficLight = "green"
if(trafficLight === "green") {
  console.log("go")
} else if(trafficLight === "yellow") {
  console.log("slow down")
} else if(trafficLight === "red") {
  console.log("stop")
} else {
  console.log("oops, something went wrong!")
}
// Output: "go"

// Write a statement that takes two variables that are numbers and outputs the larger number. If the numbers are equal, output "the numbers are the same".
var num1 = 2
var num2 = 7
if(num1 === num2) {
  console.log("the numbers are the same")
} else if(num1 < num2) {
  console.log(num2)
} else if(num1 > num2) {
  console.log(num1)
} else {
  console.log("oops, something went wrong")
}
// Output: 7

// Write a statement that takes a variable of a number and logs whether the number is odd, even, or zero.
var num3 = 2
if(num3 === 0) {
  console.log("zero")
} else if(num3 % 2 === 0) {
  console.log("even")
} else if(num3 % 2 === 1 || num3 % 2 === -1) {
  console.log("odd")
} else {
  console.log("not a number")
}
// Output: "even"

// STRETCH Challenges
// Write a statement that takes a variable of a grade percentage and logs the letter grade for that percentage, if the grade is 100% log "perfect score", if the grade is zero log "no grade available."
var grade = 96
if(grade === 100) {
  console.log("perfect score")
} else if(grade > 89) {
  console.log("A")
} else if(grade > 79) {
  console.log("B")
} else if(grade > 69) {
  console.log("C")
} else if(grade > 59) {
  console.log("D")
} else if(grade <= 59) {
  console.log("F")
} else {
  console.log("oops, something went wrong")
}
// Output: "A"

// Write a statement that takes a variable of a boolean, number, or string data type and logs the data type of the variable. HINT: Check out the JavaScript typeof operator.
var whatType = "I am a string"
if(typeof whatType === "string") {
  console.log("string")
} else if(typeof whatType === "number") {
  console.log("number")
} else if(typeof whatType === "boolean") {
  console.log("boolean")
} else {
  console.log("oops, something went wrong!")
}
// Output: "string"

// Create a password checker using a single conditional statement. If a user inputs a password with 12 or more characters AND the password includes !, then log "That is a mighty strong password!" If the user’s password is 8 or more characters OR includes !, then log "That password is strong enough." Log "That is not a valid password." for every other input.
var password = "mypassword!!!"
if(password.length >= 12 && password.includes("!")) {
  console.log("That is a mighty strong password!")
} else if(password.length >= 8 || password.includes("!")) {
  console.log("That password is strong enough")
} else {
  console.log("That is not a valid password")
}
// Output: "That is a mighty strong password!"
```

---

# Lecture Notes

### Overview
- Conditional statements create logic through evaluations
- Only one outcome per conditional statement

### Goals
- Modeling git workflow
- Instilling good indentation habits

### Major Takeaways
- If, else if, else
- Evaluations that return a Boolean value

### Lecture
- Create a branch
- Create a JavaScript file with a `.js` extension and no spaces in the name
- Run the file with `node`

One of the most powerful thing we can have our program do is perform logic. Within that logic we want our program to be able to take a given input make a decision about that input and give us an appropriate output. Conditionals, decision trees, or just if/else statements are all the same thing. To create conditionals, we have to create evaluations. We have to create a situation where we can determine if the outcome of that evaluation is true or false.

#### Evaluations
These evaluations return Boolean values.

**Equality Operator**
- Strict equality `===` vs loose equality `==`
- Strict equality is the best practice

```javascript
var myFavNum = 7
console.log(myFavNum === 7)

var myName = "Sarah"
console.log("Sarah" === myName)
```

**Relational Operators**
- < > <= >=

**Logical Operators**
- Logical and `&&`
- Logical or `||`

```javascript
var greeting = "hello"
var num = 6

console.log(num > 2 + 2  && "hello" === greeting)

console.log(num > 2 + 2 || num === greeting)
```

**Negation**
- Logical oposite
- Bang operator `!`

#### If/Else
- Create code that will execute an output based on an evaluation
- `if` is a keyword in JavaScript, it is built into the language

```javascript
if
```

- The job of an if statement is to make a decision
- Need to pass an evaluation to the if
- To pass more info, we need parentheses

```javascript
if()
```

- Inside the parentheses we need to pass information that can be evaluated to a Boolean value of true or false
- If this information evaluates to `true` we want a response to occur
- The response is wrapped in curly braces known as a block of code
- What is inside the curly braces is the executable code, the action

```javascript
if(true){
  console.log("I'm true!")
}
```

- If the statement evaluates to false, the block of code does not run

```javascript
if(false){
  console.log("I'm false!")
}
```

Since the statement evaluates to `false` there is no executable action. Which could be fine. There are plenty of situations where either "something" or "nothing" is the desired outcome. That is still two possible outcomes. But we may want more than two possible outcomes. So let's add some code to execute if our "if" is false. If the `if` statement is false we want something to happen. That requires another key word `else`. Else is also a protected word in JavaScript. Unlike "if," "else" does not take an action. It only runs if nothing else is true. It is the catch all.

```javascript
if(false){
  console.log("I'm false!")
} else {
  console.log("here is the else")
}
```

#### Proper Indentation
The most amateur thing you can do while you are learning code is by lazy about your formatting. Having messy indentation will make your code look bad and more importantly, it makes it really hard to find mistakes.

#### Passing Evaluations
Rather than passing a Boolean value directly we can create a statement to be evaluated.

```javascript
var myName = "Sarah"
if(myName === "Sarah"){
  console.log("Hey!")
} else {
  console.log("here is the else")
}
```

- Manipulate the variable a few times
- This is a very small computer program!

#### Else If

```javascript
if(6 < 3){
  console.log("six is less than three")
} else if(6 !== 5){
  console.log("six is not equal to five")
} else {
  console.log("else!")
}
```

JavaScript is read line by line. So our little program is just waiting looking for a condition to be true, or for the else, with no qualifications. As soon as one of the evaluations returns true, the block is executed successfully and JavaScript is done. So set your logic accordingly, and test all outcomes. You could have two true statements but the one that is read first by your program is going to run. The second one will not.

- Play around and change things, add variables

### Review
- What are the three main types of evaluations?
- What data type do the evaluations return?
- Always need an if
- Can have as many else ifs as you want
- Else is a catch all and does not take an evaluation
- Only one outcome will ever be true at a time

---
[Back to Syllabus](../README.md#unit-one-javascript-foundations)
