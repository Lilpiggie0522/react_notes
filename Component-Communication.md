# Props

### Props is used to pass on data in between components, since each component is isolated, therefore props is used to communicate between components.

### Passing data
>Add properties to components tag  

### Receiving data  
>Function components use props to receive data, whereas class components use this.props  

Function components Example:  
```
function Component_advanced(props){
  console.log(props)
    return(
      <div>
        <h1>Props: {props.name}</h1>
      </div>
    )
}

ReactDOM.render(
  <Component_advanced name="rose" age={19} />, document.getElementById('root')
);
```  
>Note that function components can also be written using arrow functions  
**Arrow Functions Example:**  
```
const Component_advanced = (props) => {
  console.log(props)
  return(
    <div>
      <h1>Props: {props.name}</h1>
    </div>
  )
}
ReactDOM.render(
  <Component_advanced name="rose" age={19} />, document.getElementById('root')
);
```

Class Components Example:  
```
class Component_advanced extends react.Component{
  render(){
    console.log(this.props)
    return(
      <div>
        <h1>Props: {this.props.name}</h1>
      </div>
    )
  }
}


ReactDOM.render(
  <Component_advanced name="rose" age={19} />, document.getElementById('root')
);
```

### Props Features
1. Any type of data can be passed by the components via props.  

2. Props is read only object, which means we **cannot** do `this.props.name = "piggie"`  

3. When using class components, if constructor is written, and you wish to access props with in constructor method, then props must be passed into super(), otherwise props is inaccessible in constructor.  

Example:  
```
class Component_advanced extends react.Component{
  constructor(props){
    super(props)
    console.log(this.props)
  }

  render(){
    console.log(this.props)
    this.props.fn()
    return(
      <div>
        <h1>Props: {this.props.name}</h1>
        {this.props.tag}
      </div>
    )
  }
}

ReactDOM.render(
  <Component_advanced 
  name="rose" age={19} 
  colors={["red", "blue", "green"]} 
  fn={()=>{console.log("this is an arrow function")}}
  tag = {(<p>Piggie is a doggie</p>)}
  />, document.getElementById('root')
);
```

### Parent to Child data transfer using props
1. Parent components provides property in state
2. Add property in child tag using state from parent
3. Child component receives data using props  

```
class Parent extends react.Component{
  state = {
    lastName: "wang"
  }
  
  render(){
    return(
      <div className="parent">
        <Child name={this.state.lastName} />
      </div>
    )
  }
}

const Child = (props) => {
    return(
        <p>Child: {props.name}</p>
    )
}

ReactDOM.render(
  <Parent />, document.getElementById('root')
);
```  
### Child to Parent component
1. Set up callback function in parent, note that this function is not called by parent component, whoever is tranferring data to parent components will call it.  

2. Add a property to child component and have this property using this callback function.  

3. Have an onClick or other event listener to call the callback function using props.propertyName() and pass whatever it is that needs to be sent into the function.  

Example:  
```
class Parent extends react.Component{
  state = {
    parentName: ""
  }

  getMsg = (props) => {
    this.setState({
      parentName: props.name,
    })
  }

  render(){
    return(
      <div>
        <div className="parent">
          <h1>Parent: {this.state.parentName}</h1>
        </div>
        <div className="child">
          <Child sendMsg={this.getMsg}/>
        </div>
      </div>
    )
  }
}

class Child extends react.Component{
  constructor(){
    super()
    this.state = {
      name: "piggie",
    }
  }

  sendParent = () => {
    this.props.sendMsg(this.state)
  }

  render(){
    return(
        <button onClick={this.sendParent}>Click me and send props to parent</button>
    )
  }
}

ReactDOM.render(
  <Parent />, document.getElementById('root')
);
```