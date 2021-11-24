# Two ways to create React Components

### 1. Create React components using functions
Render function component: Use function name as component tag name.
>Start function name with an uppercase letter to render a React component
>Can use both `<Hello />`or `<Hello></Hello>`
>Function must have return statement. If nothing is intended to be rendered, return "null".

Example:
```
function Hello(){
  return(
  <div>This is my first function</div>
  )
}
```
```
ReactDOM.render(
  <Hello />, document.getElementById('root')
);
```

### Create React components using Arrow Functions
Example:
```
const Hello = () => (<div>This is my first function component</div>)
```
>Note that when writing arrow functions, either
```
const Hello = () => {
    return(
        <div></div>
    )
}
```
or
```
const Hello = () =>(<div></div>)
```

