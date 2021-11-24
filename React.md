# React Basics

Create-react-app is a type of scaffolding

`const title = createElement('h1', {Property such as className: "className"}, 'A string for h1')` or however many items to load on to h1 after 'A string for h1'

```
reactDOM.render(**title**, document.getElementById("root"))
```

# JSX

JSX = JavaScript XML(HTML), which means writing HTML in JavaScript. It is more straight forward than createElement.

JSX is not standard ECMASCRIPT grammar but **why can we use it in react.js files?**
The reason is that Create-react-app has placed babel internally to compile JSX then run in browser environment.

### React elements with no child-node can use /> to end directly. Note that this is only a JSX feature, don't do it in normal HTML.

Examle: `<h1>Hello Jsx<span /></h1>`

### Use () to wrap JSX up. This prevents auto inserting of ; in JS.

# Using JS expressions in JSX
```
const name = Jack
```
```
const dv = (<div>Hello, my name is{name})</div>
```

### JSX Conditional rendering
```
const loadData = ()=>{if(isLoading){return(<div></div>)}}
```
> **Code using ternary operator** `const loadData = ()=>{isLoading?(<div>Loading...</div>):(<div>Not loading</div>)}`

### && Operator Logic AND AND
Returns the **second operand** if the operand does not return true or false.
```
const loadData = () => {return isLoading && <h1>Loading...</h1>}
```

### List rendering in JSX
When redering list in JSX, use map! And remember to have unique key for each child element created by mapping.
```
const songs = [
    {id:1, name:"piggie"}, 
    {id:2, name:"doggie"}, 
    {id:3, name:"kitty"}
    ]
```
```
songs.map(item => <li key={item.id}>{item.name}<li>)
```