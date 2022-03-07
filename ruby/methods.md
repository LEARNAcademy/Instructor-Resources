# Ruby Methods

## Overview
- Methods are used to create customized bits of functionality that can be called as many times as we need
- Ruby methods can take any number of arguments

## Learning Objectives
- Using Ruby syntax to create a simple method
- Passing arguments to a Ruby method
- Calling a method and logging an outcome to the terminal

## Vocabulary
- def/end
- Implicit return

## Additional Resources
- <a href="https://www.w3resource.com/ruby/ruby-methods.php" target="blank">Ruby Methods</a>

#### Process
- `cd` into the `ruby-challenges` repository
- Create a new branch: `methods-initials1-initials2` (ex. methods-aw-sp)
- `touch` a file with no spaces and `.rb` extension: `methods-student1-student2.rb` (ex. methods-austin-sarah.rb)
- Open the folder in a text editor
- Code!

---

## Method Syntax

To create methods in Ruby we use the keywords `def` and `end`.

`def` stands for defines. `def` is followed with the name of the method. The block of code ends with the keyword `end`. In between is the code to be executed.

Example:
```ruby
# defines a method called greeter
def greeter
  "Hello World!"
end
```

Now we can call the method repeatedly by referencing the name `greeter`.

In IRB:
```
>greeter
Hello World!
=>nil

>greeter
Hello World!
=>nil

>greeter
Hello World!
=>nil
```

## Implicit Return
Ruby has an implicit return, which means the value of the last line of a method is automatically returned without using the keyword `return`.


## Local Variables
When defining methods with variables within them, those variables stay local to that method.

```ruby
def fun_message
  response = "This is so much fun"
  puts response
end

> fun_message
This is so much fun
=> nil

> response
  NameError
```

## Method with Parameters
Methods can also take parameters:

```ruby
def greeter name
  "Hello, #{name}!"
end

> greeter 'LEARN Student'
=> "Hello, LEARN Student!"
```

While Ruby doesn't require parentheses around the arguments for a method, it is best practice to use parentheses if there is more than one argument.

```ruby
def add(num1, num2)
  num1 + num2
end

> add 1, 3
=> 4

> add(1, 2)
=> 3
```


## Challenges

- Create a method called sum_these_numbers which takes two integers as an argument and prints their sum to the screen.
- Create a method called is_even, which takes a single integer, and which then returns true if the number is even, and false otherwise.
- Create a method that takes a number as an argument and prints "Valid" if the number is between 1 and 10 (inclusive) and "Invalid" otherwise.
- Create a method that takes in a string and determines if the string is a palindrome.


## Challenge: Password Checker

### User Stories

You are writing the user registration page for a secure web site.
On the registration page, the user has to enter a user ID and a password, which has to adhere to the to following criteria:

- As a developer, I can create a method that checks for the following rules for a user ID and password:
  - User ID and password _cannot_ be the same.
  - User ID and password _must_ be at least six characters long.
  - Password _must_ contain at least one of: !#$
  - User ID _cannot_ contain the following characters: !#$ or spaces
  - Password _cannot_ be the word "password".

### User Stories: Stretch

- As a user, I can enter my user ID and password into the terminal after being prompted to find out if the they are acceptable.

### User Stories: Super Stretch

- As a developer, my method ensures that the user's password _must_ contain at least one number.

---

# Lecture Notes

### Overview
- Ruby methods are custom logic that can take inputs and will always produce outputs

### Process
- Ensure you are in the cohort-lecture-examples repo
- Ensure your local is up to date and there are no stale branches
- Create a new branch
- Create a Ruby file with the naming convention `language-topic.rb`
- Run the file with `ruby`

### Additional Notes and Goals
- The `puts` or `p` should always be on the invocation not on the inner working of the method

### Major Takeaways
- Every `def` needs a corresponding `end`
- Ruby has an implicit return
- Methods must be invoked

### Lecture
Everything in Ruby is an object which is an instance of a class. If everything is an object, that means that all functions are technically methods. Just like in JavaScript we need to be able to define custom methods that take an input and produce an output. Talking about custom methods is basically the same thing we talk about when we say "creating a function to do x, y, z" in JavaScript.
- When you create a method in Ruby, you define it
- `def` is a keyword in Ruby
- `def` is short for define
- Every `def` needs a corresponding `end`

#### Method Syntax
The most simple method we can create will just return a line of code. The method won't do anything until it is invoked. Note that there isn't a return. In JavaScript if we didn't use the keyword return, we would get back undefined. While there is a `return` keyword in Ruby, we don't have to use it. Ruby will automatically return the last line of every method unless we say otherwise. That is called an implicit return.

```ruby
def greeter  # step one - define the method
end

def greeter  # step two - add a string
  'Hello World!'
end

p greeter  # step three - invoke the method
```

#### Methods with Arguments
Okay so let's add a parameter to our method. Of course, if we are creating custom methods we probably want to pass in information. We can do that by adding a parameter.

```ruby
def greeter name
  "Hello #{name}!"
end
p greeter
```

It is not necessary to use parentheses around the parameters. But it is a good practice. It is definitely a good practice to use parentheses if there are multiple parameters.
- Create a method that takes in two numbers
- Return the numbers multiplied

```ruby
def multiply(num1, num2)
  num1 * num2
end
p multiply(3, 7)
```

#### Methods with Conditional Logic
Often we need to add more logic into a method. We can create a method that decides which number is greater.
- Every `def` needs an `end`
- Every `if` needs an `end`

```ruby
def greater_num(num1, num2)
  if num1 > num2
    "#{num1} is greater"
  elsif num1 < num2
    "#{num2} is greater"
  else
    "#{num1} and #{num2} are equal"
  end
end
p greater_num(27, 22)
p greater_num(6, 27)
p greater_num(42, 42)
```

#### Getting User Input
So as a final step, let's get the user input from the terminal rather than from our program. We can create a method that asks a user for their name and age. Then it will give a customized answer to whether the user is old enough to vote.
- Content from the terminal is always going to be a string
- Need to modify the the age to be a number

```ruby
puts 'Enter Your Name'
user_name = gets.chomp
p user_name

puts 'Enter your Age'
user_age = gets.chomp
p user_age
p user_age.class

user_age = gets.chomp.to_i

def can_you_vote(name, age)
  if age >= 18
    "Hi #{name}. #{age} is old enough to vote"
  else
    "Hi #{name}. #{age} is not old enough to vote"
  end
end
p can_you_vote(user_name, user_age)
```

### Review
- What is def?
- What is implicit return?
- Where does the `p` and the `puts` belong in the method?
- What data type will the `gets` method return?

### Next Steps
- Open the syllabus section and briefly run through the challenges and expectations
- Remind the student to use the `ruby-challenges` repo
- Remind the students of the appropriate naming conventions for their branch and file
- Post pairs in Slack
- Open breakout rooms with ability for participants to choose their room

---
[Back to Syllabus](../README.md#unit-four-ruby)
