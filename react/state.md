# React State

- [Challenges](#challenges)
- [Lecture Notes](#lecture-notes)

#### Overview
JavaScript classes manage both data and behavior. In a React class component, the data is managed in a special object called state. State can be updated via class methods and therefore change what appears in the browser.

#### Previous Lecture (1 hour, 3 min)
[![YouTube](http://img.youtube.com/vi/n1UHz9dD9Ds/0.jpg)](https://www.youtube.com/watch?v=n1UHz9dD9Ds)

#### Learning Objectives
- can define React state
- can demonstrate JavaScript syntax in the JSX return
- can demonstrate the setState syntax to update the state object
- can create a React component with a constructor method and state object
- can make decisions on the flow of information in a component by identifying the points in which stateful components re-render

#### Vocabulary
- state
- setState()
- constructor method
- dumb/pure/display component
- smart/impure/logic component

#### Process
- `cd` into the `react-challenges` repository
- Create a new branch: `state-initials1-initials2` (ex. state-aw-sp)
- Create a new React application with no spaces: `yarn create react-app state-student1-student2` (ex. yarn create react-app state-austin-sarah)
- `cd` into the project
- Open the project in a text editor
- Create a directory in *src* called *components*
- Code!

#### Useful Commands
- $ yarn create react-app app-name
- $ yarn start
- control + c (stops the server)
- control + t (opens a new terminal tab)

#### Troubleshooting Tips
- Is your server running?
- Are your components imported and exported?
- What is your error message telling you?
---

### React State
Everything in React is a component. Components can be broken down into two basic categories: components that hold state and components that do not hold state.

But what is state?

**State** is an object that stores a component's data that determines how the component renders and behaves.

To make a component dynamic, the value of state must often be changed by the application. To change the value of state we use a JavaScript method called **setState()**. You should never manipulate state directly. The React DOM will re-render every time you call `this.setState` and update the component.

The state object lives inside the **constructor method**. Just like in regular JavaScript classes, the constructor method runs automatically when we instantiate a class. Because this class is a React component, this makes the constructor a React lifecycle method used for creating data that belongs to the class.

If a component is holding data in a state object it is referred to as a **logic component**. Other, interchangeable names for a logic component are a smart component or an impure component. If a component does not hold state it is considered a **display component**. Other terms for display components are dumb components or pure components. It is important to make the distinction as we want to streamline the data flow in our apps and be able to fix any issues quickly.

### Counter Example

Here is an example that creates a simple counter in React.

**src/App.js**

```javascript
import React, { Component } from 'react'
import Counter from './components/Counter'

class App extends Component {
  render() {
    return (
     <Counter />
    )
  }
}

export default App
```

We imported counter and called a Counter component in the return section. Now we will create the Counter component. Our Counter component will hold state, making it a logic component.

**src/components/Counter.js**

```javascript
import React, { Component } from 'react'

class Counter extends Component {
  constructor(props){
    super(props)
    this.state = {
      count: 0
    }
  }

  render(){
    return(
      <div>
        <h2>Counter: {this.state.count}</h2>
      </div>
    )
  }
}

export default Counter
```

Notice that we created a constructor, passed in props and also called super and passed in props. We will learn more about props soon, but for now let's focus on the state object which is called with `this.state` and set equal to an object with one key:value pair. The key in the object is a symbol called `count` and the value is initially set as 0.

We then see a render method and a return. In the return section we are displaying the value of our state object by calling `this.state.count` which references the value of the `count` key in the state object.

We can simplify this slightly with object destructuring.

**src/components/Counter.js**

````javascript
import React, { Component } from 'react'

class Counter extends Component{
  constructor(props){
    super(props)
    this.state = {
      count: 0
    }
  }

  render(){
    let {count} = this.state

    return(
      <>
        <h2>Counter: {count}</h2>
      </>
    )
  }
}

export default Counter
````

In the render section we destructure the count out of the state object by setting the count equal to `this.state` and then use the new variable count in the return.  

Next, we will create a button to increase the value of the counter by one per click. The button will have an `onClick` attribute that calls a method named `handleChange`.

**src/components/Counter.js**

````javascript
import React, { Component } from 'react'

class Counter extends Component{
  constructor(props){
    super(props)
    this.state = {
      count: 0
    }
  }

  render(){
    let {count} = this.state

    return(
      <>
        <h2>Counter: {count}</h2>
        <button onClick={this.handleChange}>
          Press Me!
        </button>
      </>
    )
  }
}

export default Counter
````

Now let's create our `handleChange` function so our application knows what to do when the button is pressed.

**src/components/Counter.js**

````javascript
import React, { Component } from 'react'

class Counter extends Component{
  constructor(props){
    super(props)
    this.state = {
      count: 0
    }
  }

  handleChange = () => {
    let newCount = this.state.count + 1
    this.setState({count: newCount})
  }

  render(){
    let {count} = this.state

    return(
      <>
        <h2>Counter: {count}</h2>
        <button onClick = {this.handleChange}>
          Press Me!
        </button>
      </>
    )
  }
}

export default Counter
````

The handleChange function takes `this.state.count` and adds one to the value then saves the new value in a variable called `newCount`. By calling `this.setState()` and setting the state object key `count` to our `newCount` variable.

Now we have a fully functioning button that increments by one every time the button is pressed and displays the current count.

Now the power of React begins to emerge because back on our App component, we can add multiple Counter component calls and see all of them on the page operating independently of one another! App is a display component, as its only job is to render information in the browser.

**src/App.js**

````javascript
import React, { Component } from 'react'
import Counter from './components/Counter'

class App extends Component{
  render(){
    return(
      <>
        <Counter />
        <Counter />
        <Counter />
        <Counter />
      </>
    )
  }
}

export default App
````

---
### Challenges

#### Color Box: User Stories
- As a user, I can see a white square on the screen
- As a user, when I click on the square the name of a color appears in the box
- As a user, each time I click the box I see a new color name
- As a user, I can cycle through a list of color names, one per click - green, blue, yellow, red, purple, orange
- As a user, when I click the box, the background changes to match the name of the color name displayed in the box
- As a user, I can see many color boxes on the page all acting independently of one another

#### Stretch
- As a user, I can see a button to add or remove color boxes
- As a user, when I click the add button, I can add one colorbox that acts independently of the other colorboxes
- As a user, when I click the remove button, I can remove one colorbox

---

# Lecture Notes

### Overview
- A React application is a collection of components
- Components are classes that incorporate both logic and markup
- The logic comes as JavaScript code and the mark up is called JSX

### Goals
- Modeling git workflow putting a React app inside a shared repo
- Review of basic React class components structure
- Adding a constructor and state object
- Adding logic to a React class component
- Invoking a component multiple times creating multiple instances of a single class that operate independently
- Discuss the syntax differences of inline styling in JSX vs HTML

### Major Takeaways
- Constructor and state object syntax
- Placement of constructor, logic, and render inside a React class component
- `setState()` method

### Lecture
- Create a branch
- Create a React app with no spaces in the name
- `cd` into the project
- Run the app with `yarn start`

#### Review of React Anatomy
Let's start out by reviewing the basic structure of a React class component. Have the class walk through what is needed in order to put Hello World in the browser.

```javascript
import React, { Component } from 'react'

class App extends Component {
  render() {
    return(
      <>
        <h2>Hello World</h2>
      </>
    )
  }
}
export default App
```

And what is happening here?
- We have an import that gives us the good stuff from mother React
- We have a class that is inheriting from React Component
- We have a render, which is a method that is specific to React class components
- We have a return from that render method, just like any other method in JavaScript, we want to return something
- But in React what we return is exactly one item of JSX
- And it is a great practice to have that one thing that gets returned be a React Fragment which are noted by empty opening and closing tags
- Nested between the empty tags we can add as many additional tags as we want
- Then we have an export that makes this class findable to the rest of the project

#### Running App Example
For this example, I am making a very simple app that is going to log of the number of miles I run per month. I want to be able to see the current number of miles and add miles to the current number.

#### Starting with Markup
Start out with adding some basic static data. See a header, the current number of miles, and a button that can increase the miles by one.
```javascript
class App extends Component {
  render() {
    return(
      <>
        <h2>Mile Tracker</h2>
        <p>Miles: 0</p>
        <button>Add a mile</button>
      </>
    )
  }
}
```

#### State Object
We need a place to store the miles. We need to maintain a running total of miles that can be updated every time we click the button. Right now I have a hard coded 0. Eventually we are going to replace that 0 with a class variable that can reflect the changes in the miles.

Class variables are stored in the constructor. We know the constructor is a method that runs automatically when the component is invoked. In React there is a very particular way that we create class variables. It is called state. State is an object that holds as many key value pair as needed. The values in the state object can be made available to the entire class.

```javascript
constructor(props){
  super(props)
  this.state = {

  }
}
```

This setup is exactly, exactly what you will write when you are adding state to a component. The keys and values that get added to state will depend on what your application needs. Our application needs to store miles. So we will create a key:value pair of miles and set an initial value of 0.

Now if I want to log the value of our state object what would I need to write in this console log to access the value.

```javascript
constructor(props){
  super(props)
  this.state = {
    miles: 0
  }
}
```
`this.state` is the name of the object and `miles` is the key that holds the value of 0.

To see this value in action we can log `this.state.miles` inside the render before the return. Inspecting the page will show the value.

#### Passing Class Variables in JSX
Instead of hard coding the value of 0 in our JSX we can reference the state value. We have `this.state.miles` logged in JavaScript. We need to reference it down in JSX land. If I put `this.state.miles` inside the JSX tag it just treats those characters like innerHTML.

```javascript
render() {
  console.log(this.state.miles)
  return(
    <>
      <p>Miles: this.state.miles</p>
      <button>Add a mile</button>
    </>
  )
}
```

This isn't what we want. We need to tell our program to read this as JavaScript. So to do that I have to wrap this variable name in curly braces. The curly brace indicate that we are escaping out of JSX and using passing in JavaScript code.

```javascript
render() {
  console.log(this.state.miles)
  return(
    <>
      <p>Miles: {this.state.miles}</p>
      <button>Add a mile</button>
    </>
  )
}
```

So now I see 0 but it is coming from state rather than from a hard coded 0 in the JSX. And if I change the value in state, I get a repaint that updates the DOM and changes the view.

#### Updating State with Logic
The button needs to add a mile every time it gets clicked. Updating the number of miles is an action. The button will have behavior. And in order to create behavior means we need to create a function.

The functions we write that produce behavior specific to our app live between the constructor and the render. Think of your class components as having three parts. Constructor at the top, custom logic function in the middle, render at the bottom. The only one that is vital to put content on the page is the render. The other parts are for preforming logic.

Our function is going to take the current value of miles and add one. We need to update the value of that particular key in state. We also need to ensure React recognizes the change and updates its view appropriately. So because of this React has a hard and fast rule: you don't update state directly. React has a special method called `setState()` whose job is to set and update the values in the state object. And since it is a method that is being called in the context of the class, we will use our old friend 'this'.

```javascript
addMile = () => {
  this.setState()
}
```

`setState()` is designed interact with the state object. Inside `setState()` we are passing an object with the key we want to update, in our case miles. And the new value. In our case, we want to increase the value by one. So if I want to reference the value, we will do that the same way we did it other places in the app and add one.

```javascript
addMile = () => {
  this.setState({miles: this.state.miles + 1})
}
```

`setState()` is the output of our function. So we can think of `setState()` as the return in a React function. Just like return there should only be one `setState()` and when we hit that line the function action is done.

#### Adding the Button Action
Just like any function, it is not doing anything until it gets called. And we want to call our function when the button gets clicked. So we need an onClick attribute.

Button is a JSX tag that is almost exactly like an HTML button tag. And the HTML button tag can take attributes. Meaning we can add information inside the opening tag that modifies the behavior of the tag. `onClick` is the attribute and it is followed with an equal sign and a value. But in this case the value is JavaScript, so we need our curlies. And inside the curlies we need to call the function here that belongs to the class and we are inside the context of our class, so we need to use `this`

```javascript
render() {
  return(
    <>
      <p>Miles: {this.state.miles} </p>
      <button onClick={this.addMile}>Add a mile</button>
    </>
  )
}
```

Now we have a working app!

#### Creating Multiple Trackers
But If I want to keep track of my miles run per month, I need more than one tracker. We are going to do a big refactor here. So take this in, take a screen shot, whatever you want to do. We are going to tear this apart. We are going to move all this logic into another component.

App.js is the highest level component. It is the class that puts everything else on the page. We are going to group all the other components we create into another folder. This is just a convention to keep our files organized. Inside of `src` we are going to create a new folder called components. And inside of components, we will create a file called Tracker.js

Tracker.js is uppercase because it is a nice convention to name the file exactly the same as the class. Just like App.js is the name of the file and the name of the class.

Cut everything and move it over.

To do that, we need two things. One is a component call.

```javascript
import React, { Component } from 'react'

class App extends Component {
  render() {
    return(
      <>
        <h1>Mile Tracker</h1>
        <Tracker />
      </>
    )
  }
}
export default App
```

If you look in the browser you will see an error: Tracker is not defined. This is because App.js needs to know how to find the Tracker component.

import Tracker from './components/Tracker'

Now we are back to where we started, but now we have options.

```javascript
render(){
  return(
    <>
      <h1>Mile Tracker</h1>
      <h3>January</h3>
      <Tracker />
      <h3>February</h3>
      <Tracker />
      <h3>March</h3>
      <Tracker />
    </>
  )
}
```

We wrote one component and can call it as many times as we want and all of them maintain their own state.

And that is pretty cool.

#### Display vs Logic Components
Handling state is an important part of creating React apps. But you don't want every component to have state. It is important to keep the data centralized. In this example we have one component that holds state and one that does not. This is also known as creating a logic component (that holds state) and a display component (that does not).

#### Inline Styling with JSX
One last thing, to talk about. That will help you with your challenge today. And that is inline styling in JSX.

I mentioned that JSX is just like HTML most of the time. And this is one of the times it is very different. The style attribute can be added to any tag. That is the same. And just like the onClick, we need to pass JavaScript so we need our friend the curlies to escape into JavaScript. Then, once we are inside the curlies, what gets passed is key:value pairs.

```html
<button onClick={this.addMile} style={ {color: "pink"} }>Add a mile</button>
```

The key is the styling property and the value has to be a data type that JavaScript recognizes. In this case it is a string. So this is different. And most of the time we want stylings to be in the css file, but sometimes you want inline styling and today you will want inline styling.

One final hint about styling. The value has to be a data type JavaScript recognizes, but that can be stored in a variable. So I can also do this:

```javascript
class Tracker extends Component {
  constructor(props){
    super(props)
    this.state = {
      miles: 0,
      color: "pink"
    }
  }

  addMile = () => {
    this.setState({miles: this.state.miles + 1})
  }

  render() {
    return(
      <>
        <p>Miles: {this.state.miles} </p>
        <button onClick={this.addMile} style={ {color: this.state.color} }>Add a mile</button>
      </>
    )
  }
}
```

### Review
- What is the constructor?
- What is JSX?
- What is state?
- What is `setState()`?
- What is an attribute?
- When do we need to use curly braces in the JSX section?
- Where do git commands happen vs yarn commands

### Next Steps
- Open the syllabus section and briefly run through the challenges and expectations
- Remind the student to use the `react-challenges` repo
- Remind the students of the appropriate naming conventions for their branch and project name
- Remind the students that yarn commands happen at the project level and git commands happen at the repo level
- Post pairs in Slack
- Open breakout rooms with ability for participants to choose their room

---
[Back to Syllabus](../README.md#unit-two-introduction-to-react)
