# Ruby Conditionals

- [Challenges](#challenges)
- [Lecture Notes](#lecture-notes)

#### Overview
Decision structures, also called decision trees, conditional statements, or if/else statements, are fundamental to computer programming. Conditional statements are a sequence of well-defined instructions that produce a unique output based on the value of the input. Conditionals follow a flowchart-like structure.

#### Learning Objectives
- can define the syntax of a conditional statement in Ruby
- can reproduce the syntax of string interpolation in Ruby

#### Vocabulary
- if/elsif/else
- unless
- gets
- chomp
- #{}

#### Additional Resources
- [Ruby Conditionals](http://ruby-for-beginners.rubymonstas.org/conditionals.html)

#### Process
- `cd` into the `ruby-challenges` repository
- Create a new branch: `conditionals-initials1-initials2` (ex. conditionals-aw-sp)
- `touch` a file with no spaces and `.rb` extension: `conditionals-student1-student2.rb` (ex. conditionals-austin-sarah.rb)
- Open the folder in a text editor
- Code!

---

### If/Else/End

Conditionals in Ruby use the keywords `if` `else` and `end`. Simple evaluations in Ruby don't need to be wrapped in () and code blocks don't have {} so **indentation is super important**. Just like JavaScript the `else` block is a catch all and does not take an evaluation.

```ruby
my_num = 10
if my_num == 10
  puts 'Your number is 10!'
else
  puts 'Your number is not 10.'
end
```

### If/Elsif/Else/End

To add additional evaluations to an `if/else` code block, Ruby offers the keyword `elsif`. After the if statement you may use as many `elsif` statements as you want. Ending with an `else` will capture all the leftover possibilities.

```ruby
my_num = 20
if my_num == 10
  puts 'Your number is 10!'
elsif my_num < 10
  puts "#{my_num} is less than 10."
elsif my_num > 10
  puts "#{my_num} is greater than 10."
else
  puts 'Something went wrong.'
end
```

### Unless

Ruby also offers `unless` as a way to make conditional statements. `Unless` is just like if !(...). It is just like an `if` in reverse. It's a conditional statement that executes only if the condition is false instead of true.

```ruby
my_num = 10
unless my_num > 20
  puts "#{my_num} is not greater than 20."
else
  puts "#{my_num} is greater than 20."
end
```

### Input
Ruby has the unique ability to not only produce an outcome in the terminal but to take user input in the terminal. The command for user input in the terminal is an action called called `gets`. It is a bit like `prompt()` in JavaScript. And just like `prompt()` the input value from gets needs to be stored in a variable to access later.

```ruby
> puts 'Enter your name'
=> "Enter your name"

> name = gets
# gets provides a blank line that accepts user input as a string
LEARN Student
=> "LEARN Student\n"

> puts "Hello, #{name}. How are you today?"
"Hello, LEARN Student
. How are you today?"
```

The string output from `gets` includes the return character you type to enter the user input. Ruby has a command called `chomp` that removes any additional line breaks and white space from the end of a string.

```ruby
> puts 'Enter your name'
=> "Enter your name"

> name = gets.chomp
=> "LEARN Student"

> puts "Hello, #{name}. How are you today?"
=> "Hello, LEARN Student. How are you today?"
```

## Challenges

Rock, Paper, Scissors

**Story**: As *user 1*, I can see a prompt in the terminal asking me to type either "rock", "paper", or "scissors".

**Story**: As *user 2*, I can see a prompt in the terminal asking me to type either "rock", "paper", or "scissors".

**Story**: As a user, I can see a message in the terminal saying if *user 1* or *user 2* won the round.

**Story**: As a user, I can see a message in the terminal saying if there was a tie.

---

# Lecture Notes

### Overview
- Conditional statements create logic through evaluations that return a Boolean value
- There is only one outcome per conditional statement
- Ruby allows two-way interactions through the terminal

### Process
- Ensure you are in the cohort-lecture-examples repo
- Ensure your local is up to date and there are no stale branches
- Create a new branch
- Create a Ruby file with the naming convention `language-topic.rb`
- Run the file with `ruby`

### Additional Notes and Goals
- Indentation always matters, but it really matters in Ruby

### Major Takeaways
- Using p and puts
- Defining executable code blocks
- Syntax of Ruby conditionals - `if`, `elsif`, `else`, `end`
- Syntax of string interpolation `"#{}"`

### Lecture
Creating decisions structures is an important fundamental in performing any kind of code logic. We've seen this action in JavaScript and now we will look at the similarities and difference in creating decision structures in Ruby.

Luckily, if we understand the fundamental concepts, the small changes in syntax are very manageable. To review, a decision structure - also called a decision tree or an if statement - is a series of evaluations. Each evaluation will returns a Boolean values of true or false. If a statement is true, the corresponding code will execute and the statement will be finished. If the statement is false, no code will execute and the program will move to the next decision.

#### Ruby Conditionals
Ruby is a language that is designed to be very human readable. So there are a lot fewer curly braces than we see in JavaScript. In replacement of the curly braces, Ruby depends on indentation. As a Ruby developer, all indentations should consist of two spaces. Indentation always matters, but in really matters in Ruby.
- `if` is a keyword in Ruby
- `if` takes an evaluation that will return a Boolean value
- `end` is a keyword in Ruby
- `end` closes the code block

```ruby
if 9 + 9 == 18
  p 'the answer is 18'
end
```

- `else` is a keyword in Ruby
- Just like in JavaScript, the else statement is a catchall and does not take an evaluation

```ruby
if 9 + 9 == 19
  p 'is the answer 19?'
else
  p 'no conditions in this statement evaluated to true'
end
```

- `elsif` is a keyword in Ruby
- `elsif` takes an evaluation that will return a Boolean value
- There can be as many `elsif` statements as needed

```ruby
if 9 + 9 == 19
  p 'is the answer 19?'
elsif 9 + 9 == 20
  p 'is the answer 20?'
elsif 9 + 9 == 21
  p 'is the answer 21?'
elsif 9 + 9 == 18
  p 'is the answer 18?'
else
  p 'no conditions in this statement evaluated to true'
end
```

#### User Input
Ruby has a method that will allow two-way interaction in the terminal. We are used to seeing the output of our code. In Ruby we can use the terminal to facilitate user inputs. This will make the conditional statements a little more fun.
- Start with a basic conditional statement that makes an evaluation using a variable

```ruby
my_name = 'Sarah'

if my_name == 'Sarah'
  p 'Hey there Sarah!'
else
  p "Hi there, #{my_name}"
end
```

- In order to see a different outcome, we would need to change the value of the variable
- This can be made more fun by assigning our variable through the terminal
- `gets` is a method that will stop the execution of the program and wait for you to type something and hit enter
- We can save whatever the user types into a variable
- `p` the variable and look at the output

```ruby
gets # step one - see the action in the terminal
my_name = gets # step two - saving output in a variable
p my_name
```

- Look at the output and notice the extra characters
- The `\n` is a character for a line break, typically we don't see these character but the computer sees them
- We need to remove the line break characters so they are not included in the variable
- Ruby has a method that will remove any additional characters at the end of a string
- Note that `gets` will always return a string

```ruby
p 'What is your name?'
your_name = gets.chomp
p "Thank you for being a full stacker, #{your_name}!"

my_name = gets.chomp
p my_name

if my_name == 'Sarah'
  p 'Hey there Sarah!'
else
  p "Hi there, #{my_name}"
end
```

### Review
- What are the keywords in the conditional statement?
- What are the possible outcomes of a conditional statement evaluation?
- What does `gets` do?
- What does `.chomp` do?

### Next Steps
- Open the syllabus section and briefly run through the challenges and expectations
- Remind the student to use the `ruby-challenges` repo
- Remind the students of the appropriate naming conventions for their branch and file
- Post pairs in Slack
- Open breakout rooms with ability for participants to choose their room

---
[Back to Syllabus](../README.md#unit-four-ruby)
