# JavaScript Higher-Order Functions

- [Challenges](#challenges)
- [Lecture Notes](#lecture-notes)

#### Overview
Higher-order functions are built in methods in JavaScript that act on arrays. They are a specific subset of built in methods that take a function as an argument.

#### Previous Lecture (1 hour 35 min)
[![YouTube](http://img.youtube.com/vi/gvbLBhc20w4/0.jpg)](https://www.youtube.com/watch?v=gvbLBhc20w4)

#### Learning Objectives
- can define `.forEach()` and `.map()` and `.filter()` as array methods
- can distinguish between a function and a higher-order function
- can utilize the required parameter for `.forEach()` and `.map()` and `.filter()`
- can recall the optional parameters for `.forEach()` and `.map()` and `.filter()`
- can demonstrate the proper use of both `.map()` and `.filter()` to produce expected outcomes

#### Vocabulary
- higher-order function
- value
- index

#### Process
- `cd` into the `javascript-foundations-challenges` repository
- Create a new branch: `higher-order-initials1-initials2` (ex. higher-order-aw-sp)
- `touch` a file with no spaces and `.js` extension: `higher-order-student1-student2.js` (ex. higher-order-austin-sarah.js)
- Open the folder in a text editor
- Code!

#### Troubleshooting Tips
- Does the function have a return?
- Is there a `console.log` on the function invocation?
- Does the number of arguments match the number of parameters?

---

## Higher-Order Functions
A higher-order function is a function that either takes in another function as an argument or returns another function as an output.

We will focus on two higher-order functions for this lesson - **.map()** and **.filter()** both have three built-in parameters - the value, index, and array.

What the parameters are named is arbitrary, but the order will always be the same. The higher-order functions have to take at least one argument (value) but can take two or three if needed.

`.map(value, index, array)`  
`.filter(value, index, array)`


1. The **value** of the array at the current iteration (required).

2. The **index** of the array at the current iteration (optional).

3. The **array** the higher-order function was called on (optional).


## Map

The **.map()** function iterates through an array and returns a new array of the same length.

Here is an example of iterating using a for loop:

```javascript
var myArray = [5, 3, 2, 9, 8];

let newArray = [];
for(let i=0; i<arr.length; i++){
  let valueTimesThree = myArray[i] * 3;
  console.log(valueTimesThree);
  newArray.push(valueTimesThree);
}

console.log(newArray);
```

Now let's look at this same objective with **.map()**

```javascript
var myArray = [5, 3, 2, 9, 8]

const multiplier = myArray.map(value => {
    return value * 3
})

console.log(multiplier)
```

Because we are using an arrow function we can reduce the code even further. If there is only one line of code to be executed, we can remove the `return` keyword as the return is implied.

```javascript
var myArray = [5, 3, 2, 9, 8]

const multiplier = myArray.map(value => value * 3)

console.log(multiplier)
```

And finally let's wrap the `.map()` logic in a function that can take in any array to make the function reusable.

```javascript
var myArray = [5, 3, 2, 9, 8]

const multiplier = (array) => {
  return array.map(value => value * 3)
}
console.log(multiplier(myArray))
```

Notice that `.map()` *iterates* through the specified array **AND** returns a new array with the updated values.

Here is another example with proper pseudocoding:
```javascript
// create a function that takes in an array and returns each word capitalized
var fruitArray = ["banana", "mango", "apple", "grape"]

// declare a function that takes in an array
const capitalizer = (array) => {
  // create a local variable that maps through the array
  let eachItem = array.map(value => {
    // with each value access the first index and capitalize the letter then concatenate the remainder of the word
    return value[0].toUpperCase() + value.substring(1)
  })
  // return the local variable joined into a string
  return eachItem.join(" ")
}
// logging the function and pass in the array
console.log(capitalizer(fruitArray))
```
**Note:** - This function has a return for the outer function **AND** a return for the higher-order function.


## Filter

The `.filter()` function loops through an array and returns a new array with only the values that are **truthy** or the values that satisfy your stated condition. Filter will return a subset of the given array.

Here is an example of *iterating* and returning a subset using a for loop:

```javascript
var numbersArray1 = [1, 2, 7, 4, 10, 8, 9]

const onlyEven = (array) => {
  let newArr = []
  for(let i=0; i<array.length; i++){
    if(array[i] % 2 === 0){
      newArr.push(array[i])
    }
  }
  return newArr
}

console.log(onlyEven(numbersArray1))
```

So, in the above example, we have created a function that takes an array as an argument, loops through the array, and returns a new array containing only the even numbers.

#### Using Filter

```javascript
var numbersArray1 = [1, 2, 7, 4, 10, 8, 9]

const onlyEven = (array) => {
  return array.filter(value => value % 2 === 0)
}

console.log(onlyEven(numbersArray1))
```

Here is another example with proper pseudocoding:
```javascript
// create a function that returns only the values at the odd indexes
var numbers = [4, 24, 5, 9, 0, 78]

// declare a function that takes in an array
const getOnlyOddIndex = (array) => {
  // return a higher-order function that takes in the value and the index
  return array.filter((value, index) => {
    // return only the values that have an odd index
    return index % 2 !== 0
  })
}
// log the function and pass in the array
console.log(getOnlyOddIndex(numbers))
```


## Map vs Filter

When deciding which higher-order function to use, remember these two differences:

- `.map()` will do something to each item in an array and return an array of the same length.
- `.filter()` will make a decision about each item in an array and return a subset based on the criteria given.

---

### Challenges
 Copy the challenges into your JavaScript file. Comment out the instructions and code the solution to each problem beneath the prompt. Use `.map()` or `.filter()` to complete all of the following exercises.   
 **Don't forget to pseudo code.**

```javascript
// 1. Write a function that takes in an array of numbers and returns a new array with all numbers multiplied by 10.

  var arr1 = [3, 9, 15, 4, 10]
  // --> [30, 90, 150, 40, 100]

  // declare a function that takes in an array of numbers
  const tenFold = (array) => {
    // use .map() function to iterate through the array and return a new array with all the values multiplied by 10
    return array.map(value => value * 10)
  }
  // logging the function and pass in the array
  console.log(tenFold(arr1))
  // Output: [30, 90, 150, 40, 100]

// 2. Write a function that takes in an array of numbers and returns a new array with only odd numbers.

  var arr2 = [2, 7, 3, 5, 8, 10, 13]
  // --> [7, 3, 5, 13]

  // declare a function that takes in an array of numbers
  const onlyOdd = (array) => {
    // use .filter() function to iterate through the array and return a new array with only odd values determined by using modulo and strict inequality operators
    return array.filter(value => value % 2 !== 0)
  }
  // logging the function and pass in the array
  console.log(onlyOdd(arr2))
  // Output: [7, 3, 5, 13]

// 3. Write a function that takes in an array of numbers and letters and returns a string with only the letters. **HINT:** Use [typeof](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/typeof) method

  var comboArr = [7, "n", "i", "c", 10, "e", false, "w", 3, "o", "r", "k"]
  // --> "nicework"

  // declare a function that takes in an array of numbers and letters
  const letters = (array) => {
    // create a local variable that filters through the array assessing each value
    let dataType = array.filter(value => {
      // using typeof and strict equality operators return the values with a datatype of string
      return typeof(value) === "string"
    })
    // return the local variable joined into a string with no spaces
    return dataType.join("")
  }
  // logging the function and pass in the array
  console.log(letters(comboArr))
  // Output: "nicework"

// 4. Create a function that takes in an array and returns an array without any false, null, 0, or blank values.

  var filterArrayValues = [58, " ", "abcd", true, null, false, 0]
  // --> [58, "abcd", true]

  // declare a function that takes in an array
  const truth = (array) => {
    // create a local variable that filters through the array assessing each value
    let trueValue = array.filter(value => {
      // using Boolean() function and strict equality operators return values that are true
      return Boolean(value) === true
    })
    // return the local variable excluding blank strings using strict inequality operator
    return trueValue.filter(value => value !== " ")
  }
  // logging the function and pass in the array
  console.log(truth(filterArrayValues))
  // Output: [58, "abcd", true]

```

**STRETCH Challenges**
```javascript
// 1. Create a function that takes in a string and returns a new string with all the vowels removed.

  var str = "javascript is awesome"
  // --> "jvscrpt s wsm"

  // declare a function that takes in a string
  const deleteVowels = (string) => {
    // create a local variable to split the string into an array of letters
    let letterArray = string.split("")
    // use .filter() function to iterate through the array and return a new array without vowels by using strict inequality and logical operators
    let noVowel = letterArray.filter(value =>
      value !== "a" &&
      value !== "e" &&
      value !== "i" &&
      value !== "o" &&
      value !== "u")
    // return the string without any vowels using the join() method  
    return noVowel.join("")
  }
  // logging the function and pass in the string
  console.log(deleteVowels(str))
  // Output: "jvscrpt s wsm"

// 2. Create a function that takes in two arrays as arguments returns one array with no duplicate values.

  var arr1 = [3, 7, 10, 5, 4, 3]
  var arr2 = [7, 8, 2, 1, 5, 4]
  // --> [3, 7, 10, 5, 4, 8, 2, 1]

  // declare a function that takes in two arrays
  const noDuplicates = (array1, array2) => {
    // use a local variable to concat two arrays
    let array3 = array1.concat(array2)
    // filter through the array3 to see if the index of the current value matches the index of the current iteration and return an array with no duplicate values
    return array3.filter((value, index, array) =>
      array.indexOf(value) === index)
  }
  // logging the function and pass in the arrays
  console.log(noDuplicates(arr1, arr2))
  // Output: [3, 7, 10, 5, 4, 8, 2, 1]
```
---

# Lecture Notes

### Overview
-

### Process
- Ensure you are in the cohort-lecture-examples repo
- Ensure your local is up to date and there are no stale branches
- Create a new branch
- Create a JavaScript file with the naming convention `language-topic.js`
- Run the file with `node`

### Additional Notes and Goals
### Major Takeaways
### Lecture
#### Topic
### Review

### Next Steps
- Open the syllabus section and briefly run through the challenges and expectations
- Remind the student to use the `javascript-foundations-challenges` repo
- Remind the students of the appropriate naming conventions for their branch and file
- Post pairs in Slack
- Open breakout rooms with ability for participants to choose their room
---
[Back to Syllabus](../README.md#unit-one-javascript-foundations)
