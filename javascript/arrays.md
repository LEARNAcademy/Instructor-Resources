# JavaScript Arrays

- [Challenges](#challenges)
- [Lecture Notes](#lecture-notes)

#### Overview
Arrays are variables that store collections of data in an ordered list. Having an organized data set gives developers the ability to access particular pieces of information, access every item in the set, or make a decision about every item in the data set. Arrays are indexed which means the data can be accessed by its location within the array. Arrays also have many built-in methods that can be used to manipulate and access the content.

#### Previous Lecture (43 min)
[![YouTube](http://img.youtube.com/vi/Bj3li2W6yks/0.jpg)](https://www.youtube.com/watch?v=Bj3li2W6yks)

#### Learning Objectives
- can recall the syntax of an array
- can define the value and index
- can conceptualize the difference between mutator and accessor methods
- can extract a single value from an array
- can apply built in methods to mutate and access the array

#### Vocabulary
- array
- element
- value
- index
- zero indexed
- built-in method
- argument
- mutator/setter methods
- accessor/getter methods
- destructuring

#### Additional Resources
- [W3Schools JavaScript Arrays](https://www.w3schools.com/js/js_arrays.asp)
- [W3Schools JavaScript Array Methods](https://www.w3schools.com/js/js_array_methods.asp)

#### Process
- `cd` into the `javascript-intro-challenges` repository
- Create a new branch: `arrays-initials1-initials2` (ex. arrays-aw-sp)
- `touch` a file with no spaces and `.js` extension: `arrays-student1-student2.js` (ex. arrays-austin-sarah.js)
- Open the folder in a text editor
- Code!

#### Troubleshooting Tips
- Is the file path is correct?

---


### Arrays: Collections of Data
Until now, we've only dealt with one piece of information at a time: one number, one string, one element on a page. But, often we need to group things together. For example, what if we wanted to have a list of the months of the year? We'd use an **array**, which is a collection of ordered data. Arrays can contain any type of information as long as it is a data type JavaScript recognizes.

Here are a few examples of arrays assigned to variables:

```javascript
var months = ["January", "February", "March", "April", "May", "June"]

var numbers = [17, 15, 14, 3, 5, 10]

var comboDataArray = [17, "January", true, "March 14", 42, null, false, "LEARN", 10]
```

### Anatomy of an Array

```javascript
var learnStudents = ["Debra", "Jonas", "Joel"]
```

Arrays consists of the following:
1. Variable declaration
    - Just like any other variable, we must inform JavaScript of our intention to create a variable
    - `var`
2. Variable name
    - Variables must be camelCase and descriptive
    - `var learnStudents`
3. Single equal sign
    - Variables must be assigned with a single equal sign
    - `var learnStudents =`
4. Opening and closing square brackets `[]`
    - The contents of an array are stored inside square brackets
    - `var learnStudents = []`
5. Elements in the array
    - Each item in the array is called an **element**
    - Elements are separated from each other by a comma
    - Elements in the array must be a data type recognized by JavaScript
    - `var learnStudents = ["Debra", "Jonas", "Joel"]`

### Value
Each element in the array must be a JavaScript data type. The content of each element is called the **value**.

```javascript
var learnStudents = ["Debra", "Jonas", "Joel"]
```
- `"Debra"` is a value in the array
- `"Jonas"` is a value in the array
- `"Joel"` is a value in the array

### Index
Every value in an array has a particular location know as the **index**. Indexes are sequential numbers that are a bit like an address for every element in the array. Arrays are **zero indexed** which means the elements are numbered starting with the number 0 and increase by one whole number for each new element.

```javascript
var learnStudents = ["Debra", "Jonas", "Joel"]
```
- The value `"Debra"` is at the index of `0`
- The value `"Jonas"` is at the index of `1`
- The value `"Joel"` is at the index of `2`

### Accessing Elements
One of the many benefits to storing data in arrays is that we can access the individual values. Since the indexes are like an address, we can reference the variable that holds the entire array and the specific index in square brackets in order to retrieve the value. If the index does not exist the output will be undefined.

```javascript
var learnStudents = ["Debra", "Jonas", "Joel"]

console.log(learnStudents[0])
// output --> "Debra"

console.log(learnStudents[2])
// output --> "Joel"

console.log(learnStudents[6])
// output --> undefined
```

### Changing Elements
By referencing the array and the index we are essentially creating a variable for that particular value. Just like any other variable we can reassign its value using a single equal sign and a new item. This will permanently modify the array.

```javascript
var learnStudents = ["Debra", "Jonas", "Joel"]

learnStudents[0] = "Summer"
console.log(learnStudents)
// output --> ["Summer", "Jonas", "Joel"]

learnStudents[1] = "Brian"
console.log(learnStudents)
// output --> ["Summer", "Brian", "Joel"]
```

### Length Property
Because arrays are an ordered collection of data, they have a length property. The length of an array is dynamic, which means it can change depending on the needs of a developer. `.length` is an informational command that returns the number of elements in the array. The length is the always the last index of the array plus one.

```javascript
var learnStudents = ["Debra", "Jonas", "Joel"]

console.log(learnStudents.length)
// output --> 3
```

### Built-in Methods
JavaScript has many built-in methods. A **built-in method** is a small piece of functionality that has been added to the language to accomplish a common task. Since arrays are a great way to store data it makes sense that there are a lot of built-in methods that act on arrays to help us to access and modify the content. Some built-in methods will require additional information to perform the action intended. This additional information is passed into the parentheses that follow the built-in method which is called an **argument**.

Built-in methods for arrays fall into one of two categories: mutators and accessors. **Mutators** are built-in methods that modify the original array, also know as "setter methods." **Accessors** are built-in methods that do not change the original array, also known as "getter methods."

### Mutators
Mutator methods modify the array the method is called on. When working with mutators it is important to remember the output of the method action will not always be the array. To see the effect of the mutator method we can call the variable containing the array.

**.push(value)**
- Adds a value onto the end of an array
- Takes an argument of what is to be added
- The argument must be a data type recognized by JavaScript
- The output of the method itself is the length of the new array

```javascript
var learnStudents = ["Debra", "Jonas", "Joel"]

console.log(learnStudents.push("Ryan"))
// output --> 4

console.log(learnStudents)
// output --> ["Debra", "Jonas", "Joel", "Ryan"]
```

**.pop()**
- Removes the last value in an array
- The output of the method itself is the value that is removed

```javascript
var learnStudents = ["Debra", "Jonas", "Joel"]

console.log(learnStudents.pop())
// output --> "Joel"

console.log(learnStudents)
// output --> ["Debra", "Jonas"]
```

**.unshift(value)**
- Adds a value to the beginning of an array
- Takes an argument of what is to be added
- The argument must be a data type recognized by JavaScript
- The output of the method itself is the length of the new array

```javascript
var learnStudents = ["Debra", "Jonas", "Joel"]

console.log(learnStudents.unshift("Rachael"))
// output --> 4

console.log(learnStudents)
// output --> ["Rachael", "Debra", "Jonas", "Joel"]
```

**.shift()**
- Removes the value at the zeroth index of the array
- The output of the method itself is the value that is removed

```javascript
var learnStudents = ["Debra", "Jonas", "Joel"]

console.log(learnStudents.shift())
// output --> "Debra"

console.log(learnStudents)
// output --> ["Jonas", "Joel"]
```

**.reverse()**
- Reverses the order of the values in an array
- The output of the method itself is the modified array

```javascript
var learnStudents = ["Debra", "Jonas", "Joel"]

console.log(learnStudents.reverse())
// output --> ["Joel", "Jonas", "Debra"]

console.log(learnStudents)
// output --> ["Joel", "Jonas", "Debra"]
```

**.sort()**
- Alphabetizes the values in an array
- Can take an optional argument for more advanced sorting actions
- The output of the method itself is the modified array
- Can take arguments for numbers

```javascript
var learnStudents = ["Debra", "Jonas", "Joel"]

console.log(learnStudents.sort())
// output --> ["Debra", "Joel", "Jonas"]

console.log(learnStudents)
// output --> ["Debra", "Joel", "Jonas"]

let numbers = [4, 2, 5, 1, 3]
numbers.sort((a, b) => a - b)
console.log(numbers)
// output --> [1, 2, 3, 4, 5]
```

### Accessors  
Accessor methods do not modify the original array. Accessors return a specific output or a new array. In order to keep the output of an accessor method, we need to save it as a variable.

**.indexOf(value)**
- Returns the index of the first instance of a given value
- If the value does not exist within the array, returns `-1`
- The original array is unchanged

```javascript
var learnStudents = ["Debra", "Jonas", "Joel"]

console.log(learnStudents.indexOf("Joel"))
// output --> 2

var joelIndex = learnStudents.indexOf("Joel")
console.log(joelIndex)
// output --> 2

console.log(learnStudents.indexOf("Mary"))
// output --> -1

console.log(learnStudents)
// output --> ["Debra", "Jonas", "Joel"]
```

**.lastIndexOf(value)**
- Returns the last index of a given value
- Useful when there are repeated values in an array
- If the value does not exist within the array, returns `-1`
- The original array is unchanged

```javascript
var learnStudents = ["Debra", "Joel", "Jonas", "Joel"]

console.log(learnStudents.lastIndexOf("Joel"))
// output --> 3

var lastJoelIndex = learnStudents.lastIndexOf("Joel")
console.log(lastJoelIndex)
// output --> 3

console.log(learnStudents.lastIndexOf("Mary"))
// output --> -1

console.log(learnStudents)
// output --> ["Debra", "Jonas", "Joel"]
```

**.slice(staringIndex, endingIndex)**
- Returns a subset of the array
- Slice requires an argument for the starting index of the subset
- The ending index is an optional argument, if no ending index is specified the default is the end of the array
- The original array is unchanged

```javascript
var learnStudents = ["Debra", "Mary", "Jonas", "Joel"]

console.log(learnStudents.slice(0, 2))
// output --> ["Debra", "Mary"]

console.log(learnStudents.slice(2))
// output --> ["Jonas", "Joel"]

var slicedArray = learnStudents.slice(2)
console.log(slicedArray)
// output --> ["Jonas", "Joel"]

console.log(learnStudents)
// output --> ["Debra", "Mary", "Jonas", "Joel"]
```

**.concat()**
- Merges two or more arrays to form one combined array
- The original array is unchanged

```javascript
var learnStudents1 = ["Debra", "Jonas", "Joel"]
var learnStudents2 = ["Mary", "Juan", "Matt"]

console.log(learnStudents1.concat(learnStudents2))
// output --> ["Debra", "Jonas", "Joel", "Mary", "Juan", "Matt"]

var comboArrays = learnStudents1.concat(learnStudents2)
console.log(comboArrays)
// output --> ["Debra", "Jonas", "Joel", "Mary", "Juan", "Matt"]

console.log(learnStudents1)
// output --> ["Debra", "Jonas", "Joel"]
```

### Strings to Arrays and Back Again
In JavaScript, arrays and strings have a lot of similar properties. They both are a collection of items, both have a length property, both are zero-indexed. But strings and arrays have many differences. It is often convenient to convert string into arrays and vice-versa.

**.join("")**
- Converts all values in an array to a string
- Join takes an optional argument that describes what is between each value
- The original array is unchanged

```javascript
var learnStudents = ["Debra", "Mary", "Jonas", "Joel"]

console.log(learnStudents.join())
// output --> "Debra,Mary,Jonas,Joel"

console.log(learnStudents.join(""))
// output --> "DebraMaryJonasJoel"

console.log(learnStudents.join(" "))
// output --> "Debra Mary Jonas Joel"

console.log(learnStudents.join("-"))
// output --> "Debra-Mary-Jonas-Joel"

var joinedNames = learnStudents.join(" ")
console.log(joinedNames)
// output --> "Debra Mary Jonas Joel"

console.log(learnStudents)
// output --> ["Debra", "Mary", "Jonas", "Joel"]
```

**.split("")**
- Converts a string into an array
- Split takes an optional argument that describes where the string is split
- The original string is unchanged

```javascript
var learnStudents = "Debra Mary Jonas Joel"

console.log(learnStudents.split())
// output --> ["Debra Jonas Joel"]

console.log(learnStudents.split(""))
// output --> ["D", "e", "b", "r", "a", " ", "J", "o", "n", "a", "s", " ", "J", "o", "e", "l"]

console.log(learnStudents.split(" "))
// output --> ["Debra", "Mary", "Jonas", "Joel"]

console.log(learnStudents.split("a"))
// output --> ["Debr", " M", "ry Jon", "s Joel"]

var splitNames = learnStudents.split(" ")
console.log(splitNames)
// output --> ["Debra", "Mary", "Jonas", "Joel"]

console.log(learnStudents)
// output --> ["Debra", "Mary", "Jonas", "Joel"]
```

### Array Destructuring
The destructuring assignment is a special way of assigning variables in JavaScript. **Destructuring** allows you to take an array and unpack each value into individual variables in a singe assignment.

Destructuring assignments requires variables names in square brackets and an equal number of values. Each variable is assigned in order.

```javascript
var [firstName, secondName] = ["Mary", "Debra"]

console.log(firstName)
// output --> "Mary"

console.log(secondName)
// output --> "Debra"
```
---

### Challenges

```javascript
// Copy the challenges into your JavaScript file. Comment out the instructions and code the solution to each problem beneath the prompt.

// Consider the variable:
var groceryList = ["chips", "dip", "cookies"]

// 1. Write the code that will add "soda" to the end of the original array.
groceryList.push("soda")
console.log(groceryList)
// Output: ["chips", "dip", "cookies", "soda"]

// 2. Write the code that will add "granola" to the end of array without altering the original array.
console.log(groceryList.concat("granola"))
// Output: ["chips", "dip", "cookies", "soda", "granola"]

// 3. Write the code that will return a subset of the array containing only "chips" and "dip".
console.log(groceryList.slice(0, 2))
// Output: ["chips", "dip"]

// 4. Write the code that will add "beans" to the "chips" and "dip" array.
var nachos = groceryList.slice(0, 2)
nachos.push("beans")
console.log(nachos)
// Output: ["chips", "dip", "beans"]

// Consider the variable:
var numbers = [2, 4, 6, 8, 10]

// 5. Write the code that will add the number 0 to the beginning of the array.
numbers.unshift(0)
console.log(numbers)
// Output: [0, 2, 4, 6, 8, 10]

// 6. Write the code that will add the number 12 to the end of the array.
numbers.push(12)
console.log(numbers)
// Output: [0, 2, 4, 6, 8, 10, 12]

// 7. Write the code that will remove the first number from the array.
numbers.shift()
console.log(numbers)
// Output: [2, 4, 6, 8, 10, 12]

// 8. Write the code that will add the number 0 to the beginning of the array without altering the original array. **HINT**: it's not `.unshift` You'll have to get creative! ;)
console.log([0].concat(numbers))
// Output: [0, 2, 4, 6, 8, 10, 12]

// Consider the variable:
var numSet = [2, 13, 6, 8, 4, 2]

// 9. Write the code that finds the index of the first appearance of the number 2.
console.log(numSet.indexOf(2))
// Output: 0

// 10. Write the code that finds the index of the last appearance of the number 2.
console.log(numSet.lastIndexOf(2))
// Output: 5

// 11. Write the code that returns the number at the third index.
console.log(numSet[3])
// Output: 8

// Consider the variable:
var characters = ["y", "a", "r", "r", "a"]

// 12. Write the code that brings all the letters in the characters array together into a string.
console.log(characters.join(""))
// Output: "yarra"

// 13. Write the code that reverses the order of the letters in the characters array and saves it into a variable called charsReversed.
var charsReversed = characters.reverse()
console.log(charsReversed)
// Output: ['a', 'r', 'r', 'a', 'y']

// 14. Write the code that brings all the letters in the charsReversed array together into a string with an asterisk between each letter.
console.log(charsReversed.join("*"))
// Output: "a*r*r*a*y"

// 15. Write the code that brings all the letters in the charsReversed array together into a string without separators.
console.log(charsReversed.join(""))
// Output: "array"

// Create two arrays consisting of three first names of your cohort members in each.
var cohort1 = ["Austin", "TJ", "Chelsea"]
var cohort2 = ["Sarah", "Rob", "Kumba"]
console.log(cohort1)
// Output: ["Austin", "TJ", "Chelsea"]
console.log(cohort2)
// Output: ["Sarah", "Rob", "Kumba"]

// 16. Write the code that sorts the names in alphabetical order.
console.log(cohort1.sort())
// Output: ["Austin", "Chelsea", "TJ"]
console.log(cohort2.sort())
// Output: ["Kumba", "Rob", "Sarah"]

// 17. Write the code that sorts the names in reverse alphabetical order.
console.log(cohort1.sort().reverse())
// Output: ["TJ", "Chelsea", "Austin"]
console.log(cohort2.sort().reverse())
// Output: ["Sarah", "Rob", "Kumba"]

// 18. Write the code that sorts all the names in alphabetical order in a single array.
console.log(cohort1.concat(cohort2).sort())
// Output: ["Austin", "Chelsea", "Kumba", "Rob", "Sarah", "TJ"]

// Consider the variables:
var numbers = [42, 221, 71, 7, 18, 87]
var oddIndexes = []

// 19. Write the code that logs the values from the numbers array that are at odd indexes.
console.log(numbers[1])
// Output: 221
console.log(numbers[3])
// Output: 7
console.log(numbers[5])
// Output: 87

// 20. Write the code that adds the values from odd indexes into the oddIndexes array.
oddIndexes.push(numbers[1])
oddIndexes.push(numbers[3])
oddIndexes.push(numbers[5])
console.log(oddIndexes)
// Output: [221, 7, 87]
```

---

# Lecture Notes

### Overview
- Until now, we've only dealt with primitive data types which are single pieces of information
- Arrays are a non-primitive data type that are collections of ordered data
- Arrays can contain any type of information as long as it is a valid data type
- Interacting with arrays is a really important fundamental concept

### Process
- Ensure you are in the cohort-lecture-examples repo
- Ensure your local is up to date and there are no stale branches
- Create a new branch
- Create a JavaScript file with the naming convention `language-topic.js`
- Run the file with `node`

### Additional Notes and Goals
- Modeling git workflow
- Use online documentation to look at built-in methods

### Major Takeaways
- Bracket notation
- Index and value
- Accessors vs mutators

### Lecture
Arrays are a collection of data. The data is organized like a list with each item having a unique placement in the array.
- Declaring an array
- Saving the array in a variable

```javascript
console.log(["ash", "beech", "cedar", "date"])
var streetNames = ["ash", "beech", "cedar", "date"]
console.log(streetNames )
```

#### Value
Each item in the array must be a data type recognized by JavaScript. The actual data is called the value.

"ash" is a value
"beech" is a value
"cedar" is a value
"date" is a value

#### Indexing
Each item in the array has a unique placement called an index. The index is like an address. The index can be used to extract individual values from the array.
- Zero indexing

```javascript
//                    0         1         2      3
var streetNames = ["ash", "beech", "cedar", "date"]
```

#### Accessing Items
- Bracket notation

```javascript
var streetNames = ["ash", "beech", "cedar", "date"]
console.log(streetNames[0])
console.log(streetNames[1])
console.log(streetNames[2])
console.log(streetNames[3])
```

#### Modifying Items
- Reassigning a value
- Values in the array are reassigned the same way that variables are reassigned with a singel equal sign

```javascript
var streetNames = ["ash", "beech", "cedar", "date"]
streetNames[3] = "elm"
console.log(streetNames)
// Output: ["ash", "beech", "cedar", "elm"]
```

#### Length Property
Length determines the number of items in the array. The output will always be a number. Length is always the last index plus one.
```javascript
var streetNames = ["ash", "beech", "cedar", "date"]
console.log(streetNames.length)
// Output: 4
```

#### Built-in Methods
- Review built in methods
- Review arguments
- Mutators - modify the original array
  - `.push()` - adds an item to the end of the array, takes an argument of the value to add
  - `.pop()` - removes the last item, doesn't take an argument
  - .`reverse()` - doesn't take an argument
  - `.sort()` - alphabetizes string, when sorting numbers additional info will be necessary
- Accessors - doesn't modify the array
  - `.indexOf()` - take the argument of a value and returns the index
  - `.slice()` - creates a subset of the array, take the argument of the index that starts the subset and an optional argument of the end of the subset
  - `.concat()` - merges two arrays
- Array to string
  - `.join()` - takes an argument that determine what is in
  between each character in the string
- String to array
  - `.split()` - takes an argument of where to split the string determining what is at each index in the array

#### Array Destructuring
Destructing allows for individual assignment of array values to variables.

```javascript
var [firstName, lastName] = ["Bruce", "Wayne"]

console.log(firstName)
// Output: "Bruce"
console.log(lastName)
// Output: "Wayne"
```

### Review
- What is an array?
- What is the value?
- What is the index?
- What is the difference between value and index?
- What is a built-in method?
- What is an accessor?
- What is a mutator?

### Next Steps
- Open the syllabus section and briefly run through the challenges and expectations
- Remind the student to use the `javascript-intro-challenges` repo
- Remind the students of the appropriate naming conventions for their branch and file
- Post pairs in Slack
- Open breakout rooms with ability for participants to choose their room

---
[Back to Syllabus](../README.md#unit-one-javascript-foundations)
