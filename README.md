# ReactJS  Best Practices :star2:

> NOTE: This document is a live document and updated frequently (Pull requests are more than welcomed :smiley: ) .
 
![ReactJS Logo](https://cdn-images-1.medium.com/max/2000/1*3SrhT42nL9Sprx6mh6sGnA.png)

The content of this document defines a set of best practices to follow when developing an application using ReactJS. The objective of these practices is to maintain a consistent code style throughout the whole application and to improve the maintainability of the code. 

In no particular order...

- Use PascalCase for Components and its respective file name
```javascript
  class MyReactComponent extends React.Component {

  }
```

- Always define the initial state in the constructor of a component. If the initial state is dependent on the `props` make sure to specify default values when `props` are undefined.
```javascript
  constructor(props) {
    super(props);
    this.state = {
      count: props.count ? props.count : 0,
      average: 0,
    }
  }
```

- Use [fat arrow function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions) instead of binding method to `this` in the constructor.
```javascript
  constructor(props) {
    super(props);
  }

  calculateSum = () => {
    // logic goes here
  }
```

- Always prefer [fat arrow functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions)
```javascript
  calculateSum = () => {
    // logic goes here
  }
```

- Use `componentDidMount()` method when adding listeners (e.g: Flux Stores) instead of doing that within `componentWillMount()` or `constructor()` methods.

- Make sure to remove/unsubscribe all the listeners/subscriptions added in `componentDidMount()` within `componentWillUnmount()` method.

- When updating the state of a component if the update relies on the `state` of the component, use the updater function.

```javascript
  calculateSum(addedValue) {
    this.setState((prevState, props) => {
      return {
        sum: prevState.sum + addedValue
      };
    });
  }
```

- If the initial state is dependent on `props` make sure to add the same logic in `componentWillReceiveProps(nextProps)` as well, unless it is not the expected behavior of the component.
```javascript
  componentWillReceiveProps(nextProps) {
    this.setState({
      count: props.count ? props.count : 0,
    });
  }
```

- Keep the render method pure and simple as possible. Try to move all the dynamic style calculation, className changes, etc. into state properties or into functions.

- Keep setting the `style` property on the `div`s in `render()` method to minimum. Always prefer CSS classes.

- It is a MUST to add a JSDoc at the component level describing the component's purpose, how to use the component and if the parent component should pass `props` what are those and their functionality.

- DO NOT use `props` property values directly in the `render()` method. Instead assign those values into properties in the `state` and use `state` properties within the `render()` method.

- Never invoke `this.SetState( /* your code */)` directly within the `render()` method. Instead extract it into a separate function.

- Use the [Spread Operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_operator) to create a copy an Array or an Object
```javascript
  let arr = [1, 2, 3];
  let arr2 = [...arr, 4] 
  // arr2 becomes [1, 2, 3, 4]
  // arr remains unaffected
```







 
