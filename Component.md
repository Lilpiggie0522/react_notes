# Two ways to create React Components

### 1. Create React components using functions
Render function component: Use function name as component tag name.
Start function name with an uppercase letter to render a React component
Can use both `<Hello />`or `<Hello></Hello>`
Function must have return statement. If nothing is intended to be rendered, return "null".

Example:
```
function Hello(){
  return(
  <div>This is my first function</div>
  )
}
```
```
ReactDOM.render(
  <Hello />, document.getElementById('root')
);
```

### 2.Create React components using Arrow Functions
Example:
```
const Hello = () => (<div>This is my first function component</div>)
```
>Note that when writing arrow functions, either
```
const Hello = () => {
    return(
        <div></div>
    )
}
```
or
```
const Hello = () =>(<div></div>)
```

### 3.Creating React components using Class Names
Class components: Components created by ES6 Classes
Class name also needs to start with uppercase letters
Class components inherits React.Component parent class
Class components must provide render()
render() must have return statement

Example:
```
class Hello extends React.Component{
    render(){
        return(
            <div>Hello Class Component!</div>
        )
    }
}

ReactDOM.render(<Hello />, document.getElementsById("root"));
```
**Note that** render() is written as:
>render(){
    (<div></div>)
}

### Extract components into single file
>1.Create Hello.js
>2.Import React in Hello.js
>3.Create components
>4.Export component in Hello.js

Example: 
```
// In Hello.js
class Hello extends React.components{
    render(){
        (<div>Extracted Component</div>)
    }
}

export default Hello
```
```
// In Index.js
import Hello from './Hello.js'
ReactDOM.render(<Hello />, document.getElementById("root"))
```
