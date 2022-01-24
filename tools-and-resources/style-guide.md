# Instruction Team Style Guide

NOTE: WIP

### JavaScript

- All JavaScript operators have a space on each side
- Attributes in a JSX tag do not have spaces
- No spaces between the method/action and parentheses
- Space between closing parentheses and opening curly brace
- Indentations consist of two spaces

Conditional Statements
```javascript
if(evaluation) {
  return "Output"
} else if(evaluation) {
  return "Output"
} else {
  return "Output"
}
```

For Loops
```javascript
for(let i = 0; i < array.length; i++) {
  "Output"
}
```

Functions and Expressions
```javascript
const iAmAFunction = (argument) => {
  return "Output"
}

function iAmAFunction(argument) {
  return "Output"
}

componentDidMount() {
  return "Output"
}

() => {return "Output"}
```

Higher-order Functions
```javascript
.map(value => {
  return "Output"
})
```
