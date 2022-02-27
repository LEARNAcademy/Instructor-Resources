# JavaScript Functions, Loops, and Arrays (Oh My!)

- [Challenges](#challenges)
- [Lecture Notes](#lecture-notes)

#### Overview
Functions are powerful tools that can take any kind of data as an input. Often we need a function to interact with data sets and perform iterations. This section integrates functions, loops, and arrays to create reusable, iterative code machines.

#### Previous Lecture (42 min)
[![YouTube](http://img.youtube.com/vi/V6pmC4ylFjk/0.jpg)](https://www.youtube.com/watch?v=V6pmC4ylFjk)

#### Learning Objectives
- can extrapolate that an array can be passed into a function via an argument
- can create a function that acts on an array using a for loop

#### Process
- `cd` into the `javascript-foundations-challenges` repository
- Create a new branch: `func-loops-arrays-initials1-initials2` (ex. func-loops-arrays-aw-sp)
- `touch` a file with no spaces and `.js` extension: `func-loops-arrays-student1-student2.js` (ex. func-loops-arrays-austin-sarah.js)
- Open the folder in a text editor
- Code!

#### Troubleshooting Tips
- Does the function have a return?
- Is there a `console.log` on the function invocation?
- Does the number of arguments match the number of parameters?

---

### Putting It All Together
As we work to solve more complicated problems with code, we need to add more logic into our functions. In this section, we will explore how arrays and loops can be integrated into functions.

**Example:** Create a function that takes in an array and returns a new array with all numbers multiplied by 5.

```javascript
var myArr1 = [1, 5, 7, 3, 10]

const mult5 = (array) => {
  let newArr = []
  for(let i=0; i<array.length; i++){
    newArr.push(array[i] * 5)
  }
  return newArr
}

console.log(mult5(myArr1))
```

Notice that we created an empty array inside our function and used the **.push()** method to populate our empty array. The function then returned the newly populated array.

In the following example, we can add a nested conditional statement to return only certain items from the array.

**Example:** Create a function that takes in an array and returns a new array with only the even numbers.

```javascript
var myArr2 = [1, 2, 7, 4, 10, 8, 9]

const onlyEven = (array) => {
  let newArr = []
  for(let i=0; i<array.length; i++){
    if(array[i] % 2 === 0){
      newArr.push(array[i])
    }
  }
  return newArr
}

console.log(onlyEven(myArr2))
```

---

### Challenges
```javascript
// Copy the challenges into your JavaScript file. Comment out the instructions and code the solution to each problem beneath the prompt.
// Don't forget to pseudo code.

// Write a function that takes in an array of numbers and returns an array with all numbers multiplied by 3.
var testArr1 = [3, 9, 15, 4, 10]
const multipliedByThree = (array) => {
  // create an empty array to store multiplied numbers
  let newArray = []
  // iterate over array
  for(let i = 0; i < array.length; i++) {
    // push current iteration multiplied by three to newArray
    newArray.push(array[i] * 3)
  }
  return newArray
}
console.log(multipliedByThree(testArr1))
// Output: [9, 27, 45, 12, 30]

// Write a function that takes in an array of numbers and returns a new array with only odd numbers.
var testArr2 = [0, 2, -7, 3, 5, 8, 10, 13]
const onlyOdd = (array) => {
  // create an empty array to store odd numbers
  let oddArray = []
  // iterate over array
  for(let i = 0; i < array.length; i++) {
    // evaluate if current iteration is odd using modulo
    if(array[i] % 2 !== 0) {
      // push current iteration multiplied by three to newArray
      oddArray.push(array[i])
    }
  }
  return oddArray
}
console.log(onlyOdd(testArr2))
// Output: [-7, 3, 5, 13]

// Write a function that takes in an array of numbers and letters and returns a string with only the letters. HINT: use the typeof method.
var comboArr = [7, "n", true, "i", "c", 10, "e", -388, "w", 3, "o", 0, "r", false, "k"]
const onlyLetters = (array) => {
  // create an empty array to store just letters
  let stringArray = []
  // iterate over array
  for(let i = 0; i < array.length; i++) {
    // check if current iteration is a string using typeof
    if(typeof array[i] === "string") {
      // push iteration that evaluates as a string to array
      stringArray.push(array[i])
    }
  }
  return stringArray.join("")
}
console.log(onlyLetters(comboArr))
// Output: "nicework"

// Create a function that takes in an array of numbers and returns the sum.
var addThese1 = [1, 2, 3, 4]
const sumOfArray = (array) => {
  // declare variable that is set to start value of 0
  let sum = 0
  //iterate over array
  for(let i = 0; i < array.length; i++) {
  // add to sum the current iteration
    sum += array[i]
  }
  return sum
}
console.log(sumOfArray(addThese1))
// Output: 10

var addThese2 = []
console.log(sumOfArray(addThese2))
// Output: 0

// Create a function that takes in an array of numbers and returns the index of the largest number.
var indexHighestNumber = [1, 4, 2, 3]
const findHighestNumber = (array) => {
  // declare variable that is set to start value of 0
  let highestNumber = 0
  // declare variable that stores the value of the last iteration
  let lastNumber = array[0]
  // iterate over array
  for(let i = 0; i < array.length; i++) {
    // check if the last number is equal to the current iteration
    if(array[i] > lastNumber) {
      // set last number to be current iteration if it is larger so future iterations are only compared to the highest number in array to that point
      lastNumber = array[i]
      // set highest number to current index if it is larger than last number
      highestNumber = i
    }
  }
  return highestNumber
}
console.log(findHighestNumber(indexHighestNumber))
// Output: 1

// STRETCH Challenges

// Create a function that takes in two arrays and returns one array with no duplicate values.
var arr1 = [3, 7, 10, 5, 4, 3, 3]
var arr2 = [7, 8, 2, 3, 1, 5, 4]
const noDuplicates = (array1, array2) => {
// create variable that holds concated arrays together
let concatArray = array1.concat(array2)
  let noDuplicateArray = []
  // iterate over each index of the array and compare current value in array to new array
  for(let i = 0; i < concatArray.length; i++) {
    if(noDuplicateArray.indexOf(concatArray[i]) === -1) {
      // push value that is not a duplicate into empty array
      noDuplicateArray.push(concatArray[i])
    }
  }
  return noDuplicateArray
}
console.log(noDuplicates(arr1, arr2))
// Output: [3, 7, 10, 5, 4, 8, 2, 1]

// Create a function that takes in two numbers as arguments and returns an array the length of the first number filled with the second number.
var arrayLength = 6
var arrayValue = 0
const buildArray = (length, value) => {
  // create an empty array
  let newArray = []
  // iterate for the length provided
  for(let i = 0; i < length; i++) {
    // for each iteration, push the value given into empty array
    newArray.push(value)
  }
  return newArray
}
console.log(buildArray(arrayLength, arrayValue))
// Output: [0, 0, 0, 0, 0, 0]

var arrayLength = 4
var arrayValue = 11
console.log(buildArray(arrayLength, arrayValue))
// Output: [11, 11, 11, 11]

// Create a function that takes a number as an argument. Add up all the numbers from 1 to the number you passed to the function.
// 1 + 2 + 3 + 4 = 10
var addUp1 = 4
const letsAdd = (number) => {
  // create variable that starts at 0
  let mySum = 0
  // iterate to the number 4 starting at the number 1
  for(let i = 1; i <= number; i++) {
    // add the variable mySum the set index number which will increase by one each iteration.
    mySum += i
  }
  return mySum
}
console.log(letsAdd(addUp1))
// Output: 10

var addUp2 = 10
// 1 + 2 + 3 + 4 + 5 + 6 + 7 + 8 + 9 + 10 = 55
console.log(letsAdd(addUp2))
// Output: 55

var addUp3 = 600
console.log(letsAdd(addUp3))
// Output: 180300

// EPIC Challenges
// In this challenge, as a developer you will create a number guessing game.  Please read through all steps before starting.

// Create a function called highLow that takes in a number and returns whether the number is higher or lower than the "answer" which is a random number.
// Create an HTML page and link your JavaScript file. More info here .

// <!DOCTYPE html>
// <html lang="en">
// <head>
//   <meta charset="UTF-8">
//   <meta http-equiv="X-UA-Compatible" content="IE=edge">
//   <meta name="viewport" content="width=device-width, initial-scale=1.0">
//   <title>Document</title>
// </head>
// <body>
//   <h1>Number Checker</h1>
//   <p>I am thinking of a number between 1 and 100...</p>
//   <input type="text" id="number">
//   <button type="button" name="button" onclick="highLow()">Click me!</button>
//   <script type="text/javascript" src="js-functions-loops-arrays.js"></script>
//   <h3 id="output"></h3>
// </body>
// </html>

// As a user, I see a prompt or input where I can guess a number between 1 and 100 (both inclusive).
// As a user, I can see if my guess is too high or too low.
// As a user, if I guess the "answer" correctly I am notified that I won.
// As a user, I can continue to guess the "answer" until I am correct.
// STRETCH: As a user, if I have not guessed the correct number in seven tries I see a losing message.

var guesses = 0
var randomNumber = Math.ceil(Math.random() * 100)
const highLow = () => {
  var number = document.getElementById("number").value
  if(number == randomNumber) {
    document.getElementById("output").innerHTML = "You guessed the right number! 🥳"
    alert("You guessed the right number!")
    guesses = 0
  } else {
    for(let i = 1; i < 100; i++) {
      if(guesses >= 6){
        alert(`Sorry, out of guesses!  The number was ${randomNumber}`)
        guesses = 0
      }	else if(number < randomNumber) {
        document.getElementById("output").innerHTML = `${number} is too low.  Please guess again`
      } else if(number > randomNumber) {
        document.getElementById("output").innerHTML = `${number} is too high.  Please guess again`
      } else {
        return "oops, something went wrong"
      }
    }
  }
  guesses ++
}
```
---

# Lecture Notes

### Overview
- Incorporating looping logic into reusable functions
- Functions are dynamic and not attached to any particular dataset
- Collecting the output of the iteration into a storage place
- Functions will only return one thing

### Process
- Ensure you are in the cohort-lecture-examples repo
- Ensure your local is up to date and there are no stale branches
- Create a new branch
- Create a JavaScript file with the naming convention `language-topic.js`
- Run the file with `node`

### Additional Notes and Goals
- Establish good indentation practices
- Tracking many scopes (many curly braces)

### Major Takeaways
- Problem solving with iteration
- Scope of the `for loop` vs scope of the function

### Lecture
Functions are logic machines that developers use to create reusable, or dynamic, code. Functions must be invoked. When a function is invoked it will always return exactly one thing. Functions can be designed to have one or more inputs so that you can use a function logic to manipulate data.

#### Iteration
Let's create a function that will multiply each number in an array by 5. It doesn't matter what numbers are in the array or how many numbers are in the array. The function will handle any array of numbers.
```javascript
const myArrayOfNums1 = [2, 3, 4, 5, 6]
const myArrayOfNums2 = [4, 5, 6]
const myArrayOfNums3 = [7, 8, 9, 10]
```

Anytime you are faced with a problem and you are thinking to yourself, I need to do something to each item, or make a decision about each item, think iteration.
- Set up a function that takes an array as a parameter
- Call the function passing in each of the test arrays

```javascript
const myArrayOfNums1 = [2, 3, 4, 5, 6]
const myArrayOfNums2 = [4, 5, 6]
const myArrayOfNums3 = [7, 8, 9, 10]

const mult5 = (array) => {

}
console.log(mult5(myArrayOfNums1))
console.log(mult5(myArrayOfNums2))
console.log(mult5(myArrayOfNums3))

```

Does this work?

```javascript
const mult5 = (array) => {
  return array * 5
}
console.log(mult5(myArrayOfNums1))
console.log(mult5(myArrayOfNums2))
console.log(mult5(myArrayOfNums3))

// Output: NaN
```

Nope because arrays can't be multiplied, only numbers can. So we need to get into this array and have access to each number. The word "each" always makes me think of iteration.

#### Adding a Loop: Part I
For loops require three things: a starting place, a stopping place, and how to get from the starting to the stopping. For loops don't innately connect with arrays. There is nothing that says a for loop's iteration is happening on an array. For loops are only good at counting. To get a for loop to iterate on an array we just match the count to the indexes of an array. And if we have the index, we can extract the values. So `i` is completely arbitrary. It is just a variable that communicates intent.

```javascript
const myArrayOfNums1 = [2, 3, 4, 5, 6]
const myArrayOfNums2 = [4, 5, 6]

const mult5 = (array) => {
  for(let i = 0; i < array.length; i++) {
    console.log(i)
  }
}
console.log(mult5(myArrayOfNums1))
// Output:
// 0
// 1
// 2
// 3
// 4
// Output: undefined

console.log(mult5(myArrayOfNums2))
// Output:
// 0
// 1
// 2
// Output: undefined
```

- Each iteration returns the current value of `i`
- The function logs undefined because there is no return
- We have crafting a for loop to log a series of numbers that match up exactly with the indexes of whatever array we pass in to the function

#### #### Adding a Loop: Part II
Now that we have successfully added a for loop that will create a series of numbers that match the indexes, we can extract the value.
- To get the value from the array we need the name of the array and the index in square brackets

```javascript
const myArrayOfNums1 = [2, 3, 4, 5, 6]
const myArrayOfNums2 = [4, 5, 6]

const mult5 = (array) => {
  for(let i = 0; i < array.length; i++) {
    console.log(array[i])
  }
}
console.log(mult5(myArrayOfNums1))
// Output:
// 2
// 3
// 4
// 5
// 6
// Output: undefined

console.log(mult5(myArrayOfNums2))
// Output:
// 4
// 5
// 6
// Output: undefined
```

- Each iteration returns the value at each index of the array
- The function logs undefined because there is no return

#### Manipulating the Output
Now that we can access the value in the array we can manipulate the output by performing logic on each number in the array.

```javascript
const myArrayOfNums1 = [2, 3, 4, 5, 6]
const myArrayOfNums2 = [4, 5, 6]

const mult5 = (array) => {
  for(let i = 0; i < array.length; i++) {
    console.log(array[i] * 5)
  }
}
console.log(mult5(myArrayOfNums1))
// Output:
// 10
// 15
// 20
// 25
// 30
// Output: undefined

console.log(mult5(myArrayOfNums2))
// Output:
// 20
// 25
// 30
// Output: undefined
```

#### Returning the Value
Right now the console log is doing all the heavy lifting. Our function is still returning undefined. Functions need the keyword `return`.
- Remove the console.log and add return
- Explore the idea of where to add the return

```javascript
const myArrayOfNums1 = [2, 3, 4, 5, 6]
const myArrayOfNums2 = [4, 5, 6]

const mult5 = (array) => {
  for(let i = 0; i < array.length; i++) {
    return array[i] * 5
  }
}
console.log(mult5(myArrayOfNums1))
// Output: 10

console.log(mult5(myArrayOfNums2))
// Output: 20
```

We got rid of the undefined, but it is still not producing the correct response. That is because once the function returns something, it is done. And the iteration will not continue.

#### Capturing Each Value of During the Iteration
We can't return in the loop. That kills the iteration. We need to capture these values and keep them somewhere and return that thing rather than a single value in the loop.
- Create a storage array outside the scope of the for loop
- Return the array rather than the inner workings of the loop

```javascript
const myArrayOfNums1 = [2, 3, 4, 5, 6]
const myArrayOfNums2 = [4, 5, 6]

const mult5 = (array) => {
  let storageArray = []
  for(let i = 0; i < array.length; i++) {
    storageArray.push(array[i] * 5)
  }
  return storageArray
}
console.log(mult5(myArrayOfNums1))
// Output: [10, 15, 20, 25, 30]

console.log(mult5(myArrayOfNums2))
// Output: [20, 25, 30]
```

### Review
- What is function?
- What is iteration?
- What are some keywords that can help you identify the need for iteration?
- Why can't you use the keyword `return` inside the scope of a for loop?
- What should you look for if your function logs undefined?
- What does `.push()` do?

### Next Steps
- Open the syllabus section and briefly run through the challenges and expectations
- Remind the student to use the `javascript-foundations-challenges` repo
- Remind the students of the appropriate naming conventions for their branch and file
- Post pairs in Slack
- Open breakout rooms with ability for participants to choose their room

---
[Back to Syllabus](../README.md#unit-one-javascript-foundations)
