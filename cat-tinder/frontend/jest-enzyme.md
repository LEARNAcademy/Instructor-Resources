# Cat Tinder Testing with Jest and Enzyme

## Video: Jest and Enzyme
[![YouTube](http://img.youtube.com/vi/cvuAaJAFQ2o/0.jpg)](https://www.youtube.com/watch?v=cvuAaJAFQ2o)

## Overview
- There are two main tools you'll use to test your React applications: Jest and Enzyme.
- Jest is a JavaScript testing framework that is added to React when you use the command yarn create react-app.
- Enzyme is a JavaScript testing utility for React that makes it easier to test your React Components' output.

## Learning Objectives
- Using Enzyme in a React application
- Running Jest in a React application
- Organizing the component testing suite

## Vocabulary
- Jest
- Enzyme
- Shallow rendering

## Useful Commands
- $ yarn add -D enzyme react-test-renderer enzyme-adapter-react-16
- $ yarn test
- Control + C to stop the testing suite.

## Additional Resources
- [Jest Matchers](https://facebook.github.io/jest/docs/en/using-matchers.html#content)
- [Enzyme Docs](https://enzymejs.github.io/enzyme/)

## Set Up / Install
- $ yarn add -D enzyme react-test-renderer enzyme-adapter-react-16

## Jest
When you create a new React application, we get Jest automatically, which is great because Enzyme must be used in conjunction with a testing suite. On top of Jest being bundled in with our application, it also creates a test file for App.js. It has one test that looks at React's boilerplate code.

**/src/App.test.js**
```javascript
import React from 'react';
import { render } from '@testing-library/react';
import App from './App';

test('renders learn react link', () => {
  const { getByText } = render(<App />);
  const linkElement = getByText(/learn react/i);
  expect(linkElement).toBeInTheDocument();
});
```

## Enzyme
Enzyme uses Jest and layers on React specific functionality. Adding Enzyme makes working with React components even better, by allowing us to render a component or page for us and allow us to query the elements rendered.

Additionally, much like React's "hot-reload" when we run our React server, once we run `yarn test` it will continue to run and watch our file structure for any changes and re-run the test automatically for us.

## Organizing Your Tests
Each component in the Cat Tinder application needs a corresponding test file. The files can be named the same as the component file with a `.test.js` file extension.

In this case, we will create a test file called *CatIndex.test.js* in the directory in `src/pages`.

After we create our test file, we need to import in the following lines at the top of our file:

**`src/pages/CatIndex.test.js`**
```javascript
// Imports React into our test file.
import React from 'react'

// Imports Enzyme testing and deconstructs Shallow into our test file.
import Enzyme, { shallow } from 'enzyme'

// Imports Adapter utilizing the latest react version into our test file so we can run a testing render on any component we may need.
import Adapter from 'enzyme-adapter-react-16'

// Imports in the component we are going to be testing.
import CatIndex from '../CatIndex'

//Allows us to utilize the adapter we import in earlier, allowing us to call and render a component.
Enzyme.configure({adapter: new Adapter()})
```

Let's write a test to check for the text rendering in our components. We will write a test, then we'll update the code to make it pass. (That's TDD!)

```javascript
it('CatIndex renders content', () => {
  const catIndex = shallow(<CatIndex />)
  expect(catIndex.find('p').text()).toEqual('All the cats.')
})
```
Notice we import '__shallow__' from Enzyme. Here we create a variable that utilizes shallow to instantiate an instance of our CatIndex component. The magic of Enzyme is that once we have our component instanced, we can then call `catIndex.find('p').text()` to inspect the DOM of that component, find our paragraph element and look at the text it's wrapping.

Also notice the syntax of the expectation:
```javascript
    expect(<componentVariable>.<elementQueryMethod>()).<matcher>(<expectedValue>)
    expect(<actualThing>).<matcher>(<expectedValue>)
```
There are a lot of different matchers out there. We can expect our component to contain elements, or be greater/lesser than something, to be true or to be false.. etc etc.

Refer to the [Jest Matchers](https://facebook.github.io/jest/docs/en/using-matchers.html#content) docs for more information on what matchers to use and how to utilize them in your expects.



## Challenge: Cat Tinder Tests
- Add Enzyme to your application
- Add a `__tests__` directory to your component folder with test files for each existing component
  - Create a test for each page, checking that the page is rendering by a single element/tag.
- Add a `__tests__` directory to your pages folder and test files for each existing page.
  - Create a test for each page, checking that the page is rendering by a single element/tag.


## Stretch Challenges
- As a developer, I can make my tests more DRY by declaring reusable variables in global scope.
- Pages:
  - Create an additional test for the page `Home.js` that checks for the first `img` tag and all of its its props.
- Components:
  - Create an additional test for the component `Header.js` to check for a tag by its class name to contain some text.
  - Create an additional test for component `Footer.js` to check for the div `footer` to contain an HTML anchor tag linking to `/catIndex`.

---
[Back to Syllabus](../../README.md#cat-tinder-frontend)

# Lecture Notes
### Overview
  -   Jest as the test runner, assertion library, and mocking library
  -   Enzyme to provide additional testing utilities and interaction with react elements
  - Testing syntax that is specific to enzyme and react adapter 16

### Process
- Ensure you are in the cat-tinder-frontend-instructors repo
- Ensure your local is up to date and there are no stale branches
- Highlight the trello card for current section and walk through the user stories
- Create a new branch using the branch name on the trello card
- Begin lecture

### Additional Notes and Goals
 - Testing is about ensuring that all of the different elements are working without having to look at everything manually
 - Testing's usefulness is exponential 
  - It is more powerful / meaningful the more tests we write

### Major Takeaways
  - Enzyme
    - How to install
    - Syntax
    - Looking at the documentation 
  - Shallow Rendering
  - How to run the test

### Lecture
- Jest was built by Facebook for testing javascript. 
- React comes bundled with Jest.
  - it does not need to be installed separately.
  - Jest acts as a test runner, assertion library, and mocking library.
    - Jest can run lot's of different kinds of tests,
    - Jest provides lots of values for our expect statement
    
- Enzyme, created by Airbnb, adds some great additional utility methods for rendering a component (or multiple components), finding elements, and interacting with elements.

# Jest and Enzyme
- Both Jest and Enzyme are specifically designed to test React applications, Jest can be used with any other Javascript app but Enzyme was designed mainly for use with React, React native but can be used in conjunction with mocha to test Node.js.
- Jest can be used to test React projects without Enzyme.
- Enzyme can be used without Jest, however Enzyme must be paired with another test runner if Jest is not used. 
 
As described, we will use:
-   Jest as the test runner, assertion library, and mocking library
-   Enzyme to provide additional testing utilities and interaction with react elements


# Vocabulary
Jest
Enzyme
Shallow rendering

# Jest
## Jest Demonstration 
    In /src/App.test.js: this is a testing file built for us by Create React App. This file only 

```javascript
import React from 'react';
import { render } from '@testing-library/react';
import App from './App';

test('renders learn react link', () => {
  const { getByText } = render(<App />);
  const linkElement = getByText(/learn react/i);
  expect(linkElement).toBeInTheDocument();
});
```

## Running Jest
`$ yarn test`

 - this test should fail
 - this testing suite works without Enzyme as jest will be our "Test runner" 

 - If we look in the package.json file we can see the line 

"test": "react-scripts test"

this is the "test" in our $ yarn test

# Enzyme
- Enzyme is a package but it also has some packages we need to bring in alongside  that will allow it to work seamlessly with later versions of React 
  - enzyme
  - react-test-renderer
  - enzyme-adapter-react-16

`$ yarn add -D enzyme react-test-renderer enzyme-adapter-react-16`

# Imports to component-name.test.js for Enzyme setup
```javascript
import React from 'react'
import Enzyme, { shallow } from 'enzyme'
import Adapter from 'enzyme-adapter-react-16'
```
<hr>
configuration

```javascript
Enzyme.configure({ adapter: new Adapter() })
```
- Here we are going to have Enzyme configure its set up by destructing a new instance of adapter from the class adapter that we imported. 


```javascript
describe("When App renders", () => {
  it("displays a Header and Footer", () => {
  })
})
```
 - We've caught up to what we're most familiar with in testing.
 -  What is new is something called a shallow render. 

```javascript
  const renderedApp = shallow(<App/>)
```

## Shallow
- Renders only the react nodes that we select, generally we will use it to select our components. This is useful to isolate the component for pure unit testing. It protects against changes or bugs in a child component altering the behavior or output of the component under test
- As of Enzyme 3 shallow components do have access to life cycle methods by default

# Syntax for assertions
  - expect will call on some element of our shallow render
    - called the actualQueried here
    -  
```javascript
expect(<actualQueried>),<matcher>(<expected>)
```

# App.test.js 
  - see the App component layer
  - use the [.debug method](https://enzymejs.github.io/enzyme/docs/api/ShallowWrapper/debug.html)
  - use the [.props method](https://enzymejs.github.io/enzyme/docs/api/ShallowWrapper/props.html)



```javascript

import App from './App'
import React from 'react'
import Enzyme, { shallow } from 'enzyme'
import Adapter from 'enzyme-adapter-react-16'
import Home from './pages/Home'

Enzyme.configure({ adapter: new Adapter()})


describe("When App renders", () => {
  it("displays a Header and Footer", () => {
  
    const renderedApp = shallow(<App/>)
    
    const renderedHeader = renderedApp.find("Header")
    const renderedFooter = renderedApp.find("Footer")
    
    expect(renderedHeader.length).toEqual(1)
    expect(renderedFooter.length).toEqual(1)
  })

  it('provides a route "/" to the home component', () => {
    
    const renderedApp = shallow(<App/>)

   
    const renderedHomeRoute = renderedApp.find('[path="/"]')
        // debug
    console.log("rendered home debug", renderedHomeRoute.debug())
        // props
    console.log("rendered home props", renderedHomeRoute.props())
    //Assert
    expect(renderedHomeRoute.length).toEqual(1)
    expect(renderedHomeRoute.props().component).toEqual(Home)
  })
})
```

# Organization
- lets move away from testing our general app and start the practice of making solid tests for each of our components and pages. 

we'll make a new file called and place it along side our Header file

`Header.test.js`



# src/components/Header.test.js
```javascript
import React from 'react'
import Enzyme, { shallow } from 'enzyme'
import Adapter from 'enzyme-adapter-react-16'
import Header from '../Header'


Enzyme.configure({ adapter: new Adapter()})

describe("When Header Loads ... ", ()=>{
    
    // let header
    // beforeEach(()=>{
    //     header = shallow(<Header/>)
    // })
    it('displays NavLinks on the header',()=>{
        
        const navLinkWrapper = header.find('NavLink')
       
        expect(navLinkWrapper.length).toEqual(3)
    })
    it('displays an "a" tag on the header',()=>{
        
        const aTagWrapper = header.find('a')
       
        expect(aTagWrapper.length).toEqual(1)
    })

})

// GO BACK TO THE FOR EACH
```
# src/components/Footer.test.js
```javascript
import React from 'react'
import Enzyme, { shallow } from 'enzyme'
import Adapter from 'enzyme-adapter-react-16'
import Footer from './Footer'

Enzyme.configure({ adapter: new Adapter()})

describe('When Footer renders', () => {
  const footer = shallow(<Footer />)
  const footerNav = footer.find('NavLink')

  it('has clickable links', () => {
    expect(footerNav.length).toEqual(4)
  })
})
```


### Review
 - The basic anatomy up for an Enyzme test is 
   - imports
   - configurations
   - testing blocks
   - shallow render
   - assertion on the render
 - [Selectors syntax](https://enzymejs.github.io/enzyme/docs/api/selector.html)
 - Assertion syntax
    > expect(<componentVariable>.<elementQueryMethod>()).<matcher>(<expectedValue>)> expect(<actualThing>).<matcher>(<expectedValue>)


### Next Steps
- Open the syllabus section and briefly run through the challenges and expectations
- Remind the student to use the `react-challenges` repo
- Remind the students of the appropriate naming conventions for their branch and file
- Post pairs in Slack
- Open breakout rooms with ability for participants to choose their room

---