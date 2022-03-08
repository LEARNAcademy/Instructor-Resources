# Ruby Hashes

- [Challenges](#challenges)
- [Lecture Notes](#lecture-notes)

## Overview
- A hash is a collection of unique keys and their values
- A hash is a bit like an array but instead of the values being referenced by an index, the values are reference by their unique key
- The class `Hash` falls under the category of enumerable, which means you can use iterable methods on a hash

## Learning Objectives
- Exploring the different ways hashes can be constructed
- Applying iterable methods to a hash

## Vocabulary
- Hash
- Symbol
- Hash rocket
- Enumerable
- Duck Typing

## Additional Resources
- [ Ruby Hash Docs ](https://ruby-doc.org/core-2.7.0/Hash.html)
- [ Ruby Hashes for Beginners ](http://ruby-for-beginners.rubymonstas.org/built_in_classes/hashes.html)
- [ Ruby's Magical Enumerable Module ](https://blog.appsignal.com/2018/05/29/ruby-magic-enumerable-and-enumerator.html)

#### Process
- `cd` into the `ruby-challenges` repository
- Create a new branch: `hashes-initials1-initials2` (ex. hashes-aw-sp)
- `touch` a file with no spaces and `.rb` extension: `hashes-student1-student2.rb` (ex. hashes-austin-sarah.rb)
- Open the folder in a text editor
- Code!

---

## Ruby Hashes
A hash is a container for data. The data in a hash are stored in key:value pairs.

As is common in programming, are many ways to define the keys and values in a hash. As of Ruby 2.7, the accepted syntax of creating a hash looks like this:

```ruby
recipe = { flour: "2 1/4 cups", sugar: "1 cup", eggs: 2 }
```

Looking at the output in the terminal we get this:
```
=> {:flour=>"2 1/4 cups", :sugar=>"1 cup", :eggs=>2}
```

This output illustrates an older syntax of hashes. There are two things to note with the syntax of this output:

1. The first is the data type of the key which is a Ruby **symbol**. A symbol is expressed with the colon on the left side of the variable such as `:flour`.

2. The second is the **hash rocket** that separates the key and the value. A hash rocket is this syntax `=>`. Hash rockets used to be the only way to define a value in a hash. The later versions of Ruby adopted a more JavaScript-like syntax to make the code more readable. Hash rockets are still valid Ruby code and are seen in terminal outputs so it is important to recognize the many hash syntaxes.

## Operations on a Hash

**Create**  
As we know, everything in Ruby is a class. So we can call the `.new` method on the class `Hash` to instantiate a new hash.

```ruby
> recipe = Hash.new
```

**Read**  
When we call `recipe` we can see it is an empty hash.
```ruby
> recipe
 => {}
```

**Update**  
We can add values to the hash by providing a key in square braces and assigning that key a value.

```ruby
> recipe[:flour] = "2 1/4 cups"
> recipe[:sugar] = "1 cup"
> recipe[:eggs] = 1
```

Now we can see the output of the hash with the keys and values.
```ruby
> recipe
=> {:flour=>"2 1/4 cups", :sugar=>"2cups", :eggs=> 1}
```

This same syntax can be used to update the value in a hash.

```ruby
> recipe[:eggs] = 2
=> {:flour=>"2 1/4 cups", :sugar=>"2 cups", :eggs=>2}
```

Now, what if we needed to update the name of a key? That requires a little bit more Ruby code.

```ruby
> recipe
> recipe[:buter] = "1 cup"
```

Oops, we misspelled butter. Let's update that key to be the correct spelling using this format: `hash[:new_key] = hash.delete :old_key`

```ruby
> recipe[:butter] = recipe.delete :buter
```

**Show**  
We can look at just a single value from the hash by calling its key.

```ruby
> recipe[:sugar]
=> "2 cups"
```

**Delete**  
If we want to remove a key:value pair from the hash all together we can use the Ruby method `.delete` and pass in the key as an argument. Ruby will return the value from the deleted key as an output of that method. And when we call the variable `recipe` we see the key:value pair has been removed.

```ruby
> recipe.delete(:butter)
=> "1 cup"
> recipe
=> {:flour=>"2 1/4 cups", :sugar=>"2 cups", :eggs=>2}
```

## Enumerables and Duck Typing
Everything in Ruby is an instance of a class. And each class has certain abilities. For example, class Integer has the ability to have mathematical operations performed on its instances while that is not true of NilClass.

We know that methods are functions that belong to a class. And Ruby decides which methods belong to which class based on the ability of the class (what it can do) rather than what each class is. This concept is called **Duck Typing**. "If it looks like a duck and quacks like a duck just go ahead and treat it like a duck."

The power of Duck Typing is that because Hashes share abilities with classes like Arrays and Ranges, we can use the same methods available to those classes on class Hash.

Hashes, like Arrays and Ranges, have the ability to iterate. So we can use methods such as `.each` and `.map` on Hashes.

`.each` calls a block once for each key in the hash, passing the key-value pair as a parameter.

If no block is given, an enumerator is returned instead.

```ruby
> recipe = {flour: "2 1/4 cups", sugar: "2 cups", eggs: 2, butter: "1 cup"}

> recipe.each do |key, value|
  puts "Add #{value} #{key} to the bowl."
end
```
When applied to a hash, `.each` can take two possible arguments - the key and the value. These arguments are simply placeholders used inside the do/end block.

`.each` executes once time for each key:value pair in the hash.

Output:
```
Add 2 1/4 cups flour to the bowl.
Add 2 cups sugar to the bowl.
Add 2 eggs to the bowl.
Add 1 cup butter to the bowl.
=> {:flour=>"2 1/4 cups", :sugar=>"2 cups", :eggs=>2, :butter=>"1 cup"}
```

`.map` also executes once for each key:value pair and returns an array of the same length.

```ruby
> recipe.map do |key, value|
>   "Add #{value} #{key} to the bowl."
> end
```

Output:
```
=> ["Add 2 1/4 cups flour to the bowl.", "Add 2 cups sugar to the bowl.", "Add 2 eggs to the bowl.", "Add 1 cup butter to the bowl."]
```

## Summary
- Hashes are collections of key:value pairs.
- The class Hash can be created by assigning a variable or by using the `.new` method.
- Hashes can have new key value pairs added, updated or deleted.
- Hashes have enumerable abilities allowing developer the ability to use methods such as `.each` and `.map` to iterate over the key:value pairs.

## Challenges
- As a developer, I can create a hash called my_phone using the Ruby method `.new`.
- As a developer, I can add five key:value pairs of app names and their descriptions to my hash.
- As a developer, I can return a value from my_phone by passing in the name of a key.
- As a developer, I can update two keys in my_phone.
- As a developer, I can update two values in my_phone.
- As a developer, I can delete two key:value pairs from my_phone.
- As a developer, I can use an enumerable method to return information about all of my_phone's applications.

### Stretch Challenges
- As a developer, I can create a custom method that takes in my_phone and returns an array with the app name capitalized and information about each phone app.

---

# Lecture Notes

### Overview
- Hashes are a data structure in Ruby
- Hashes are a dictionary-like collection of key:value pairs
- Hashes are very similar to JavaScript objects but also have some iterative properties

### Process
- Ensure you are in the cohort-lecture-examples repo
- Ensure your local is up to date and there are no stale branches
- Create a new branch
- Create a Ruby file with the naming convention `language-topic.rb`
- Run the file with `ruby`

### Additional Notes and Goals
- Introducing CRUD actions
- Opportunity to discuss duck-typing

### Major Takeaways
- How to access a value in a hash by referencing the key
- Symbol syntax in Ruby
- Hash rocket

### Lecture
Hashes have key:value pairs where the key is a symbols and the value is any type of data recognized by Ruby. To access the value in a hash you must reference the key.

#### Creating a Hash
There are two ways to create a hash.
- Key:value pairs inside curly braces
- The keys are the Ruby data type symbol
- The values is any data type recognized by Ruby
- Key:value sets are comma separated
- Assign the hash to a variable and print the variable
- Look at the syntax of the output

```ruby
learn_staff = {instructor: 'Austin', career: 'Jake', marketing: 'TJ'}

p learn_staff

# Output:
{:instructor=>"Austin", :career=>"Jake", :marketing=>"TJ"}
```

The output is interesting because it shows another version of the Ruby syntax. Like all languages, Ruby has gone through many iterations and has evolved over time. Writing a symbol can look like it did when we created the hash, or it can have the colon in front. When you reference a symbol it will often have the colon-first syntax. In this syntax the thing that separates the keys from the values is called a hash rocket.

The second way to create a hash is to use the Ruby method `new`. The `new` method is called on a class. It will instantiate the class. Another way of saying that is that we are going to create an instance of the class which is an object.

```ruby
my_hash = Hash.new
p my_hash
```

#### Manipulating Hashes
Generally speaking there are four actions that a develop would want to perform on a single piece of data. The first is that you want to return data, you want to read a particular piece of information. The second is create content, adding new items. The third is update existing content. And the last is delete or remove existing content.

Return all the data in the hash
```ruby
learn_staff = {instructor: 'Austin', career: 'Jake', marketing: 'TJ'}

p learn_staff
```

Return one value in the hash
```ruby
learn_staff[:marketing]
# Output:
=> "TJ"
```

Add content to the hash
```ruby
learn_staff[:boss_lady] = 'Chelsea'
p learn_staff

learn_staff[:enrollment] = 'Kumba'
p learn_staff
```

Update content in the hash
```ruby
learn_staff[:boss_lady] = 'Chelsea K'
p learn_staff

learn_staff[:instructor] = 'Austin W'
p learn_staff
```

Remove content from the hash
```ruby
learn_staff.delete(:career)
p learn_staff
```

#### Enumerables and Duck Typing
Ruby has a lot of methods. There are methods that we can call on a hash to help manipulate or return information. There is a concept in Ruby called modules. Modules are way of grouping together like things that have similar properties. One of the main modules in Ruby is called the enumerable module. The enumerable module is a grouping of things that are iterable. Hashes, arrays, and ranges all belong to the Ruby module called enumberables.

So why is this important? You'll remember from JavaScript that all built in methods have to be called on a particular data type. Map only works on arrays, toUpperCase only works on strings, as so on. In JavaScript, all methods are connected to a particular data types. But Ruby takes a different approach. Rather than limit a method to a single data type, Ruby developers decided to look at the behavior of a method and define it by its action rather than strictly by the data type it must be applied to.

This concept is called Duck Typing. The saying is, that if it walks like a duck and quacks like a duck, then you can call it a duck. So in Ruby there is a method called reverse. You can call the reverse method on a string, but it can also call it on an array. Because the behavior of reversing characters in a string and the behavior of reversing indexes in an array are basically the same thing. Ruby developers don't worry about whether reverse is a string method or an array method. They both quack like ducks.

So with that when it comes to ranges, arrays, and hashes, grouping them together under the category of enumerables means that they all quack like ducks and so we can apply a lot of the same methods to all of them.

This is a long way of saying that we can use each and map on a hash.
- When mapping a hash we have access to the key and the value in that order

```ruby
learn_staff.each do |key, value|
  p "#{value}'s job is #{key}."
end


def my_coworkers hash
  hash.map do |key, value|
    "My coworker is #{value}."
  end
end

p my_coworkers learn_staff
```

### Review
- What is a hash?
- What how do you access a value from a hash?
- What is the syntax of referencing a symbol in Ruby?
- What is duck typing?

### Next Steps
- Open the syllabus section and briefly run through the challenges and expectations
- Remind the student to use the `ruby-challenges` repo
- Remind the students of the appropriate naming conventions for their branch and file
- Post pairs in Slack
- Open breakout rooms with ability for participants to choose their room

---
[Back to Syllabus](../README.md#unit-four-ruby)
