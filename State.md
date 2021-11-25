# Stateful components and State Less components

### Stateful components are class Components
>State is data  

>Class components have their own states, they are responsible for refreshing UI, and make the view active!  

### State less components are function components
>Function components do not have their own **states**, they are only in charge of display the data (static).  

### Basic usage of State
>State is data, is the internal data within a component, can only be accessed from inside the component  

>Value of state is an object, meaning there can be multiple data within a component.  

Example:

```
// In State.js Component  

import react from "react";

class StatePrac(){  

    state = {
        count: 10;
    }

    render(){
        return(
            <div><h1>Counter: {this.state.count}</h1></div>
        )
    }
}

export default state  

// In Index.js  
import State from './State';  

ReactDOM.render(
  <State />, document.getElementById('root')
);
```  
>Note that constructor state = {count:10} is identical to  
```
constructor(){
    super();
    this.state = {
        count:10,
    }
}
```
>The short way of calling constructor method after ES6 is recommended here.  


# State and setState in components
### setState() changing state

Example
```
import react from "react";

class State extends react.Component{

    state = {
        count: 10;
    }

    render(){
        return(
            <div>
            <h1>Counter: {this.state.count}</h1>
            <button onClick = {()={
                this.setState({
                    count: this.state.count +1,
                })
            }}></button>
            </div>
            )
    }
}

export default State;
```
>Note that  
>In `state = {count: 10}`, **state** is a React Keyword, if replced by any other words, it will not work.  
