# React Event Handling  

### Adding Events
on + Event Name = {Event handling program}, such as **onClick = {() => {}}**  

>Note that all React Events use Lower Camel Case to name  

### Class components event adding
Example:  

```  
import react from "react";  

class Event extends react.component{
    handleClick(){
        console.log("Click event triggered")
    }

    render(){
        return(
            <button onClick={this.handleClick}></button>
        )
    }
}

export default Event  
```  
### Function components adding events

Example:
```
import react from "react";  
function Event(){
    function handleClick(){
        document.getElementsByTagName("button")[0].style.color = "red";
        console.log("Click by function components triggered!")
    }
    return(
        <button onClick={handleClick}>click here!</button>
    )
}
```

### Event objects
>The object that is passed to event handling function is called SyntheticEvent, it is an object that contains useful metadata related to the event such as the target element's value  

Example:
```  
// In Event_Object.js

import React from "react";

function Events_Objects(){
    function handleClick(e){
        e.preventDefault();
        console.log(e.target.href);
    }
    return(
        <a href="https://www.google.com" onClick={handleClick}>Click here</a>
    )
}

export default Events_Objects

// In Index.js

import EvObject from './Events_Object';  

ReactDOM.render(
  <EvObject/>, document.getElementById('root')
);
```