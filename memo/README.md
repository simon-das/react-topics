# Memo
React.memo is a higher-order component in React that can be used to optimize the performance of functional components by preventing unnecessary re-renders. It works by memorizing the result of a component's rendering 
and reusing it when the component's inputs (props) have not changed.

It skips re-rendering a component when its props are unchanged.

<br>

```jsx
import React from 'react';

const MyComponent = React.memo(({ name }) => {
  console.log('Rendering MyComponent');

  return (
    <div>
      Hello, {name}!
    </div>
  );
});

// Parent component
const App = () => {
  const [count, setCount] = React.useState(0);

  const incrementCount = () => {
    setCount((prevCount) => prevCount + 1);
  };

  return (
    <div>
      <button onClick={incrementCount}>Increment</button>
      <MyComponent name="John" />
      <p>Count: {count}</p>
    </div>
  );
};

export default App;
```

<br>

## Reference
https://react.dev/reference/react/memo
