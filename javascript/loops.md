# JavaScript Loops

- [Challenges](#challenges)
- [Lecture Notes](#lecture-notes)

#### Overview
Iteration is a very important concept in computer programming. Iteration is the process of executing a block of code over and over again until a condition is met. There are particular data types that are conducive to iterations; particularly data types with length properties such as strings and arrays. For loops are an example of iteration. For loops must define a starting location, a condition to be met that will end the loop, and what executable action will take place during the iteration.

#### Previous Lecture (27 min)
[![YouTube](http://img.youtube.com/vi/VIZpFSwnO_s/0.jpg)](https://www.youtube.com/watch?v=VIZpFSwnO_s)

#### Learning Objectives
- can define the conditions of a for loop
- can define the difference between index and value
- can explain the concept of iteration
- can create a basic for loop that returns an expected output
- demonstrates proper use of const, let, and var when creating variables based on an understanding of global and local scope
- can create a for loop that iterates upon an array to return an expected outcome

#### Vocabulary
- iteration
- for loop
- let
- i (index)
- value
- scope
- local scope
- global scope

#### Additional Resources
- [ W3Schools For Loop ](https://www.w3schools.com/js/js_loop_for.asp)
- [ W3Schools While Loops ](https://www.w3schools.com/js/js_loop_while.asp)

#### Process
- `cd` into the `javascript-intro-challenges` repository
- Create a new branch: `loops-initials1-initials2` (ex. loops-aw-sp)
- `touch` a file with no spaces and `.js` extension: `loops-student1-student2.js` (ex. loops-austin-sarah.js)
- Open the folder in a text editor
- Code!

#### Troubleshooting Tips
- `control + c` will stop an infinite loop

---

### Iteration
In development, **iteration** is the process of performing a particular action a certain number of times or until a condition is met. A common form of iteration is called a for loop. A **for loop** defines a variable and increments or decrements the variable on each iteration.

Many computer programs and programming languages use iterations to perform specific tasks, solve problems, and present solutions.  The for statement creates a loop that is executed as long as a condition is true. The loop will continue to run as long as the condition is true. It will only stop when the condition becomes false.

### For Loop
JavaScript has many types of loops. For now, we are going to focus on breaking down the `for loop`.

This is the most common type of loop you will see used in JavaScript. It gives you the most control over how you are iterating over items by letting you define:

1. Where the count (index) starts
2. How many iterations we want the loop to go through
3. What to do after each loop

Can you guess what this loop will do?

```javascript
for(let i=0; i<5; i++){
  console.log(i)
}
```

How about this loop?

```javascript
for(let i=10; i>0; i--){
    console.log(i)
}
```

For loops are especially helpful when we want to iterate through an array and **do something to each element**.

```javascript
//loop through and array of numbers and return each number multiplied by 3.

var arr = [5, 3, 2, 9, 8]

for(let i=0; i<arr.length; i++){
  console.log(arr[i] * 3)
}
```

So, what's going on in the above example?  During each loop the array[i] is being replaced with..

arr[0] which becomes 5 * 3

arr[1] which becomes 3 * 3

arr[2] which becomes 2 * 3

etc.

We can also 'filter' an array based on certain conditions (if / else statements)

```javascript
//write a for loop that logs all numbers except 5
//expected output [3, 2, 7]

var arr = [5, 3, 5, 2, 5, 7]

for(let i=0; i<arr.length; i++){
  if(arr[i] !== 5){
    console.log(arr[i])
  }      
}
```

Notice the indentation in the above example. This helps us to see if we have closed all of our open curly brackets.  We can see that the first closing curly closes our if/else statement, and the last closing curly closes our for loop.


## Scope - var/let/const

**Scope** refers to where a variable is accessible or visible. The two main types of scope are:

- **Global** - variables that can be seen and used anywhere in the program.

- **Local** - also know as lexical or block scope. Variables in local scope can only be used within the block/function/loop that it is assigned.

Notice that in our loops we use `let` to assign `i` or `index` to a starting value. In the most recent updates to JavaScript (ES6) `let` and `const` were added to deal with scoping issues.  Prior to this, `var` was the only way to assign variables which were always global and sometimes caused problems. Now we have:

- **var** - puts the variable in global scope and may or may not be reassigned.  

- **let** - this means that the variable will only be used in the block in which it is defined. This also means that this variable could be reassigned elsewhere in your program.

- **const** - this means that the variable will not be reassigned.

![scope](./assets/scope.jpg)

---

### Challenges

```javascript
// 1. Logging values with for loops
// - Write a for loop that logs each number from 1 - 20.
for(let i = 1; i <= 20; i++) {
  console.log(i)
}
// Output: 1, 2, 3, 4, ...20


// - Write a for loop that logs the result of each number from 1 - 20 tripled.
for(let i = 0; i <= 20; i++) {
  console.log(i * 3)   
}
// Output: 3, 6, 9, 12, ...60

// - Create a for loop that logs each even number from 1-20, and in the place of every odd number, returns the word "ODD" **Expected output** --> ODD, 2, ODD, 4, ODD, 6 ...etc
for(let i = 1; i <= 20; i++) {
  if(i % 2 !== 0) {
    console.log("ODD")
  } else {
    console.log(i)
  }
}
// Output: ODD, 2, ODD, 4, ODD, 6, ...etc

// 2. Looping over an array. Consider this variable:
let nums = [3, 57, -9, 20, 67]
// - Create a loop that will log the highest number from the array. **Expected output** --> 67
const highest = nums[0]
for(let i = 0; i < nums.length; i++) {
  if(nums[i] > highest) {
    highest = nums[i]    
  }
}
console.log(highest)
// Output: 67

// - Create a loop that will log the lowest number from the array **Expected output** --> -9
let lowest = nums[0]
for(let i = 0; i < nums.length; i++) {
  if(nums[i] < lowest) {
    lowest = nums[i]
  }
}
console.log(lowest)
// Output: -9

// - Create a loop that will log the remainder of each number when divided by 2. **Expected output** --> 1, 1, -1, 0, 1
for(let i = 0; i < nums.length; i++) {
  console.log(nums[i] % 2)
}
// Output: 1, 1, -1, 0, 1

// 3. Looping over a string. Consider this variable:
var myString = "learn student"

// - Write the code that will log the number of times the letter "e" occurs in the string. **Expected output** --> 2
let letterECount = 0
for(let i = 0; i < myString.length; i++) {
  if(myString[i] === 'e') {
    letterECount += 1
  }
}
console.log(letterECount)
// Output: 2

// ### STRETCH Challenges

//1. Even or Odd: Write a for loop that iterates from 0 to 15. For each iteration, it will check if the current number is odd or even, and display the appropriate outcome. **Expected output** -> "0 is even" "1 is odd" "2 is even" ...etc

for(let i = 0; i <= 15; i++) {
  if(i % 2 === 0) {
    console.log(`${i} is even`)
  } else {
    console.log(`${i} is odd`)
  }
}
// Output: "0 is even", "1 is odd", "2 is even", ...etc

// 2. Fizz Buzz: Use a for loop to log all numbers from 1-100.  If a number is a multiple of 3, replace it with the word `fizz`. If a number is a multiple of five, replace it with the word `buzz`. If a number is a multiple of both 3 and 5, replace it with `fizzbuzz`. **Expected output** --> 1, 2, "fizz", 4, "buzz", "fizz", 7, 8, "fizz", "buzz", 11, "fizz", 13, 14, "fizzbuzz" ...etc

for(let i = 1; i <= 100; i++) {
  if(i % 3 == 0 && i % 5 == 0) {
    console.log("fizzbuzz")
  } else if(i % 3 === 0) {
    console.log("fizz")
  } else if(i % 5 === 0) {
    console.log("buzz")
  } else {
    console.log(i)
  }
}
// Output: 1, 2, "fizz", 4, "buzz", 6, 7, 8, "fizz", "buzz", 11, "fizz", 13, 14, "fizzbuzz", ...etc
```

---

# Lecture Notes

### Overview
- Iteration is the process of repeating a task until a condition is met
- Iteration is a fundamental concept in programming
- There are many ways to iterate, one of which is a for loop

### Process
- Ensure you are in the cohort-lecture-examples repo
- Ensure your local is up to date and there are no stale branches
- Create a new branch
- Create a JavaScript file with the naming convention `language-topic.js`
- Run the file with `node`

### Additional Notes and Goals
- For loops don't innately interact with arrays, for loops are just good at counting
- For loops are one way to create iteration, but definitely not the only way

### Major Takeaways
- For loops take three pieces of information: where to start, where to stop, and how to there
- For loops have an associated executable block of code that will run once for every iteration
- Logic can be passed into the executable block of code to modify the outcome of the iteration

### Lecture
One of the most fundamental concepts in coding is the being able to repeat a process over and over again. This is called iteration. Computers are really great at iteration. There are many ways to create iteration. Today we will look specifically at how for loops can interact with arrays. The array data type is basically a list. Developers use arrays to group data. Two very common actions are wanting to look at each item in an array or make a decision about each item in the array.

#### Anatomy of a Loop
For loops don't innately connect to arrays. But they are really good at counting. And we can match up the counting action of a for loop to match to the indexes of an array.

To create a for loop we need three pieces of information.
- Where to start counting
- Where to stop counting
- How to get from the start to the stop

Since we often use for loops on arrays, it is a convention to use the variable name `index` to store the current count. This is often shorted to `i`. This is the longhand way to write the three pieces.
```javascript
for(let index = 0; index < 10; index = index + 1)
```

Shorthand version of the same code.
```javascript
for(let i = 0; i < 10; i++)
```

Adding the executable block of code. The code inside the curly braces will run every time the loop runs.
```javascript
for(let i = 0; i < 10; i++) {
  console.log(i)
}
```

#### Connecting Loops to Arrays
Loops don't innately connect to arrays but we can set the starting and stopping values to match the indexes of an array.
- All arrays start with the index of zero
- All arrays have a length property
- Once we have an index we can extract the value

```javascript
const numsArray = [5, 6, 7, 8, 9]
for(let i = 0; i < numsArray.length; i++) {
  console.log("index:", i)
  console.log("value:", numsArray[i])
}
```

#### Creating Logic in the Loop
We can create code logic in the loop by adding things like conditional statements to the executable block of code.
- Return only the odd numbers

```javascript
const numsArray = [5, 6, 7, 8, 9]
for(let i = 0; i < numsArray.length; i++) {
  if(numsArray[i] % 2 !== 0){
    console.log(`${numsArray[i]} is an odd number!`)
  }
}
```

### Review
- For loops are really great at creating a series of numbers
- For loops can be used to iterate through arrays by lining up the numbers with the array's indexes
- For loops have an executable block of code that can perform logic

### Next Steps
- Open the syllabus section and briefly run through the challenges and expectations
- Remind the student to use the `javascript-intro-challenges` repo
- Remind the students of the appropriate naming conventions for their branch and file
- Post pairs in Slack
- Open breakout rooms with ability for participants to choose their room

---
[Back to Syllabus](../README.md#unit-one-javascript-foundations)
