# Cat Tinder Create Functionality

## Overview
- Adding the CRUD "create" functionality to the frontend of Cat Tinder using mock data
- Adding a form to the project
- Creating a method that will log the form data

## Learning Objectives
- Applying the concept of RESTful routes to a React application
- Connecting the data from a form input and passing it to `App.js`

## Additional Resources
- [ Reactstrap Form Components ](https://reactstrap.github.io/components/form/)
- [ React-router Redirect ](https://reactrouter.com/web/api/Redirect)

## Cat Create Form
To create a new cat, the first step is creating a form. This will allow a place for our user to add to the list of cat friends in our app. We can utilize Reactstap to help with form styling.

Reactstrap has an element called `<FormGroup>`. Nested in each `<FormGroup>` tag there will be a label and an input. Each input tag will take two attributes. The first is `type` that describes what information can be entered into the field. The second is `name` that matches the appropriate cat attribute. In this example the name of the input is "name" in reference to our cat name attribute.

Each cat attribute will have its own `<FormGroup>` inside of a single `<Form>` tag.

**src/pages/CatNew.js**
```javascript
<Form>
  <FormGroup>
    <Label for="name">Name</Label>
    <Input
      type="text"
      name="name"
    />
  </FormGroup>
</Form>
```

Complete the process by importing the Reactstrap components.

**src/pages/CatNew.js**
```javascript
import {
  Form,
  FormGroup,
  Input,
  Label
} from 'reactstrap'
```

## Cats in State
When we create new cats we want to collect the user input and transmit the data as a set. We can accomplish this by switching our inputs to be “controlled components,” meaning watched by state. Or, in other words, add a `value`, and an `onChange` attribute to the inputs. Then we can manage the value of the inputs in the components’ internal state until the form is submitted.

By adding a form object to state we can reference `this.state.form` and have a complete cat object that can be passed to `App.js` as a single unit rather than as individual values.

**src/pages/CatNew.js**
```javascript
constructor(props){
  super(props)
  this.state = {
    form:{
      name: "",
      age: "",
      enjoys: ""
    }
  }
}
```

To set the inputs to state we need a `handleChange` method to be called on every input.

**src/pages/CatNew.js**
```javascript
handleChange = (e) => {
  // destructuring form out of state
  let { form } = this.state
  form[e.target.name] = e.target.value
  // setting state to the updated form
  this.setState({form: form})
}
```

Now we can update each input with an `onChange` attribute that calls the `handleChange` method and a `value` attribute that reflects the current status of state.

**src/pages/CatNew.js**
```javascript
<FormGroup>
  <Label>Name</Label>
  <Input
    type="text"
    name="name"
    onChange={this.handleChange}
    value={this.state.form.name}
  />
</FormGroup>
```

## Passing Cats to App.js
Now that we have all the content from the form updated into state, we need to get the information back to `App.js`. This means we need to pass information "up the river" from child component to parent. To accomplish this we need to create a method in `App.js` that gets called when we submit the form.

During our scaffolding phase, the goal here is to see the new cat logged in `App.js`. Eventually this method will be refactored to include an interaction with the database.

**src/App.js**
```javascript
createNewCat = (newcat) => {
  console.log(newcat)
}
```

This method needs to be passed to our CatNew component. This will require a refactor of the basic "/catnew" route into a dynamic route that accepts props.

**src/App.js**
```javascript
<Route
  path="/catnew"
  render={(props) => <CatNew createNewCat={this.createNewCat} />}
/>
```

Once the method is passed down to the CatNew component, we can wrap it in a method that will pass our form object.

**src/pages/CatNew.js**
```javascript
handleSubmit = () => {
  this.props.createNewCat(this.state.form)
}
```

We need to call the method `onSubmit`. To accomplish this, we can add a button from Reactstrap. (Don't forget to add the Reactstrap import!)

**src/pages/CatNew.js**
```javascript
<Button
  name="submit"
  onClick={this.handleSubmit}
>
  Create a New Profile
</Button>
```

Now when we add information to the form, we can see the object logged in console.

## Finishing Touches
Here is a good opportunity to start thinking a bit about user flow. Once a cat is entered, it would be nice to redirect to see the success of the form submission. We can use a few handy tricks along with React-router functionality to create a redirect.  

**src/pages/CatNew.js**
```javascript
constructor(props){
  super(props)
  this.state = {
    form:{
      name: "",
      age: "",
      enjoys: ""
    },
    submitted: false
  }
}

handleSubmit = () => {
  this.props.createNewCat(this.state.form)
  this.setState({submitted: true})
}
```

By adding a success attribute to state we can control when the redirect happens. When state is updated we can use conditional rendering to pass a [ React-router redirect component ](https://reactrouter.com/web/api/Redirect) that renders a new page.

**src/pages/CatNew.js**
```javascript
// react-router import
import { Redirect } from 'react-router-dom'

// JavaScript code at the bottom of the JSX that will redirect when success is true
{this.state.submitted && <Redirect to="/catindex" />}
</>
```

---

## Challenge: Cat Create
As a developer, I have been commissioned to create an application where a user can see cute cats looking for friends. As a user, I can see a list of cats. I can click on a cat and see more information about that cat. I can also add cats to the list of cats looking for friends. If my work is acceptable to my client, I may also be asked to add the ability to remove a cat from the list as well as edit cat information.

- As a user, I can fill out a form to add a new cat
- As a developer, I can store the cat object in state
- As a developer, I can pass the cat object to App.js on submit and see the cat object logged in the console
- As a user, I can be routed to the index page after I submit the new cat form
- As a developer, I have test coverage on my new page

**NOTE:** We are still only interacting with mock data so we will not see a new cat added to the collection of cats.

---

# Lecture Notes

### Overview
- Using Reactstap to create a form
- Collecting the form data in state
- Using functional props to send the new cat object "up the river" to App.js
- Using conditional rendering to redirect after submission
- Adding test coverage to the form

### Process
- Ensure you are in the cat-tinder-frontend-instructors repo
- Ensure your local is up to date and there are no stale branches
- Ensure Trello is up to date
- Move the appropriate Trello card and add your name to the card
- Create a new branch in connection with the appropriate Trello card
- Run the project with `yarn`

### Additional Notes and Goals
- Structuring a form to connect to a state object
- Modeling the Trello workflow
- Modeling the PR workflow

### Major Takeaways
- Working with mock data in the frontend
- Ensuring the data is being passed to the correct component

### Lecture
We already have a page to create a new cat but so far it is not doing much of anything. We know that RESTful routes provide an agreed upon structure for how a user can interact with data. To create new items in the db, we need a form and we need to send a post request to the database. Since we are not yet working in the backend the post action won't happen, we just need to get the app structured so the data is in the right format and in the right location.

#### Create a Form
Use Reactstrap to create form data.
- [Reactstap](https://reactstrap.github.io/?path=/docs/components-forms--form)
- Import components
- Create four FormGroup sets
- The name of each input is going to match the mock data key of each cat object (name, age, enjoys, image)

```javascript
import { Form, FormGroup, Label, Input } from 'reactstrap'

<Form>
  <FormGroup>
    <Label>Name</Label>
    <Input
      type="text"
      name="name"
    />
  </FormGroup>
  <FormGroup>
    <Label>Age</Label>
    <Input
      type="number"
      name="age"
    />
  </FormGroup>
  <FormGroup>
    <Label>Enjoys</Label>
    <Input
      type="text"
      name="enjoys"
    />
  </FormGroup>
  <FormGroup>
    <Label>Image</Label>
    <Input
      type="text"
      name="image"
    />
  </FormGroup>
</Form>
```

#### Setting State
We always want to think about whether a component is going to hold logic or only be a display component. In this case, the component needs to be able to store data so that we can take the content from the inputs and wrap it into a data structure that can be sent to the backend.

The new component is going to hold state but only for its internal use.
- In the state object there is going to be a key of newCat that will have a value of an object
- The object will have all the keys from the cat mock data
- Add a handleChange method that will allow a dynamic update of the state object
- Add onChange and value attributes to each input

```javascript
constructor(props){
  super(props)
  this.state = {
    newCat: {
      name: "",
      age: "",
      enjoys: "",
      image: ""
    }
  }
}

handleChange = (e) => {
  // destructures newCat out of state
  let { newCat } = this.state
  // uses bracket notation to target a key based on the current input
  // assigns the key to the value of the current input
  newCat[e.target.name] = e.target.value
  // sets state
  this.setState({newCat: newCat})
}

<FormGroup>
  <Label>Name</Label>
  <Input
    type="text"
    name="name"
    onChange={this.handleChange}
    value={this.state.newCat.name}
  />
</FormGroup>
```

#### Submit Data in CatNew
Add a Button component from Reactstrap and connect the click event to a handleSubmit that will start with logging the state object.

```javascript
handleSubmit = () => {
  console.log(this.state.newCat)
}

<Button
  name="submit"
  onClick={this.handleSubmit}
>
  Create a New Cat Profile
</Button>
```

#### Passing Data to App.js
Now that we can see the correct data structure of each new cat being logged in the CatNew component, the next step is to pass the cat object back up to App.js.
- Create a method in App.js
- Refactor the static route to be dynamic
- Pass the method to CatNew

```javascript
// App.js
createCat = (newcat) => {
  console.log(newcat)
}

// Refactor the route to be a dynamic route
<Route
  path="/catnew"
  render={(props) => <CatNew createCat={this.createCat} /> }
/>
```

- Call the method and pass the new cat object

```javascript
// components/CatNew.js
handleSubmit = () => {
  console.log(this.state.newCat) // previous code
  this.props.createCat(this.state.newCat) // updated code
}
```

#### Redirect
To create a better user experience we can add a redirect action.

```javascript
import { Redirect } from 'react-router-dom'

class CatNew extends Component {
  constructor(props){
    super(props)
    this.state = {
      newCat: {
        name: "",
        age: "",
        enjoys: "",
        image: ""
      },
      submitted: false // add another value in state
    }
  }

  handleSubmit = () => {
    this.props.createCat(this.state.newCat)
    this.setState({submitted: true}) // update state
  }

  <Form>
    // content ....
  </Form>
  {this.state.submitted && <Redirect to="/catindex" />}
}
```

#### Test Coverage
- Add a new file called CatNew.test.js to the pages folder
- Assert against the form tags

```javascript
// src/pages/CatNew.test.js
import React from 'react'
import Enzyme, { shallow } from 'enzyme'
import Adapter from 'enzyme-adapter-react-16'
import CatNew from './CatNew'

Enzyme.configure({ adapter: new Adapter()})

describe("When CatNew renders", () => {
  it("displays a form", () => {
    const catNew = shallow(<CatNew />)
    const formGroup = catNew.find("FormGroup")
    expect(formGroup.length).toEqual(4)
    const label = catNew.find("Label")
    expect(label.length).toEqual(4)
    const input = catNew.find("Input")
    expect(input.length).toEqual(4)
  })
})
```

### Review
- CatNew is a view page for the user
- We won't be able to actually make cats since this is still mock data

### Next Steps
- Open the syllabus section and briefly run through the challenges and expectations
- Remind the students of the appropriate naming conventions for their branch based on the Trello card
- Open breakout rooms with ability for participants to choose their room

---
[Back to Syllabus](../../README.md#cat-tinder-frontend)
