# Form operations
### Controlled Components
HTML has its own states, like data entered from a textbox. However, React wishes to have all its data maintained by state. And use setState() to change it.  

>Therefore, React come up with a solution that is link the value of a form element with React state.  
>Since the element's value is controlled by React, therefore we call it controlled form element.  
**Controlled state for input, textarea and select elements using value property**  

Example:  
```
class Form extends react.Component{
    constructor(){
        super()
        this.state = {
            txt: "",
        }
    }
    handleChange = (e)=> {
        this.setState(
            {
                txt: e.target.value,
            }
        )
    }

    render(){
        return(
            {<div>
            <input type="text" value={this.state.txt} onChange = {this.handleChange}>
            </div>}
        )
    }
}

export default Form
```  
**Controlled component using checked property for checkbox**  
Example:  
```
 constructor(){
        super()
        this.state = {
            txt: "",
            richtxt: "",
            city: "",
            isChecked: false,
        }
    }
<input type="checkbox" checked={this.state.isChecked} onChange={this.handleCheck}/>
```  

### Optimize controlled components
>In the above cases, each controlled components require a function to handle event. This is repetitive, therefore a single function that applies to all types of controlled components is required. Its property eg, value or checked will also need to be dynamic.  

>We achieve this by adding a name property to the controlled component that has the same name as its state. eg, name="txt", name="isChecked", etc. Then we write a ternary operator in the event handling function and determine what its type is. Then finally, we use setState() and ES5 function [name] to set the value for value or checked depending on the property.  

Example:   
```
class Form extends react.Component{
    constructor(){
        super()
        this.state = {
            txt: "",
        }
    }

    handleChange = (e)=> {
        const target = e.target;
        const value = target.type === "checked"
        ?target.value
        :target.checked
        const name = target.name;
        this.setState({
            [name]: value,
        })
        )
    }

    render(){
        return(
            {<div>
            <input type="text" name="txt" value={this.state.txt} onChange = {this.handleChange}>
            </div>}
        )
    }
}

export default Form
```   
### Non controlled components getting values from elements
Example:  
```
constructor(){
    super()
    this.state = {
        reftxt: "",
    }
    this.txtRef = react.createRef()
}
getTxt =()=>{
    this.setState({
        reftxt: this.state.reftxt,
    })
    console.log(this.txtRef.current.value)
}
<button ref={this.txtRef} onClick={this.getTxt}>getTxt</button>
```  
>Note that it is `this.txtRef.current.value`!  




