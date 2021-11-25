# Where this points in events (事件绑定this指向/Точки привязки событий)
When writing JSX in React, it is necessary to extract JavaScript from JSX code.  
### Method 1: Use arrow functions in onclick={}
Example:  
```
class State extends react.Component{

    state = {
        count: 10,
    }
    
    handleClick(){
        this.setState({count: this.state.count + 1})
        }
        console.log()
    }

    render(){
       
        return(
            <div>
                <h1 onClick={this.handleClick}>
                    counter: {this.state.count}
                </h1>
                <button onClick = {()=> handleClick()}>+1</button>
            </div>
        )
    }

}
```
>Note that when extracting JavaScript from JSX into a method, In `{this.handleClick}`, the "this" here refers to the global object (main browser window), but when `<h1 onClick={this.handleClick}>` is executed `handleClick()` is not called, therefore according to the this pointer rule, whoever calls the method becomes the this, in this case, nobody has called the handleClick method, therefore this is null, which is undefined.  

### "this" in arrow function does not have a default object pointed to iteself  

### "this" in a function points to whereever the function is called.

### Method 2: Use bind()
```
import react from "react";

class State extends react.Component{
    constructor(){
        super();
        this.state = {
            count: 10,
        };
        this.HandleClick = this.handleClick.bind(this);
    }

    handleClick(){
        this.setState({
            count: this.state.count +=1
        })
    }

    render(){
        return(
            <button onClick={handleClick}>+1</button>
        )
    }
}

export default State;
```  
>The key here is the bind() method.  
>**For example, `this.handleClick = this.handleClick.bind(this)` replaces this in handleClick function to whatever instance you tell it to be. And then assign its value to this.handleClick, it actually can be assigned to any variables but here we have this line of code in the constructor method, therefore, we write `this.handleClick` rather than handleClick**.  

### Method 3: Use arrow function directly in class components instead of onClick = {}
>Note that this method is recommended