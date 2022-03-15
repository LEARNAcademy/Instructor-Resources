# Ruby Testing with RSpec

## Video: RSpec
[![YouTube](http://img.youtube.com/vi/NhhzRtJC8bg/0.jpg)](https://www.youtube.com/watch?v=NhhzRtJC8bg)
## Video: <a href="https://player.vimeo.com/video/168104193" target="blank">TDD and BDD with RSpec</a>

## Overview
- RSpec is the Ruby testing framework used for Test Driven Development which is best implemented using `red-green-refactor`
- RSpec is a Domain Specific Language (a language specialized for a particular task) written in Ruby
- RSpec is installed using Ruby's package manager called Rubygems

## Learning Objectives
- Exploring the syntax of RSpec
- Practicing Test Driven Development
- Exploring Ruby class inheritance

## Vocabulary
- RSpec
- TDD
- BDD
- red-green-refactor
- gem
- describe
- expect

## Useful Commands
- $ gem install rspec

## Additional Resources
- <a href="http://betterspecs.org" target="blank">Better Specs</a>, which shows tons of examples of what you should and shouldn't do with RSpec
- <a href="http://net.tutsplus.com/tutorials/ruby/ruby-for-newbies-testing-with-rspec/" target="blank">Ruby for Newbies</a>
- <a href="https://cheatography.com/dwapi/cheat-sheets/rspec-examples-with-factory-girl/" target="blank">RSpec Cheat Sheet</a>
- <a href="https://www.youtube.com/embed/fsSMuqIpu_c?ecver=2" target="blank">YouTube Video about TDD vs BDD</a>
- Here is a discussion about <a href="https://www.youtube.com/embed/GvAzrC6-spQ?ecver=2" target="blank">TDD</a> lead by Robert Martin, also known as "Uncle Bob". He's a legend in the programming world who writes extensively about software design and architecture

#### Process
- `cd` into the `ruby-challenges` repository
- Create a new branch: `rspec-initials1-initials2` (ex. rspec-aw-sp)
- Create a new directory `mkdir` rspec-student1-student2 (ex. rspec-austin-sarah)
- `cd` into the directory you just created
- `touch` a file called: `rspec.rb`
- `touch` a file called: `rspec_spec.rb`
- Add the dependencies by running $ `gem install rspec` in the terminal
- Open the RSpec folder in a text editor
- Code!

#### Fun Extra: Formatting RSpec in Terminal
To produce a more readable RSpec printout in terminal follow these steps:
- cd into your root directory (shortcut: $ `cd ~`)
- Create a new file called .rspec ($ `touch .rspec`)
- $ `open .rspec`
- Put `--color --format documentation` in the file
- Save
- Voila! Beautiful RSpec code!

---

## Test Driven Development
As you begin to write more complicated applications, you'll quickly come to realize that bugs in your code can find their way into your code in very unexpected places.  You make a small change in one place, and something seemingly unrelated breaks because of it.  Without a good set of tests for your code, you may never know it, but users always find those bugs, and that causes stress, and a rush to fix the problem, which is never a good way to develop.

The most important tool you have to assure that your code well written, and as free of bugs as possible is automated tests. Automated tests can be run over and over again, every single time you make a change, and every time they pass, you can rest assured that your code is solid, and users will have a great experience.

Over time, as you test every single piece of code that you write, you'll always have the confidence to ship your code.  If something does break, and it will, you'll know it right away and fix it before your code goes into production.

## Overview of a TDD Process

TDD stands for Test Driven Development

1. Determine a feature or behavior to implement.
2. Create the `describe` and `it` blocks pertaining to the that feature only.
3. Put in `expects` in one `it` block to assert how the objects should behave.
4. Run the tests and see that they fail (the `red` part of red-green refactor).
5. Implement just enough of the software to make the tests pass (the `green` part of red-green refactor).
6. Add more `expects` and repeat the process, until all tests pass and all features are implemented.


## Ruby Gems
A gem is library or snippet of code functionality. Gems package up Ruby code so it is easy to share with others. For this example, we ask Rubygems to install the RSpec gem using the command `gem install rspec`.

## Car Example
So far, we have a directory called `car_challenge` and two files in that directory. One for `car` and one for the tests or `specs`. Inside the spec file put the following:
- `require 'rspec'` which searches the gem file and brings in the appropriate RSpec code
- `require_relative 'car'` which connects the spec file to the `car.rb` file

Make sure RSpec is working properly by running `rspec car_spec.rb` in the terminal.

Output in the terminal:
```
No examples found.

Finished in 0.00042 seconds (files took 0.09294 seconds to load)
0 examples, 0 failures
```

### 1. Car class exists

**Test:**<br>
Write the first test within the `car_spec.rb` file.
Car has to be a thing, in other words, Car has to be a class that we can use.

```ruby
require 'rspec'
require_relative 'car'

describe 'Car' do

  it 'has to be real' do
    expect{ Car.new }.to_not raise_error
  end

end
```

There are two blocks of code in the test. The first one is the `describe` block that specifies what we are testing. In this example, we are testing the class Car.

The second one is the `it` block with a description of what will happen when a particular code snippet is run. In this example, we are expecting to be able to create a new instance of class Car.


Run your test and we should see failure.

```
Finished in 0.04241 seconds (files took 0.23341 seconds to load)
1 example, 1 failure

Failed examples:

rspec ./car_spec.rb:15 # Car has to be real
```

**Code:**<br>
Now implement a Car class in the `car.rb` file:

```ruby
class Car
end
```

And run the tests again. Do they pass? YES!

**describe "Car" vs describe Car**<br>
Now that we have a Car class we can change the test to use the class name `describe Car do` instead of the string `describe 'Car' do`.

Great. On to the next feature!

### 2. Cars have Models

**Test:**<br>
Inside the same `describe` block, we will add another `it` block. To test that Car can have a model we need to create an instance of the Car class inside the `it` block. The variable is local to that particular test.

We will set up our test to look at two things:
1. if Car can be assigned a model and return that assigned value. To accomplish this we can use the RSpec matcher `.to eq`
2. if the model method returns a String. To accomplish this we can use the RSpec matcher `to be_a` and pass the class name String.

```ruby
require 'rspec'
require_relative 'car'

describe Car do

  it 'has to be real' do
    expect{ Car.new }.to_not raise_error
  end

  it 'has a model' do
    my_car = Car.new
    my_car.model = 'Toyota'
    expect(my_car.model).to be_a String
    expect(my_car.model).to eq 'Toyota'
  end

end
```

Notice there is a difference between the expect statements in our first and second test. The first one has curly braces and the second one has parentheses. Using parentheses is testing for a value. In this case, we are expecting our car's color to have a value that belongs to the class of String. In the first `it` block, we are passing a block of code `{ Car.new }` to test behavior. The behavior we expect is for the creation of a new object from the Car class.

$ rspec car_spec.rb

```
Failures:

  1) Car has a model
     Failure/Error: my_car.model = 'Toyota'

     NoMethodError:
       undefined method `model=' for #<Car:0x00007fa0d891b038>
     # ./car_spec.rb:21:in `block (2 levels) in <top (required)>'

Finished in 0.00597 seconds (files took 0.25876 seconds to load)
2 examples, 1 failure

Failed examples:

rspec ./car_spec.rb:19 # Car has a model
```
Our test fails. Yay!

**Code:**<br>

We will write just enough code to get our test to pass.

```Ruby
class Car
  def model=car_model
    @model = car_model
  end
  def model
    @model
  end
end
```

Now our Car class has a setter and a getter method for the Car model.

$ rspec car_spec.rb

```
Finished in 0.01088 seconds (files took 0.2373 seconds to load)
2 examples, 0 failures
```

### 3. A Car's color
Our Car can be assigned a color on initialization. If no color is given a Car should be 'unpainted' by default. The Car's color should always be a String.

This challenge is going to require two different test cases. One if the car is given a color and another if it is not. We will create two different variables and test each outcome.

**Test:**<br>
```ruby
  it 'can be given a color or be unpainted by default' do
    my_car = Car.new
    expect(my_car.color).to eq 'unpainted'
    expect(my_car.color).to be_a String
    my_red_car = Car.new 'Red'
    expect(my_red_car.color).to eq 'Red'
  end
```

$ rspec car_spec.rb
```
Failures:

  1) Car can be given a color or be unpainted by default
     Failure/Error: expect(my_car.color).to eq 'unpainted'

     NoMethodError:
       undefined method `color' for #<Car:0x00007fb86a224af0>
     # ./car_spec.rb:28:in `block (2 levels) in <top (required)>'

Finished in 0.0119 seconds (files took 0.38226 seconds to load)
3 examples, 1 failure

Failed examples:

rspec ./car_spec.rb:26 # Car can be given a color or be unpainted by default
```

**Code:**<br>
```ruby
class Car

  def initialize color='unpainted'
    @color = color
  end

  def color
    @color
  end

  def model=car_model
    @model = car_model
  end

  def model
    @model
  end

end

```
$ rspec car_spec.rb
```
Finished in 0.01098 seconds (files took 0.27763 seconds to load)
3 examples, 0 failures
```

And now our tests pass!

### 4. The need for Speed
Our Car should be able to accelerate, decelerate, and tell us its current speed. Speed should be Numeric and start with a default value of 0. Ruby's Numeric class is a broad class that includes Fixnum ad Integer.

Let's break this problem down into three parts: current speed starting at 0, acceleration, then deceleration.

#### Current Speed Starting at 0

**Test:**<br>
```ruby
it "has a speed" do
  my_car = Car.new
  expect(my_car.speed).to be 0
  expect(my_car.speed).to be_a Numeric
end
```

$ rspec car_spec.rb

```
Finished in 0.00923 seconds (files took 0.31426 seconds to load)
4 examples, 1 failure

Failed examples:

rspec ./car_spec.rb:34 # Car has a speed
```

**Code:**<br>
```ruby
def initialize color='unpainted', speed=0
  @color = color
  @speed = speed
end

def speed
  @speed
end
```

#### Acceleration

**Test:**<br>
```ruby
# One way to test using values:
it "can accelerate by an amount" do
  my_car = Car.new
  my_car.accelerate 10
  expect(my_car.speed).to be 10
end

# Alternative way to test using behavior:
it "can accelerate by an amount" do
  expect{ my_car.accelerate 10 }.to change{ my_car.speed }.from(0).to(10)
  expect{ my_car.accelerate 20 }.to change{ my_car.speed }.from(10).to(30)
end
```

**Code:**<br>
```ruby
def accelerate increase_by
  @speed = @speed + increase_by
end
```

#### Deceleration
Decelerate is very similar to the accelerate test, but in order to decelerate we have to have a starting speed. The other thing to consider with decelerate is ensuring we don't get into negative speeds.

**Test:**<br>
```ruby
it "can decelerate by an amount" do
  my_car = Car.new
  my_car.accelerate 20
  expect{ my_car.decelerate 10 }.to change{ my_car.speed }.from(20).to(10)
  expect{ my_car.decelerate 20 }.to change{ my_car.speed }.from(10).to(0)
end
```

**Code:**<br>
```ruby
def decelerate decrease_by
  if @speed >= decrease_by
    @speed = @speed - decrease_by
  else
    @speed = 0
  end
end
```

### 5. The Garage
Let's create another class called Garage to store all of our Cars. Since Garage is a new class it will get its own `describe` block.

**Test:**<br>
```ruby
describe 'Garage' do

  it 'has to be real' do
    expect{ Garage.new }.to_not raise_error
  end

end
```

**Code:**<br>
```ruby
class Garage
end
```

**describe "Garage" vs describe Garage**<br>
Now that we have a Garage class we can change the test to use the class name `describe Garage do` instead of the string `describe 'Garage' do`.


## Challenge: Tasklist with TDD

#### For each story:

- Copy the story into your RSpec file as a comment
- Write the test(s) that class/method tests must pass
- Then run the test(s) and see that they fail
- Then implement the class/method, with comments, so that it passes the tests one at a time

### User Stories

**Story:** As a developer, I can create a Task.

**Story:** As a developer, I can give a Task a title and retrieve it.

**Story:** As a developer, I can give a Task a description and retrieve it.

**Story:** As a developer, I can mark a Task done. Tasks should be initialized as 'in progress'.

**Story:** As a developer, when I print a Task that is done, its status is shown.

**Story:** As a developer, I can add all of my Tasks to a TaskList.

**Story:** As a developer with a TaskList, I can print the completed items.

**Story:** As a developer with a TaskList, I can print the incomplete items.

### Stretch: Due Date

**Story:** As a developer, I can give a Task a due date.
**Hint:** Use the built-in Ruby Date class.

**Story:** As a developer with a TaskList, I can list all the not completed items that are due today.

**Story:** As a developer with a TaskList, I can list all the not completed items in order of due date.

**Story:** As a developer with a TaskList with and without due dates, I can list all the not completed items in order of due date, and then the items without due dates.

---

# Lecture Notes

### Overview
- Test-driven development is the process of creating tests first, seeing the test fail, then creating the code to make the test pass
- RSpec is a testing language for Ruby
- RSpec stands for Ruby specifications or specs
- RSpec is installed via RubyGems which is a package manager for Ruby
- Tests should only look at the output of the code, not the inner logic

### Process
- Ensure you are in the cohort-lecture-examples repo
- Ensure your local is up to date and there are no stale branches
- Create a new branch
- Create a folder called `ruby-rspec`
- Create a Ruby file called `rspec_book.rb`
- Create a Ruby spec file called `rspec_spec.rb`
- Run the tests with `rspec rspec_spec.rb`

### Additional Notes and Goals
- Looking the similarities between Jest and RSpec

### Major Takeaways
- Practicing TDD
- RubyGems or gems are a package manager for Ruby
- RSpec syntax
- Difference between expect statements with `{}` or `()`

### Lecture
RSpec is a Domain Specific Language which is a language that has been specialized for a particular task. In this case RSpec is specialized for testing Ruby code.

TDD which stands for test-driven development, is a developer philosophy of writing tests (or specs, short for specifications) first and then creating the code that will make the tests pass. TDD is closely associated with the phrase `red-green-refactor`. Which means we will write our tests first and see them fail (red), the write the code to make it pass (green), then if we need to do any refactor or make any edits on the code, then we can do so with confidence.

#### RSpec Installs and Setup
For this example we are going to create a class for Book. Book is going to be a template from which we can create many instances of books. The Book class will have both data and behavior. A book can have a title, an author, and pages which are all data. And we can read a book change the current page we are on. That is an action, or a behavior, which in development we call them methods.

We are going to have two files. One is going to have the Ruby code and one is going to have the tests.
- Google: ruby gem rspec and look at the https://rubygems.org/gems/rspec/versions/3.4.0 documentation for the number of downloads for RSpec
- $ `gem install rspec`
- Set imports
- Add `describe` block with a do/end block
- Add `it` block with a do/end block
- Add expect statement that will run the new method and expect the creation of a class
- Run the tests with `rspec rspec_spec.rb`
- Look at the failing test

```ruby
# rspec_spec.rb

# require the rspec tools
require 'rspec'
# require the file that contains the code
require_relative 'rspec_code'


describe 'Book' do
  it 'has to be real' do
    expect{ Book.new }.to_not raise_error
  end
end
```

- Add the code that will make the test pass

```ruby
# rspec_book.rb

class Book
end
```

#### Book Should Have a Title
Now we want to be able to have our Book class have some static data.
- Add an additional `it` block to the test
- Create an instance of Book
- Call a setter method to give Book a title
- Expect the outcome
- This expect has parentheses because the outcome is data, curly braces are used when the outcome is behavior
- Run the tests with `rspec rspec_spec.rb`
- Look at the failing test

```ruby
# rspec_spec.rb

it 'has a title' do
  my_book = Book.new
  my_book.title = 'Catch-22'
  expect(my_book.title).to be_a String
  expect(my_book.title).to eq 'Catch-22'
end
```

- Add the code that will make the test pass
- Can use an initializer to create the variable on instantiation
- `attr_accessor` will give us getter and setter methods

```ruby
# rspec_book.rb

class Book
  attr_accessor :title
  def initialize
    @title = title
  end
end
```

#### Book Should Have an Author
If there is no author we can have a default value of anonymous.
- Add an additional `it` block to the test
- Create an instance of Book
- Book should have a default author of anonymous
- Expect the outcome
- This expect has parentheses because the outcome is data, curly braces are used when the outcome is behavior
- Update Book to have an author
- Expect the outcome
- Run the tests with `rspec rspec_spec.rb`
- Look at the failing test

```ruby
# rspec_spec.rb

it 'has an author' do
  my_book = Book.new
  expect(my_book.author).to eq 'anonymous'
  expect(my_book.author).to be_a String
  catch22 = Book.new 'Joseph Heller'
  expect(catch22.author).to eq 'Joseph Heller'
end
```

- Add the code that will make the test pass

```ruby
# rspec_book.rb

class Book
  attr_accessor :title, :author
  def initialize author='anonymous'
    @author = author
    @title = title
  end
end
```

#### Book Should Have a Current Page
A new instance of book will always start with the page at 1.
- Add an additional `it` block to the test
- Create an instance of Book
- Expect the outcome
- This expect has parentheses because the outcome is data
- Run the tests with `rspec rspec_spec.rb`
- Look at the failing test

```ruby
# rspec_spec.rb

it 'can report the current page' do
  my_book = Book.new
  expect(my_book.page).to eq 1
  expect(my_book.page).to be_a Integer
end
```

- Add the code that will make the test pass

```ruby
# rspec_book.rb

class Book
  attr_accessor :title, :author, :page
  def initialize author='anonymous'
    @author = author
    @title = title
    @page = 1
  end
end
```

#### Reading the Book
We can add a method that will move the pages forward, we are back to looking for a behavior rather than a static output so we need different expect statements in the test.
- Google rspec change matchers: https://relishapp.com/rspec/rspec-expectations/docs/built-in-matchers/change-matcher
- Counter example in the relish docs has the syntax we are looking for
- Add an additional `it` block to the test
- Create an instance of Book
- Expect the outcome
- This expect has curly braces because the outcome is a behavior
- Run the tests with `rspec rspec_spec.rb`
- Look at the failing test

```ruby
# rspec_spec.rb

it 'can read pages' do
  my_book = Book.new
  expect{ my_book.read 10 }.to change{ my_book.page }.from(1).to(11)
end
```

- Add the method that will make the test pass

```ruby
# rspec_book.rb

class Book
  attr_accessor :title, :author, :page

  def initialize author='anonymous'
    @author = author
    @title = title
    @page = 1
  end

  def read pages_read
    @page += pages_read
  end
end
```

#### Add a Library
So now let's look at creating a collection of books. We can make another class that will handle our collection.
- Create another file called rspec_library.rb
- Need to import library in the testing file and create another describe block
- Add an `it` block to the test
- Expect the outcome
- This expect has curly braces because the outcome is a behavior
- Run the tests with `rspec rspec_spec.rb`
- Look at the failing test

```ruby
# rspec_spec.rb

require 'rspec'
require_relative 'rspec_book'
require_relative 'rspec_library'

# Other code here ...

describe 'Library' do
  it 'has to be real' do
    expect{ Library.new }.to_not raise_error
  end
end
```

- Add the code that will make the test pass

```ruby
# rspec_library.rb

class Library
end
```

#### Create a Collection of Books
We can create a collection that is a data type of Array.
- Add an additional `it` block to the test
- Create an instance of Book
- Expect the outcome
- This expect has parentheses because the outcome is a data
- Run the tests with `rspec rspec_spec.rb`
- Look at the failing test

```ruby
# rspec_spec.rb

it 'has an array of books' do
  my_library = Library.new
  expect(my_library.book_collection).to be_a Array
end
```

- Add the code that will make the test pass

```ruby
# rspec_library.rb

class Library
  attr_accessor :book_collection
  def initialize
    @book_collection = []
  end
end
```

#### Add Books
Add books to the books array.
- Add an additional `it` block to the test
- Create an instance of Library
- Create a couple instances of Book
- Expect the outcome
- This expect has parentheses because the outcome is a data
- Run the tests with `rspec rspec_spec.rb`
- Look at the failing test

```ruby
# rspec_spec.rb

it 'has an array of books' do
  catch22 = Book.new
  sherlock = Book.new
  my_library = Library.new
  my_library.add_books catch22
  my_library.add_books sherlock
  expect(my_library.book_collection).not_to be_empty
  expect(my_library.book_collection).to contain_exactly(catch22, sherlock)
end
```

- Add the code that will make the test pass

```ruby
# rspec_spec.rb

class Library
  attr_accessor :book_collection
  def initialize
    @book_collection = []
  end

  def add_books book
    @book_collection << book
  end
end
```

### Review
- What is RSpec?
- What is TDD?
- What imports are required to run RSpec?
- In which file do the imports belong?
- What is the difference between expect statements with curly braces vs parentheses?

### Next Steps
- Open the syllabus section and briefly run through the challenges and expectations
- Remind the student to use the `ruby-challenges` repo
- Remind the students of the appropriate naming conventions for their folder, branch, and file
- Post pairs in Slack
- Open breakout rooms with ability for participants to choose their room

---
[Back to Syllabus](../README.md#unit-four-ruby)
