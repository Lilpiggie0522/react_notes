# Where this points in events (事件绑定this指向/Точки привязки событий)
When writing JSX in React, it is necessary to extract JavaScript from JSX code.  

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