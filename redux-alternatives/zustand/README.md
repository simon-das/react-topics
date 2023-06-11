# Zustand
Zustand is a small, lightweight state management library for React applications. It provides a simple API for managing state in a concise and efficient manner. Zustand is inspired by the Redux state management pattern but aims to offer a more streamlined and intuitive approach.

<br>

```jsx
import create from 'zustand';

// Create a Zustand store
const useCounterStore = create((set) => ({
  count: 0,
  increment: () => set((state) => ({ count: state.count + 1 })),
  decrement: () => set((state) => ({ count: state.count - 1 })),
}));

// Component using the Zustand store
const Counter = () => {
  const { count, increment, decrement } = useCounterStore();

  return (
    <div>
      <h2>Count: {count}</h2>
      <button onClick={increment}>Increment</button>
      <button onClick={decrement}>Decrement</button>
    </div>
  );
};

export default Counter;
```
