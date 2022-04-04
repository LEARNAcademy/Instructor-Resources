# React Consuming External APIs Using Fetch

## Video: Fetch
[![YouTube](http://img.youtube.com/vi/Law40pSLeHM/0.jpg)](https://www.youtube.com/watch?v=Law40pSLeHM)

## Overview
- In modern web applications, communication between the frontend application and the backend server happens using JSON.
- APIs are packets full of raw data (JSON) meant to be consumed by other websites.
- To consume an API, a developer codes a fetch request to the API's url and parses through the data response (JSON) to return meaningful information to the user.
- Many companies make their APIs available to the public for free so that other developers can make use of the data a company has acquired.
- Using external APIs in your applications will expand functionality and increase user enjoyment.

## Learning Objectives
- Explore the variety of public APIs
- Understanding the process of making a fetch request to an API

## Vocabulary
- API
- JSON
- endpoint
- fetch
- Promise

## Set Up

#### Creating a new React app:
```
$ yarn create react-app my-app
$ cd my-app
$ yarn start
```

## Access a Free API
- Google!
- Look for good documentation



## Fetch and Promises
Fetch is a JavaScript function that allows developers to make asynchronous network requests.

The `fetch()` function takes one mandatory argument: the path to the resource you want to fetch.

Fetch returns a Promise. A Promise is a JavaScript object. Promises represent the eventual completion or failure of an asynchronous operation and either the payload or the error.

When the response from the network request comes back, the promise is fulfilled.

If the response is successful, a JSON payload is delivered to the application.

```javascript
fetch("https://api-url-here.com")
.then(response => response.json())
.then(payload => this.setState(payload))
.catch(error => console.log(error))
```


## Challenge
- Create a React application that shows the user their current location and IP address
- Use [ this ](https://ipapi.co/api/?shell#location-of-clients-ip) API and documentation

## Stretch Challenge
- Use an external API and docs to create an application of your choice
- Here is the [ Nasa API ](https://api.nasa.gov/)

---

# Lecture Notes

### Overview
- Being a full-stack developer means interacting with APIs, sometimes it is an API that you create to serve data to the frontend of your app, other times it is consuming data that exists from an external source
- Fetch is a JavaScript API that allows for asynchronous actions
- Fetch returns a Promise

### Process
- Ensure you are in the cohort-lecture-examples repo
- Ensure your local is up to date and there are no stale branches
- Create a new branch
- Create a React project with the naming convention `framework-topic`
- Run the project with `yarn start`

### Additional Notes and Goals
- [Mean Girls Video](https://www.youtube.com/watch?v=jjt9Qx9MBPk)
- Revisit React after a long break from JavaScript and frontend code

### Major Takeaways
- Asynchronous programming is powerful yet complicated
- Fetch returns a Promise
- A Promise has three states: pending, fulfilled, rejected

### Lecture
The Fetch API interface allows web browsers to make HTTP requests to web servers. Fetch is a method in JavaScript that makes asynchronous requests. JavaScript, as a language, is a single threaded. That means it can do one thing at a time. JavaScript has a queue of tasks and it executes the tasks one by one, in order. This can become problematic when working with external APIs. As a developer, you don't have control over how long it will take to complete a request-response cycle. Even having a progress bar or a loading message requires code logic to be executing. Asynchronous programming is the way to solve this problem. An asynchronous action will step out of the queue while it is processing and step back in when the process is complete.

#### Promises
Fetch is a way to make asynchronous requests. When you send out a request and specify that it is going to be asynchronous, what you get back is a Promise. Promises represent the eventual completion (or failure) of an asynchronous operation. Promises will return either the payload of data or an error. A Promise is a proxy for a value not yet known. A Promise says, "I will definitely give you back something. I just have no way of knowing if it will succeed or fail or how long it will take."
- Promises are JavaScript objects
- Promises are in one of three states: pending, fulfilled, rejected
- Fetch is a method that takes the argument of a URL
- Fetch is followed by a series of methods that are higher-order functions to handle the response
-

#### Fetch
To explore the fetch syntax, we are going to use a really simple API. [IP address location](https://ipapi.co/api/?shell#location-of-clients-ip)

- React app is going to make a request to the external API
- Need to store the data in the component
- Render the data to the page

```javascript
class App extends Component{
  constructor(props){
    super(props)
    this.state = {
      ipAddress: ""
    }
  }

  // First - Make sure the function works.
  getIp = () => {
    alert("yo") // step 1
  }

  // Second - This is the very simplest use of fetch. Passing an argument of API endpoint you want to fetch and returns a promise containing the response.
  getIp = () => {
    fetch("https://ipapi.co/json/")
    .then(response => console.log(response))
  }

  // Third - The object is just an HTTP response. To extract the JSON body content from the response, we use the .json() method and we can see the promise object.
  getIp = () => {
    fetch("https://ipapi.co/json/")
    .then(response => console.log(response.json()))
  }

  // Fourth - Once the promise is fulfilled we can handle the payload.
  getIp = () => {
    fetch("https://ipapi.co/json/")
    .then(response => response.json())
    .then(payload => console.log(payload))
  }

  // Fifth - Once we can see the payload being logged the next step is setting the data to state.
  getIP = () => {
    fetch("https://ipapi.co/json/")
    .then(response => response.json())
    .then(payload => this.setState({ip: payload}))
  }

  // Sixth - Catch is like an else statement that can log any errors we get.
  getIP = () => {
    fetch("https://ipapi.co/json/")
    .then(response => response.json())
    .then(payload => this.setState({ip: payload}))
    .catch(error => console.log(error))
  }

  render(){
    return(
      <>
        <h1>Find Your IP Address</h1>
        <button onClick={this.getIp}>Click here to see your IP Address</button>
        <p>IP: {this.state.ipAddress.ip}</p>
      </>
    )
  }
}
```

#### NASA API Scaffold
The NASA API has super cool information and it gives us a test run at the data. No matter what, storing data costs money. And accessing that stored data cost money. So it is common for developers to limit the number of API calls (or requests) that can be made to a server. That way, whoever owns the data stays in change of who can access it and can control the amount of traffic to prevent overwhelming the server.

Remember that every time you make a request, you get a response. Even if that response is an error. A malicious person could have a bunch of computers pinging a web server thousands and thousands of times a second and back up the server. All the requests will get answers, but if the server is answering slower than the requests are coming in a queue will start to form. This can create a situation where normal users will try and use the site and it will look like it is down because that request is behind so many others. When this is done intentionally to cause harm it is called a DDOS attack - or distributed denial of service attack.

To prevent this from happening, developers will ask users of their API to register so that they can put a limit on the number of requests made by a single app. This is usually done in the form of an API key. A key will be a token that is added to the URL in the fetch request.
- Not all APIs are created equally
- Scaffold the app by putting the data in a local file
- Make sure the logic works
- Then make the fetch request
- [Nasa API](https://api.nasa.gov/)

```javascript
// File - src/mockNasa.js
// let nasaData = .....
// export default nasaData
// beautify

import React, { Component } from 'react'
import './App.css'
import nasaData from './mockNasa.js'

class App extends Component {
  constructor(props) {
    super(props)
    this.state = {
      nasa: nasaData.photos,
      pic: null
    }
  }

  getPic = () => {
    let randomNum = Math.floor(Math.random() * this.state.nasa.length)
    this.setState({pic: this.state.nasa[randomNum].img_src})
  }

  render() {
    console.log(this.state.nasa)
    return(
      <>
        <h1>Mars Rover Pic</h1>
        <button onClick={this.getPic}>Click here</button>
        <br />
        <img style={{height: "200px"}} src={this.state.pic} alt="random Mars Rover" />
      </>
    )
  }
}
export default App
```

#### NASA API Fetch
Now that the app is working correctly it is time to fetch live data.
- Make an account with NASA
- Generate an API key
- Start with adding it directly to the URL
- [Hiding API Keys](https://www.pluralsight.com/guides/hiding-secret-keys-in-create-react-app)
- Create an .env file and add it to .gitignore
- REACT_APP_MY_NASA_API_KEY = "key here"
- Update fetch call
- Will need to restart server

```javascript
// First - Add the key directly to the URL.
componentDidMount() {
  fetch("https://api.nasa.gov/mars-photos/api/v1/rovers/curiosity/photos?sol=1500&api_key=long-string-of-characters-here")
  .then(response => response.json())
  .then(payload => {
    console.log(payload)
    this.setState({nasa: payload.photos, pic: payload.photos[0].img_src})
  })
  .catch(error => console.log(error))
}

// Second - Replace the key with an environment variable.
componentDidMount() {
  let apiKey = process.env.REACT_APP_NASA_API_KEY
  fetch(`https://api.nasa.gov/mars-photos/api/v1/rovers/curiosity/photos?sol=1500&api_key=${apiKey}`)
  .then(response => response.json())
  .then(payload => {
    console.log(payload)
    this.setState({nasa: payload.photos, pic: payload.photos[0].img_src})
  })
  .catch(error => console.log(error))
}
```

### Review
- What are APIs? Websites that store data.
- How can you access an API? With a fetch request.
- What does fetch return? A promise.
- What are the three states of a promise? Pending, rejected, fulfilled.
- What is an API key?
- How do you protect your API key? Don't push it to GitHub, use an .env file.
- How do you know if you have found a "good" API or a "bad" one? You don't. You have to read the docs and test it out.

### Next Steps
- Open the syllabus section and briefly run through the challenges and expectations
- Remind the student to use the `react-challenges` repo
- Remind the students of the appropriate naming conventions for their branch and file
- Post pairs in Slack
- Open breakout rooms with ability for participants to choose their room

---
[Back to Syllabus](../README.md#unit-six-ruby-on-rails)
