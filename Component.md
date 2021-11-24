# Two ways to create React Components

### 1. Using function to create React components
Render function component: Use function name as component tag name.
> Can use both `<Hello />`or `<Hello></Hello>`

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