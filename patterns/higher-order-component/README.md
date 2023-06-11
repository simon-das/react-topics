# HOC
A Higher-Order Component (HOC) is a design pattern in React that allows you to reuse component logic by wrapping a component with another component. 
HOCs are functions that take a component as input and return a new component with additional functionality.

<br>

```jsx
import React from 'react';

// Define a Higher-Order Component
const withLogger = (WrappedComponent) => {
  return class WithLogger extends React.Component {
    componentDidMount() {
      console.log('Component has mounted:', WrappedComponent.name);
    }

    render() {
      return <WrappedComponent {...this.props} />;
    }
  };
};

// Create a regular component
const MyComponent = ({ name }) => {
  return <div>Hello, {name}!</div>;
};

// Wrap the component with the HOC
const MyComponentWithLogger = withLogger(MyComponent);

// Usage
const App = () => {
  return <MyComponentWithLogger name="John" />;
};
```

<br>

## Reference
https://legacy.reactjs.org/docs/higher-order-components.html
