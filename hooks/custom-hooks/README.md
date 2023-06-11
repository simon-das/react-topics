# Custom Hook
A custom hook in React is a JavaScript function that allows you to reuse logic and stateful behavior across multiple components. It enables you to encapsulate complex logic into a reusable unit, promoting code reusability and readability.

Custom Hooks allow you to share the logic and behavior of state management, but not the actual state itself.

<br>

```jsx
import { useState } from 'react';

function useCounter(initialValue) {
  const [count, setCount] = useState(initialValue);

  const increment = () => {
    setCount(count + 1);
  };

  const decrement = () => {
    setCount(count - 1);
  };

  return { count, increment, decrement };
}

// Usage example
function CounterComponent() {
  const { count, increment, decrement } = useCounter(0);

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={increment}>Increment</button>
      <button onClick={decrement}>Decrement</button>
    </div>
  );
}
```

<br>

## Reference
https://react.dev/learn/reusing-logic-with-custom-hooks
