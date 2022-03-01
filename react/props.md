# React Props

- [Challenges](#challenges)
- [Lecture Notes](#lecture-notes)

## Video: React Props
[![YouTube](http://img.youtube.com/vi/-5dtIo_oib0/0.jpg)](https://www.youtube.com/watch?v=-5dtIo_oib0)

## Overview
- Props (properties) is a keyword in React for passing information from one component to another
- Props are only passed in one direction, from parent to child
- Props cannot be updated, they are "read only"

## Learning Objectives
- Understanding how to pass data and methods to a child component through the component call
- Understanding how to access the data and methods within the child component
- Understanding the unidirectional flow of information in React

## Vocabulary
- props
- component call

#### Process
- `cd` into the `react-challenges` repository
- Create a new branch: `props-initials1-initials2` (ex. props-aw-sp)
- Create a new React application with no spaces: `yarn create react-app props-student1-student2` (ex. yarn create react-app props-austin-sarah)
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

## Communication Between Components

Since React is component based, communication between the components is very important. Where nested components gave us the ability to build modular interfaces and state gave us a means of tracking and updating data within components, props give us the ability to communicate by passing data and methods between components. Specifically, it gives us the ability to pass data down to nested components.

In a React application, props (for the most part) come from state. In a very practical sense, props are a snapshot of state that are passed on to components tasked with displaying and/or letting a user interact with that information.

Information gets passed from the parent component to the child component through the component call. It is very similar to how a function get passed information through an argument.

**src/App.js**

```javascript
import React, { Component } from 'react'
import GreetPerson from './components/GreetPerson'

class App extends Component{
  render(){
    return(
      <div>
        <GreetPerson name="Bob" />
      </div>
    )
  }
}
export default App
```
Within the `<GreetPerson />` component call we are passing a variable `name` that contains the string "Bob".

The variable is now available to the `GreetPerson` component as props.

To call `name` as props in the child component we use `this.props.name`

**src/components/GreetPerson.js**
```javascript
import React, { Component } from 'react'

class GreetPerson extends Component{
  render(){
    return(
      <h1>Hi, { this.props.name }!</h1>
    )
  }
}
export default GreetPerson
```

## Passing a Value From State as Props

Rather than hardcoding "Bob" directly in the component call, we can use the state object to pass props to the child component.

**src/App.js**
```javascript
import React, { Component } from 'react'
import GreetPerson from './components/GreetPerson'

class App extends Component{
  constructor(props){
    super(props)
    this.state = {
      personOne: "Bob",
      personTwo: "Teddy"
    }
  }
  render(){
    return(
      <div>
        <GreetPerson name={ this.state.personOne } />
        <GreetPerson name={ this.state.personTwo } />
      </div>
    )
  }
}

export default App
```

The variable `name` is assigned information from state. `name` is available to `GreetPerson` as props. The component `GreetPerson` is being called twice, each with different information from the state object.

Here we start to see the power of these mechanisms working together. We are reusing a component to display different sets of information. Using props and components can make for an extremely dynamic application.

**src/components/GreetPerson.js**
```javascript
import React, { Component } from 'react'

class GreetPerson extends Component{
  render(){
    return(
      <h1>Hi, { this.props.name }!</h1>
    )
  }
}
export default GreetPerson
```

Notice very little has changed but the potential of our application shifts dramatically. First, we added state to the App component by setting up a constructor with two values in state. Then, in the return we changed the hardcoded names to reference the items in state. In moving the values into state, we've centralized our data and made them available to any other components in the App component.

## Refactor: Mapping a Component Call

With a little refactoring and DRYing up our code using a programmatic approach, this can become even more dynamic.

**src/App.js**
```javascript
import React, { Component } from 'react'
import GreetPerson from './components/GreetPerson'

class App extends Component{
  constructor(props){
    super(props)
    this.state = {
      people: [
        "Bob",
        "Teddy"
      ]
    }
  }
  render(){
    return(
      <div>
        { this.state.people.map(person => <GreetPerson name={ person } /> )}
      </div>
    )
  }
}
export default GreetPerson
```
The refactor includes creating an array of names in the state object. Then, to render the components we can use map() to iterate over the names of the `people` array and return a `GreetPerson` component for each name.

Now, as we add things to state, the component updates without any more code!

## Passing a Method as Props

We have explored passing information as props, but we can pass behavior as well. The process is very similar. In this example, we can create a button that when clicked will greet different people from our array. To accomplish this, we can pass both the state object and a method to our child component.

**src/App.js**
```javascript
import React, { Component } from 'react'
import GreetPerson from './GreetPerson'

class App extends Component{
  constructor(props){
    super(props)
    this.state = {
      people: [
        "Bob",
        "Teddy",
        "Joe"
      ],
      currentPerson: 0
    }
  }
  handleGreeting = () => {
    let nextPerson = Math.floor(Math.random() * this.state.people.length)
    this.setState({ currentPerson: nextPerson })
  }

  render(){
    return(
      <GreetPerson
        person={ this.state.people[this.state.currentPerson] }
        greeting={ this.handleGreeting }
      />
    )
  }
}
export default App
```

Now we are passing both data and behavior to our child component `GreetPerson`:
1. Data: the component has access to `this.state.people` as `this.props.person` through the variable `person`
2. Behavior: the component has access to `handleGreeting` as `this.props.greeting` through the variable `greeting`


**src/components/GreetPerson.js**
```javascript
import React, { Component } from 'react'

class GreetPerson extends Component{
  render(){
    return(
      <div>
        <h1>Hello, { this.props.person }!</h1>
        <button onClick={ this.props.greeting }>Greet Next Person</button>
      </div>
    )
  }
}

export default GreetPerson
```

The button in `GreetPerson` is responsible for calling the method in our parent component. If we wanted to add more names in our application, the only thing we would have to modify is the number of items in our array. The rest of our application is dynamic!

## Challenges

Dice Roller: Using a well thought out state tree and nested component structure, construct an application that rolls a die and keeps track of the numbers rolled.  Here is a wireframe to help you start planning your application:

![dice game](./assets/dice-game.png)

- As a user, I can see an application called Dice Roller
  - As a developer, I can create a React application with `App.js` as my stateful component
  - As a developer, I can create two child components that will accept props from `App.js`
- As a user, I can click a box and see the outcome of my current "roll"
  - As a developer, I can pass a method from `App.js` to my dice component to display a number between 1 and 6
- As a user, I can see my roll logged
  - As a developer, I can pass the value of the roll to a log component
- As a user, I can see the roll log continue to grow as I roll the dice

### Stretch Goals
- As a user, I can see the image of a dice face when I "roll" the dice
- As a user, I can click a restart button that clears my roll log

---

# Lecture Notes

### Overview
- Passing data and behavior into a child component
- Creating a distinction between logic and display components
- Props are an information pipeline between components
- Props cannot be updated

### Process
- Ensure you are in the cohort-lecture-examples repo
- Ensure your local is up to date and there are no stale branches
- Create a new branch
- Create a React app with the naming convention `framework-topic`
- `cd` into the project
- Run the project with `yarn start`
- Ensure all git commands are done at the repo level and all yarn commands are done at the project level

### Additional Notes and Goals
- Working with a project folder nested inside a git repository

### Major Takeaways
- Props, short for properties, are a one-directional pipeline of information between components
- State can be manipulated and updated, props cannot, props can only be re-rendered to reflect the updated state
- Passing props to a component is a similar concept to passing arguments to a function
- Keep the data and behavior centralized in the application

### Lecture
React is a collection of components. The power of this is components can be called as many times we need. Each component call instantiates that component class. And each instance of the class is a unique instance that will act independently from any other instance. This is wonderful but at this point every instance of that class component is exactly identical. We can create dynamic components that will accept additional information as props in the same way that a function will accept more information via arguments.

#### Saving App Buildout
For this example we are going to create an app that is going to draw a card and then keep track of the card that was previously drawn. Since we are just prototyping the app we are going to start with a single suit. Once the app is working we can add the full deck of cards.
- Set up App.js with a header
- Ensure App.js renders to the browser

```javascript
import React, { Component } from 'react'

class App extends Component {
  render() {
    return(
      <>
        <h1>Card Draw</h1>
      </>
    )
  }
}
export default App
```

#### Adding Card Logic
Now that the app is working we can add a state object that will hold our mini card deck and a method that will pick a random card from the deck.
- Add a state object
- Add an array of cards to state
- Add a currentCard to state
- Add a method that generates a random number to access a card from the array
- Set the currentCard to state
- Log currentCard in the render
- Add a button to call the drawCard method

```javascript
import React, { Component } from 'react'

class App extends Component {
  constructor(props) {
    super(props)
    this.state = {
      cardDeck: ["Ace", "Two", "Three", "Four", "Five", "Six", "Seven", "Eight", "Nine", "Ten", "Jack", "Queen", "King"],
      currentCard: ""
    }
  }

  drawCard = () => {
    let randomCard = Math.floor(Math.random() * this.state.cardDeck.length)
    this.setState({currentCard: this.state.cardDeck[randomCard]})
  }

  render() {
    console.log(this.state.currentCard)
    return(
      <>
        <h1>Card Draw</h1>
        <button onClick={this.drawCard}>Draw a Card</button>
      </>
    )
  }
}
export default App
```

### Card Component
Now that the logic is working, we want to create a separate component to display the card. So the first step is making sure we can see the component.
- Create a components folder in `src`
- Create a file in the components folder called `Card.js`
- Add a header to Card
- Import Card to App.js
- Call the Card component

```javascript
// src/App.js
import React, { Component } from 'react'
import Card from './components/Card'

class App extends Component {
  constructor(props) {
    super(props)
    this.state = {
      cardDeck: ["Ace", "Two", "Three", "Four", "Five", "Six", "Seven", "Eight", "Nine", "Ten", "Jack", "Queen", "King"],
      currentCard: ""
    }
  }

  drawCard = () => {
    let randomCard = Math.floor(Math.random() * this.state.cardDeck.length)
    this.setState({currentCard: this.state.cardDeck[randomCard]})
  }

  render() {
    console.log(this.state.currentCard)
    return(
      <>
        <h1>Card Draw</h1>
        <button onClick={this.drawCard}>Draw a Card</button>
        <Card />
      </>
    )
  }
}
export default App

// src/components/Card.js
import React, { Component } from 'react'

class Card extends Component {
  render() {
    return(
      <>
        <h3>Card Component</h3>
      </>
    )
  }
}
export default Card
```

#### Passing Props
Now we want the Card component to display the current card. To do this, we can pass information to the Card component through the component call. This component doesn't have its own state. It is a display component. Its job is to just take data and display it.
- Inside the component call, create a variable, equal sign, then curly braces, inside the curlies pass a value
- The variable is passed to the Card component
- The variable being passed to the Card component can be accessed in the Card component as props
- The variable can be dropped into the JSX using curly braces

```javascript
// src/App.js
render() {
  return(
    <>
      <h1>Card Draw</h1>
      <button onClick={this.drawCard}>Draw a Card</button>
      <Card card={this.state.currentCard} />
    </>
  )
}

// src/components/Card.js
import React, { Component } from 'react'

class Card extends Component {
  render() {
    return(
      <>
        <h3>Card Component</h3>
        <p>{this.props.card}</p>
      </>
    )
  }
}
export default Card
```

#### Tracking Previously Played Cards
Now that the cards variable is working, we want to be able to track all the previously played cards. We can start in App.js and create the logic to store an array of cards in state.
- Add perviousCards to the state object
- Update the drawCard method to add cards to the previousCards array using the rest syntax
- Start with logging the previousCards values in the render of App.js

```javascript
// src/App.js
import React, { Component } from 'react'
import Card from './components/Card'

class App extends Component {
  constructor(props) {
    super(props)
    this.state = {
      cardDeck: ["Ace", "Two", "Three", "Four", "Five", "Six", "Seven", "Eight", "Nine", "Ten", "Jack", "Queen", "King"],
      currentCard: "",
      previousCards: []
    }
  }

  drawCard = () => {
    let randomCard = Math.floor(Math.random() * this.state.cardDeck.length)
    this.setState({
      currentCard: this.state.cardDeck[randomCard],
      previousCards: [...this.state.previousCards, this.state.cardDeck[randomCard]]
    })
  }

  render() {
    console.log(this.state.previousCards)
    return(
      <>
        <h1>Card Draw</h1>
        <button onClick={this.drawCard}>Draw a Card</button>
        <Card card={this.state.currentCard} />
      </>
    )
  }
}
export default App
```

#### Passing the Previous Cards to Another Components
Just like we did with the Card component, we can have another component handle the display of our previous cards. Do do this we can create another component and pass the data from state. Then the previousCards component can have access to that data as props. This component doesn't have its own state. It is a display component. Its job is to just take data and display it.
- Create a file in the components folder called `PreviousCards.js`
- Add a header to PreviousCards
- Import PreviousCards to App.js
- Call the PreviousCards component
- Ensure the component renders
- Inside the component call, create a variable, equal sign, then curly braces, inside the curlies pass a value
- The variable is passed to the previousCards component
- The variable being passed to the previousCards component can be accessed in the previousCards component as props
- Console log the props

```javascript
// src/App.js
import PreviousCards from './components/PreviousCards'

render() {
  return(
    <>
      <h1>Card Draw</h1>
      <button onClick={this.drawCard}>Draw a Card</button>
      <Card card={this.state.currentCard} />
      <PreviousCards previousCards={this.state.previousCards} />
    </>
  )
}

// src/components/PreviousCards.js
import React, { Component } from 'react'

class PreviousCards extends Component {
  render() {
    console.log(this.props.previousCards)
    return(
      <>
        <h3>Previous Cards</h3>
      </>
    )
  }
}
export default PreviousCards
```

#### Mapping the Array
Now that we have access to the previous cards array as props, we want to be able to display it. But we can't just pass an array into the JSX. We need to map over the array and pass each item. Map is a JavaScript tool and when we are in JSX land, we need to use curly braces to access JavaScript.
- The return value of the map function is a JSX tag
- Look at the terminal and see the warning for `Each child in a list should have a unique "key" prop.`

React needs each JSX tag to have a unique identifier. In this case that can be achieved by referencing the index.

```javascript
// src/components/PreviousCards.js
import React, { Component } from 'react'

class PreviousCards extends Component {
  render() {
    return(
      <>
        <h3>Previous Cards</h3>
        {this.props.previousCards.map(card => {
          return <p>{card}</p>
        })} // step one - map, look at console and see error code

        {this.props.previousCards.map((card, index) => {
          return <p key={index}>{card}</p>
        })} // step two - fix error code with the key
      </>
    )
  }
}
export default PreviousCards
```

### Review
- Data can be passed to other components through the component call.
- If you pass data to another component, how is it referenced?
- What is the syntax for referencing JavaScript inside of JSX?
- What is the method for updating values in the state object?
- What is the difference between state and props?
- Can props be updated?
- What is the difference between a display component and a logic component? Why is it important to have a distinction?

### Next Steps
- Open the syllabus section and briefly run through the challenges and expectations
- Remind the student to use the `javascript-foundations-challenges` repo
- Remind the students of the appropriate naming conventions for their branch and file
- Post pairs in Slack
- Open breakout rooms with ability for participants to choose their room


---
[Back to Syllabus](../README.md#unit-two-introduction-to-react)
