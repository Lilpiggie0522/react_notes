# React component basics

### Render comment list
1. Initialize comment list data in React state.  
2. Use map() to loop over each element within the state.  
3. Add key to each of the <li> created by map().  

Example:  
>How to make comment list data in react:  
```
state = {
    comments: 
            [
                {id:1, name: 'jeff', content: "good!"},
                {id:2, name: 'tom', content: "thanks!"},
                {id:1, name: 'chris', content: "hello!"}
            ],
}  
```  
>Because `this.state.comment` is an array, therefore we use map() to loop it.  

>Note that map() is used like this:  
```  
<ul>
    {
        this.state.comments.map(item = () =>
            (
            <li>
                <h1>{item.name}</h1>
                <p>{item.content}</p>
            </li>
            )
        )
    }  
</ul>  
```  

### Conditional rendering
Use ternary operator to determine if there is data within this.state.comment, if not, render  
"No comments yet, post comments!". If there is, render out all comments.  

Example:  
```
{this.state.comments.length === 0
? <div>No comments yet, post comments!</div>
: this.state.comments.map(item = () =>
            (
            <li>
                <h1>{item.name}</h1>
                <p>{item.content}</p>
            </li>
            )
        )
}
```  
>However, this JSX code tangled with JavaScript code does not seem to look well structure wise, therefore, a way to optimize it is needed.  

### Optimize the JSX code  
We optimize the code by extracting all the content of ternary operator into a method. 
Example:  
```
renderList = () => {
    return this.state.comments.length === 0
    ? <div>No comments yet, post comments!</div>
    : this.state.comments.map(item = () =>
            (
            <li>
                <h1>{item.name}</h1>
                <p>{item.content}</p>
            </li>
            )
        )
}
}
```  
>We can also use destructuring to destructure comments in state. Look at the strike through!  
`~this.state.comments~`
