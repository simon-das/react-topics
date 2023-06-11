# Introduction
`useReducer` is a React hook that allows you to manage state in your components using a reducer function. It is an alternative to the `useState` hook when you have more complex state logic.

`useReducer(reducer, initialArg, init?)`

### Example
```jsx
import React, { useReducer } from 'react';

// Reducer function
const reducer = (state, action) => {
  switch (action.type) {
    case 'INCREMENT':
      return { count: state.count + 1 };
    case 'DECREMENT':
      return { count: state.count - 1 };
    default:
      return state;
  }
};

// Component using useReducer
const Counter = () => {
  const [state, dispatch] = useReducer(reducer, { count: 0 });

  const increment = () => {
    dispatch({ type: 'INCREMENT' });
  };

  const decrement = () => {
    dispatch({ type: 'DECREMENT' });
  };

  return (
    <div>
      <button onClick={decrement}>-</button>
      <span>{state.count}</span>
      <button onClick={increment}>+</button>
    </div>
  );
};
```

<br>

1. **Reducer**: The reducer is a function that takes the current state and an action and returns the next state. It defines how state transitions should occur in response to different actions. The reducer function is responsible for updating the state based on the action received.

2. **initArgs (optional)**: `initArgs` is an optional third argument that can be passed to `useReducer`. It allows you to initialize the state based on some complex logic or computations. If provided, it will be passed as the second argument to the `init` function (if present) or as the initial state directly.

3. **init (optional)**: `init` is an optional initialization function that can be used to determine the initial state value. It takes the `initArgs` (if provided) and returns the initial state value. The `init` function is called only once during the initial rendering.

4. **State**: The `state` is the current value of the state managed by the `useReducer` hook. It represents the current state of your component and is updated by the reducer function when the state transitions occur.

5. **Dispatch**: The `dispatch` function is provided by `useReducer` and is used to trigger state transitions by dispatching actions. When you call `dispatch` with an action object, React will pass the current state and the action to the reducer function, which will calculate and return the next state. React will then update the component with the new state, triggering a re-render.

<br>

## Reference
https://react.dev/reference/react/useReducer
