# JavaScript Functions, Loops, and Arrays (Oh My!)

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
[Back to Syllabus](../README.md#unit-one-javascript-foundations)
