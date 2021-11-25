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
