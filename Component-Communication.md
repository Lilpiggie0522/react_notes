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