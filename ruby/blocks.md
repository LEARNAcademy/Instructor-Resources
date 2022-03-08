# Ruby Blocks and Iterables

- [Challenges](#challenges)
- [Lecture Notes](#lecture-notes)

## Overview
- Ruby has lots of iteration methods
- Ruby uses the keywords `do/end` or {} to create a block of code to be executed

## Learning Objectives
- Passing a block to a Ruby iteration method
- Exploring the do/end vs {} syntax

## Vocabulary
- blocks
- do/end
- times do
- each do
- while
- map

#### Process
- `cd` into the `ruby-challenges` repository
- Create a new branch: `blocks-initials1-initials2` (ex. blocks-aw-sp)
- `touch` a file with no spaces and `.rb` extension: `blocks-student1-student2.rb` (ex. blocks-austin-sarah.rb)
- Open the folder in a text editor
- Code!

---

## Ruby Blocks

Ruby has anonymous functions similar to JavaScript. They are called blocks. Blocks can be created with the `do/end` keywords **OR** with {}. Blocks are code that is passed to a method.

### times do

Times method is a very basic method that will repeat code a certain number of times.

```ruby
my_num = 5
=> 5

> my_num.times do
   puts 'hello'
 end

hello
hello
hello
hello
hello
=> 5
```

### each do

Each method will let you do something with every element of an object or array.

```ruby
> nums = [1, 2, 3]

> nums.each do |value|
    puts value
  end
1
2
3
=> [1, 2, 3]

> nums  
=> [1, 2, 3]
````
Note the original array is untouched.



```ruby
# Block with a `do/end`
> nums.each do |value|
    puts value
  end
1
2
3
=> [1, 2, 3]


# Block with {}
> nums.each { |value| puts value }
1
2
3
=> [1, 2, 3]
```

Blocks can have multiple parameters.

```ruby
# Block with a `do/end`
> nums.each_with_index do |value, index|
    puts "#{index.to_s} #{value.to_s}"
  end
0 1
1 2
2 3
=> [1, 2, 3]


# Block with {}
> nums.each_with_index { |value, index| puts "#{index.to_s} #{value.to_s}" }
0 1
1 2
2 3
=> [1, 2, 3]
```

### While
The while method is a little bit different in that it doesn't take a block as an argument. A while loop requires a starting value and runs until a particular condition is met.

```ruby
> i = 0
> while i < 5
>   puts i
>   i += 1
> end
0
1
2
3
4
```

### map do

Ruby's map method also lets you do something with every element of an array. Map returns a new array filled with whatever gets returned by the block each time it runs.

```ruby
> my_array = [1, 2, 3]

# Block with a `do/end`
> my_array.map do |value|
    value * value
  end
=> [1, 4, 9]

> my_array
=> [1, 2, 3]

# --OR--

# Block with {}
> my_array.map { |value| value * value }
=> [1, 4, 9]

> my_array                   
=> [1, 2, 3]
```
Note the original array is untouched. To modify the original array use the bang operator.

```ruby
> my_array = [1, 2, 3]

> my_array.map! do |value|
    value * value
  end
=> [1, 4, 9]

> my_array
=> [1, 4, 9]
```


## Challenges

- Write a loop that prints the numbers 1 to 20.
- Write a loop that prints the numbers 1 to 20 using a different approach than previously used.
- Write a loop that prints only even numbers from 20 to 0.
- Create a method that takes in an array of numbers and returns a new array with all the numbers multiplied by 5.
- Create a method that takes in an array of lowercase words and capitalizes all of the words, permanently modifying the original array.
- Create a method that takes in an array of numbers and returns the largest number in the array.
- Create a method that takes in an array of numbers and returns the smallest number in the array.
- Create a method that takes in an array of numbers and returns only the odd numbers sorted from least to greatest.
- Create a method that takes in an array of strings and returns all the strings in reverse casing. All uppercased letters should be returned lowercased and all lowercased letters should be returned uppercased.
- Create a method that takes in an array of words and returns all the words that start with a particular letter. Ex) Given the array ['Apple', 'Avocado', 'Banana', 'Mango'] and the letter 'a' the method should return ['Apple', 'Avocado']. With the same method, given the letter 'm' should return ['Mango'].

### FIZZBUZZ
- Write a method that prints the numbers from 1 to 100. For multiples of three print Fizz instead of the number, for multiples of five print Buzz instead of the number, for numbers that are multiples of both three and five print FizzBuzz, for all other numbers print the number.

---

# Lecture Notes

### Overview
- There are many built in methods used for iteration in Ruby
- Some of these built in methods take additional information, similar to higher-order functions in JavaScript
- Blocks are defined by the keywords `do` and `end`

### Process
- Ensure you are in the cohort-lecture-examples repo
- Ensure your local is up to date and there are no stale branches
- Create a new branch
- Create a Ruby file with the naming convention `language-topic.rb`
- Run the file with `ruby`

### Additional Notes and Goals
- Overview different approaches to iteration in Ruby

### Major Takeaways
- Revisit iteration
- Blocks are Ruby anonymous functions that are passed to a method
- Blocks provide iteration methods more context

### Lecture
Iteration is the process of repeating a code action until a condition is met. In this section we are going to talk about different types of iteration in Ruby.

#### While
While is a keyword in Ruby. A while loop performs iteration. While just executes code until a condition is met. In this example we can print a list of numbers from 1 to 10.
- `while` needs and end to define its scope
- `while` takes a condition
- The logic goes inside the while loop
- Print the num and redefine the variable to increment by one so that eventually the while condition becomes false
- Collect the values in an array using the shovel operator

```ruby
while  # step one - define the while loop
end

num = 1  # step two - define a variable and give the while loop a condition
while num <= 10
end

num = 1  # step three - print the number and increment
while num <= 10
  p num
  num += 1
end

nums = []  # step four - shovel the values into an array
num = 1
while num <= 10
  nums << num +=1
end
p nums
```

#### Blocks
Ruby has lots of built in methods for different types of iteration. And when we are using a method for iteration we need to pass the method some info. When you pass info to a method, the info is called a block. A block is an anonymous function. It modifies the behavior of the method. This is very much like when you pass a function to the map or filter method in JavaScript. It is a function that gets passed to a method.

Blocks can be defined two ways: using the key words do/end or with curly braces. Generally speaking, the do/end should be used if the block is more than one line of code. Curly braces are used for code that can be written in one line.

#### Each
```ruby
```

#### Blocks
```ruby
```
### Review

### Next Steps
- Open the syllabus section and briefly run through the challenges and expectations
- Remind the student to use the `ruby-challenges` repo
- Remind the students of the appropriate naming conventions for their branch and file
- Post pairs in Slack
- Open breakout rooms with ability for participants to choose their room

---
[Back to Syllabus](../README.md#unit-four-ruby)
