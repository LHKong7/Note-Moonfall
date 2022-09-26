# Main Concepts



**Separation of Concerns**: Reduce <font color="teal">coupling</font>, increase <font color="teal">cohesion</font>

**Coupling**: The degree to which each program module relies on each of the other modules

**Cohesion**: The degree to which elements of a module belong together



```
ReactDOM.createRoot() :   To render a React element, first pass the DOM element to the function, then pass the React lement to root.render()

React.createElement() :

render

```







React embraces the fact that rendering logic is ***inherently coupled*** with other UI logic: how events are handled, how the state changes over time and how the data is prepared for display (React also redefiend event)

<font color="teal">React Components</font> : A **highly-cohesive** building block for UIs **loosely coupled** with other components.

​	**Cross-site-scripting (XSS)** : XSS attacks enable attackers to inject client-side scripts into web pages viewed by other users. A cross-site scripting vulnerability may be used by attackers to bypass access controls such as the same-origin policy. There are two types of XSS, *non-persistent & persistent*; traditional (caused by server-side code flats) and DOM-based (clien-side code)

​	A classic example of a potential vector is a site search engine: if one searches for a string, the search string will typically be redisplayed verbatim on the result page to indicate what was searched for. If this response does not properly [escape](https://en.wikipedia.org/wiki/Escape_character) or reject HTML control characters, a cross-site scripting flaw will ensue -> this is how react avoid XSS



**React Elements**: are the smallest building blocks of React apps, which describe what users see on the screen. Unlike DOM elements, React elements are plain objects and cheap to create. The React DOM will take care of updating trhe DOM to match the React Elements. An element is immutable whose children and attributes cannot be changed.

***All React components must act like pure functions with respect to their props***



##### State

`setState()`: 

- Do not modify state directly
- state updates may be async
- state updates are merged



##### Lifecycle

```
componentDidMount() : runs after the component output has been rendered to the DOM
```



##### Handling events

React events do not work exactly the same as native events. *When using React, you generally don’t need to call `addEventListener` to add listeners to a DOM element after it is created. Instead, just provide a listener when the element is initially rendered.*



##### Conditional Rendering

- use `if...else` 
- inline if with Logical `&&` operator
- inline if-else with `condition ? True : false`



##### Lists and keys

A `key` is a special string attribute you need to include when creating lists of elements. Keys help React identify which items have changed, are added, or are removed. Keys should be given to the elements inside the array to give the elements a stable identity.

```jsx
function ListItem(props) {
  // Correct! There is no need to specify the key here:
  return <li>{props.value}</li>;
}

function NumberList(props) {
  const numbers = props.numbers;
  const listItems = numbers.map((number) =>
    // Correct! Key should be specified inside the array.
    <ListItem key={number.toString()} value={number} />
  );
  return (
    <ul>
      {listItems}
    </ul>
 );
```

**Keys must only be unique among siblings**

**embedding map() in JSX**



##### Forms



##### Lifting State Up



##### Composition vs Inheritance

